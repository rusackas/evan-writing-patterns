# Apply-able `suggestion` comments (one-click "Apply suggestion")

When a review point is a concrete change to specific line(s), post it as a GitHub
**suggestion** so the author can click **Apply suggestion** (or batch "Add to
batch" → "Commit suggestions") instead of hand-editing. Do this wherever the fix
is a line replacement — nits, one-liner bug fixes, renames, guard/clamp tweaks,
import fixes. It's faster for the author and removes ambiguity about the exact edit.

## When it works vs. when it doesn't

- **Works (use a suggestion):** the change *replaces* existing line(s) that are
  part of the PR's diff — i.e. an added/changed line on the RIGHT side. Single
  line or a contiguous run of lines.
- **Doesn't (stay prose):**
  - **Net-new code** — a whole new test, function, or file. There's no existing
    line to replace, so there's no Apply button. Ask for it in words.
  - **Non-contiguous edits** — one logical change scattered across several
    unrelated spots. Describe it (or post several separate suggestions, one per hunk).
  - **A context (unchanged) line** — if the anchor line isn't an `+`/changed line
    in the diff, GitHub won't offer Apply. Anchor to a line the PR actually touched.

## Mechanics (gh)

An apply-able suggestion is an **inline review comment** anchored to the exact
line(s), whose body contains a fenced `suggestion` block that is the FULL
replacement for those lines, at the exact indentation of the file.

```bash
# single-line suggestion on <path>:<line> at the PR head sha
gh api repos/<owner>/<repo>/pulls/<N>/comments \
  -f body="$(cat body.md)" \
  -f commit_id="<head_sha>" \
  -f path="<path>" -F line=<line> -f side=RIGHT
```

- `commit_id` = the PR's current head sha (`gh api repos/<owner>/<repo>/pulls/<N> --jq .head.sha`).
- `line` = the file line number in the NEW version; `side=RIGHT`.
- **Multi-line** replacement: add `-F start_line=<first> -f start_side=RIGHT` and set
  `line` to the LAST line of the range; the block replaces the whole span.
- Body shape (the block content is the literal replacement, matching indentation):

  ```
  One short in-voice line on what/why.

  ```suggestion
          const val =
            action.payload.value === '' ? NaN : Number(action.payload.value);
  ```
  ```

## THE GOTCHA that silently breaks them (learned the hard way)

**Never build the comment body with bash `$'...'` ANSI-C quoting or hand-rolled
quote-switching (`'"'"'`).** An embedded quote (e.g. an empty string `''` or an
apostrophe in "Here's") terminates the `$'...'` context, and everything after it
reverts to a LITERAL `\n` instead of a real newline. Symptoms seen in the wild:
- the whole ` ```suggestion ` block ends up inline on one line → **no Apply button
  at all**; or
- the block opens correctly but the suggested *code* contains literal `\n` →
  the button shows but **applying inserts broken code**.

**Do this instead** — write the body to a file (real newlines, no shell escaping)
and post via a jq-built JSON payload so escaping is handled by jq, not the shell:

```bash
# body.md written by a real editor/heredoc with actual newlines + the ```suggestion block
jq -n --rawfile b body.md --arg sha "<head_sha>" --arg path "<path>" \
  '{body:$b, commit_id:$sha, path:$path, line:<line>, side:"RIGHT"}' \
  | gh api repos/<owner>/<repo>/pulls/<N>/comments --input -
```

**Always verify after posting:** re-fetch the comment and confirm there are ZERO
literal `\n` in the body:
`gh api repos/<owner>/<repo>/pulls/comments/<id> --jq .body | grep -c '\\n'` → must be `0`.
If it's broken, `DELETE repos/<owner>/<repo>/pulls/comments/<id>` and repost from a file.

## Replying-to-a-thread vs. fresh inline comment

To make a **bot/human thread's** fix apply-able, a fresh inline comment anchored to
the exact line is the reliable path. A `suggestion` inside a *reply* only applies if
the thread is anchored to the exact same line the block replaces — often it isn't
(the bot flagged line N but the edit is on line N±k), so prefer a new line-anchored
comment for the apply button, and (if useful) still reply on the thread in prose.
