# Blog voice: long-form writing on preset.io/blog

Everything else in this skill was built from short GitHub comments (median
24 words). Blog posts are a different genre with different rhythm, and some
GitHub-comment rules do NOT transfer. This file is built from 39 preset.io
blog posts authored by Evan, published 2020-07-02 through 2025-06-23 (all
before the one-year cutoff used elsewhere in this skill).

## The most important calibration: em-dashes are NOT rare in blog writing

`anti-patterns.md` Tell #6 documents a 0.4% em-dash rate in Evan's GitHub
comments, and treats any `—` as an AI tell there. **That rate does not hold
for blog-length prose.** 20 of the 39 posts contain at least one em-dash,
including some of the most personally-voiced ones (the "GPT x Superset"
post alone has 4). Do not apply the GitHub "no em-dash" rule to blog
writing - it would actively de-authenticate a long-form draft. The
full-stop-over-comma preference (split into separate thoughts) still holds
as good general writing advice, but em-dash presence itself is not a tell
in this genre the way it is in a two-sentence PR comment.

## Genre matters more here than in GitHub writing

Posts split cleanly into three genres with very different voice signal.
Identify which genre a piece of writing is before drafting, and calibrate
accordingly - there is no single "blog voice", there's a personal-technical
voice, an institutional-newsletter voice, and a marketing voice, and only
the first one is really "Evan."

**Personal/technical posts** (tutorials, community-topic deep dives, retros
like "git bisect", "discovering third-party plugins", "GPT x Superset"):
first-person, opinionated, funny, digressive. This is the voice to imitate
when the ask is "write like Evan."

**Monthly community newsletters**: pure event/announcement listing,
templated month-to-month, essentially zero personal voice. Don't use these
as a voice source beyond confirming the format exists; they're closer to a
mail-merge than personal writing.

**Product/marketing posts** (recent, short, feature-announcement or
case-study shaped - "Preset Workspaces and Why You Need Them," "Stop
Forking Around," the Kapa.ai case study): read as standard SaaS marketing
copy - bulleted feature lists, sales CTAs ("Talk to an Expert," "Set up a
call to learn more!"), zero "I" statements, zero jokes, generic "the
result?" conclusions. These are very likely NOT Evan's own unedited voice
(marketing-team drafted or AI-assisted with light editing) and should be
excluded from any exemplar corpus, not imitated as "the blog voice."

A rough proxy that tracks this split well: 24 of the 39 posts have zero
instances of the word "I". The personal-voice outliers cluster tightly -
"GPT x Superset" (107 uses of "I"), "discovering third-party plugins" (27),
"theming progress update" (13), "git in the loop" (10). Everything else is
institutional "we"/"Preset" voice, and the closer a piece is to zero "I",
the less it should be treated as a personal-voice exemplar.

## Vocabulary and tics specific to long-form writing

- **Slash-emphasis instead of italics**: `/word/` used for emphasis - `/work/`,
  `/fantastic/`, `/removed/`, `/approved/`, `/hide/`, `/toolkit/`,
  `/maintaining/`. Shows up across at least 7 posts spanning 2020-2025, so
  it's a genuine personal typing habit (plausibly carried over from
  plain-text email/Slack), not a one-off. Use this instead of markdown
  `_italics_` or `**bold**` for a stray emphasized word in long-form Evan
  writing.
- **Self-invented structuring gimmicks over generic listicles.** "GPT x
  Apache Superset" scores each experiment on a "Hope Scale"/"Hope Score"
  (both labels appear, used inconsistently) from 1-10 with an emoji: "Hope
  Scale: 9 🥳", "Hope Scale: 3 😭 (liar liar, pants on fire!)", "Hope Score: 7
  😃 (it seems to work… but does it help much?)". A generic AI draft
  comparing tools defaults to a Pros/Cons table; Evan invents a whimsical
  scoring bit instead. When the content calls for a comparison/roundup,
  consider whether an invented, slightly silly structuring device fits
  better than a table.
- **Dry, deadpan one-liners as their own paragraph**: "Say what?!", "Le
  sigh.", "OK, OK... the link above is a user account, not a plugin. Pardon
  the inconsistency."
- **Self-deprecating parentheticals**: "make sure everything fits onscreen
  to be readable like in this (admittedly not useful) example I've mocked
  up."
- **Idiom-heavy, casual phrasing**: "spelunking in code", "went sideways",
  "Let 'er rip", "Wipe the slate", "AHA! moment" (git-bisect); "hit the
  streets", "the driving theme (pardon the pun)" (5.0.0 release notes);
  "Gorgeous, no?", "I'll be the first to pop the champagne"
  (theming-progress-update).
- **Named, specific shout-outs** rather than generic thanks: hello-world
  credits Ville Brofeldt, Krist Wongsuphasawat, and Jesse Yang by name with
  what each contributed; 5.0.0 release notes thanks "our esteemed release
  manager Michael S. Molina." Specific credit, not "thanks to all our
  contributors."
- **Real typos survive**, evidence these posts are genuinely unedited or
  lightly edited, not run through a polish pass: "quuickly", "pesisted",
  "contrls", "exacty", "specimiens", "Suprerset", a duplicated "Firefox
  Firefox". Do not fabricate typos to imitate this (same rule as the
  GitHub-comment calibration) - it's evidence of the writing process, not a
  style to deliberately reproduce.

## Structural habits

- **Opens on the "why"**, often addressing a recurring community question
  directly ("How do I make a new plugin?", "When will there be a dark
  mode?") before getting technical.
- **Narrates through lists rather than letting them stand alone.**
  Numbered/bulleted steps appear in tutorials, but wrapped in a lot of
  connecting prose, not a bare list.
- **Closes personally on short/casual posts**, often with a direct question:
  git-bisect ends "Let me know on Slack if you enjoy this sort of tips n'
  tricks post… I'm happy to do more!"
- **Closes generically on longer "best practices" posts** - the one clear
  failure mode found. "Git in the Loop" (2,085 words) ends with a textbook
  wrap-up ("Efficiently managing GitHub notifications is essential to
  foster collaboration... Let's optimize our workflows and create vibrant
  open-source ecosystems together.") that reads exactly like the
  AI-flavored closings this skill warns against elsewhere. Post length
  seems to correlate with how generic the ending gets - watch for this on
  long technical posts specifically, and prefer a direct, personal close
  (a question, an offer, a plain "let me know") over a summary-of-the-summary.
- **Retroactively annotates outdated posts** rather than rewriting them:
  hello-world ends with "Note: this blog post is now out of date. Please
  check out our updated post here"; theming-progress-update got a note
  prepended later ("Great news — the theming vision described in this post
  is now a reality!"). A distinct, recurring editorial habit.
- **Explicit AI-authorship disclaimers, unprompted.** "GPT x Apache
  Superset" (2023) opens with "A few disclaimers before we embark: This
  post was written by human hands." Worth knowing this instinct exists,
  though it obviously can't apply to Claude-assisted drafts going forward
  without it becoming a lie.

## The outliers vs. default AI blog output

These are the concrete tells: places the real writing does something a
generic AI blog draft would not.

- **Genuine confusion/hedging left visible mid-argument, not smoothed
  over**: "That said, the PR is held up due to an issue about the
  higher-level problem that the PR is trying to solve for… something that
  wouldn't be caught unless you had a historical context with the
  codebase." A generic AI draft resolves this into clean, confident prose;
  the real version keeps the run-on, thinking-out-loud quality.
- **Opinions stated flatly, not both-sided into mush**: "GPT4 for the
  win!", "Bard wins here in my book." Default AI blog-writing hedges
  toward "both tools have their merits"; Evan just picks one.
- **Personality-forward structure over safe/generic structure** (see the
  Hope Scale above) - invented, slightly goofy framing over a Pros/Cons
  table or numbered comparison.

## What NOT to imitate

The three marketing-genre posts flagged above ("Preset Workspaces and Why
You Need Them," "Stop Forking Around," the Kapa.ai case study) and the
newsletter format are real content Evan's name is on, but they don't carry
his personal voice signal and should not be treated as "how Evan writes" -
if asked to draft something in that genre, matching the genre convention is
fine, but don't pull vocabulary/tics from the personal-voice section above
into that kind of piece; it would look pasted-in.
