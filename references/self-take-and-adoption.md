# Self-take and adoption: full mechanics

Referenced from SKILL.md's Situational playbook ("Take mechanical chores...")
and indexed in "Signature moves". Full detail on the take-it-yourself /
adopt-a-stalled-PR family, condensed to a single paragraph in SKILL.md itself.

**Take the CI/rebase/prettier chore yourself when it's mechanical**, rather
than instructing the contributor to rebase or clear a lint failure — a plain
declarative ("I'll rebase it now"), not a permission-seeking question. Cut
the precise diagnosis entirely, and never claim you've already done it
unless it's literally true (anti-pattern Tell #7). At the extreme — the
single most common edit in the corpus — Evan replaces the *entire* comment
with just the offer ("to move things forward" / "since I'm here" / "since
it's been quiet"); the opening `@handle` goes with it when the self-take
replaces the whole comment, but stays if still *talking to* the contributor.
"Adopt" is Evan's verb for carrying a stalled PR forward on a fresh branch. A
self-take can also hand the contributor the actual choice ("...on a fresh PR
if you'd prefer, or push some commits here", PR 36094), or sit as a fallback
if they don't respond to the ask at all ("If not, I'll see about pushing some
commits", PR 43199). When nothing's actually been pushed yet, the adoption
pitch gets replaced by a plain status update rather than posted as a
still-unstarted plan (PR 38691). A rebase-only ask handed back to a
contributor who just responded gets held outright rather than posted (PR
42540, `references/skip-cases.md`). When the PR isn't in a mergeable state at
all (conflicts plus failing required checks, not just a soft review gate),
that blocking status takes priority over an in-progress code-quality
question, even a well-formed one — the whole comment swaps for the
conflict/CI status plus a self-take offer, and the code point waits for a
pass once the PR is actually reviewable (PR 42849). See
`references/exemplars.md` ("Self-take that drops the @handle", and
"Contributor gone silent → adoption offer" counter-case).

A middle case, more common than a full replace: **append** a short
present-tense action tag to the end of an otherwise-unchanged substantive
comment, rather than replacing it — "Attempting that now...", "I'll see if I
can tackle the rebase now...", "(attempting now)" mid-sentence. The praise
and the blocker both stay; only the tag is added (PRs 43189, 43192, 39528
under "Appended action tag" in `references/exemplars.md`).

**Hard limit: you can't push to a contributor's fork unless they've enabled
maintainer edits.** When a draft volunteers to rebase but hits this wall, the
honest final explains the blocker ("GitHub won't let me push") and hands the
rebase back, keeping the warmth. Recurring opener: **"as it turns out"** — a
sheepish discovery hedge, not a refusal. When access is merely *untested*
rather than confirmed-blocked, the honest move is a plain uncertainty hedge
followed by an attempt anyway ("Not sure if I can push to your fork, but I'll
give it a shot") rather than assuming either way. See `references/exemplars.md`
("Can't-push-to-fork", and "Uncertain push access gets stated plainly, then
attempted anyway").
