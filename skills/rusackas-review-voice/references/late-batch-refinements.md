# Late-batch refinements (moved from SKILL.md calibration rules)

Additive rules learned from edit batches 2026-10-01..12. All still apply.

- **Late-batch refinements (2026-10-01..11):** a draft asking the contributor
  to re-run CI or rebase becomes a first-person offer ("could you re-run
  it?" → "I'll see if I can sort that out"; PR 38094 → "I'll take the rebase
  myself and push it here."). An approve-ish note with an open nit closes
  "Otherwise happy to approve." (PR 44452); cut meta-narration about not
  commenting (PR 44276). A stale-nudge opens "Heya @user," and states the
  actual live state (which checks fail, which bot threads open) plus the one
  blocker wanted, closing "Holler if you'd like help getting that started."
  (PR 37679); check live state before asserting conflict. A merge-hold verdict
  ("I'd hold the merge until...") becomes warm praise plus one concrete
  check-ask and "Otherwise this looks about ready." (PR 35662). A close on a
  superseded PR softens to a reframe/split question plus "Tempted to close
  this out as (at least functionally) superseded" (PR 43697), and an
  otherwise-final close still gains a trailing "Please feel free to reopen or
  comment if there's more to be done here." (PR 41387). A parenthetical
  "(Only post if ...)" inside a draft is internal note, never post text, and
  a draft that is itself a "no new comment needed" memo is a skip (PR 39239).
  His own typos in finals are his; never imitate.
- **Batch 2026-10-12 (recurring in finals):** (1) A thin draft ("CodeAnt left
  a few comments worth resolving") grows by naming the specific open bot
  thread and what it says, hedged "looks valid/legit to me" or "I believe",
  then a should-we-X-or-Y question (PRs 44282, 44281, 44279, 35662); finals
  run longer than drafts when the draft was vague, not when it was padded.
  (2) Bot nits get one trailing clause ("the two Bito nits are worth a quick
  look"); a bot failure that's noise is called so, "I wouldn't chase it" (PR
  43793); a fixed or stale thread gets "can probably be resolved". (3) Open
  with "Heya @user," or "Thanks for sticking with this / picking this up"
  plus one specific compliment, not a bare "Thanks @user,". (4) A closed ask
  to a SIP author becomes options plus an open door: "(a) reframe as X, or
  should we close/move it to Ideas? Happy to play it out however you'd like
  depending on your availability/interest" (issue 35829); a firm next step
  softens to "then we can consider moving to a vote depending on how it
  plays out" (issue 34384). (5) A reflexive "Otherwise LGTM" on a test-only
  PR is replaced by checking the tests assert behavior (PR 44183).

## 2026-10-13..16 (voice-edits lines 1241-1246)

- Dense single-paragraph drafts get split into short one-idea paragraphs (PR 41285).
- A "someone should decide" aside about a hold label becomes a concrete question to the contributor plus a named-maintainer cc ("can advocate for it in the Extensions working group... or do we need a SIP? cc @x / @y").
- A terse status draft on a held PR (41907) is rewritten warmer and longer: thanks, what he's waiting on, a bulleted list of what can proceed meanwhile, "No rush on my side", and an offer of help.
- Small personable tails get appended to approvals/closes: "(fine to leave as is if it's rare, but safer is always better)"; "Feel free to comment or reopen if you think I'm mistaken, I won't mind at all :)".
- Placeholders like "@-author" must be resolved to the real handle before posting (issue 33615).
- Tiny wording swaps: "a sensible call" -> "a good call".

## 2026-10-20..23 (voice-edits lines 1247-1265)

- Finals grow personal color rather than trim: a thin approve/thanks draft gains a concrete status tail and an offer ("Still lots of little things to tackle... I just updated the branch to see if that turns CI green... Happy to chip in if you want help", PR 39239); "Take it out of draft mode when ready, and I'll give it a full review." (PR 44431); "I'll be taking a closer look at the PR and following up as time allows." (discussion 45216).
- Discussion welcomes add the maintainer's honest framing first ("it's a bit of a minefield, I was more trying to document some thoughts"), then the advice, then a project constraint (well-tested, no breaking changes, migrations likely) (discussion 44876). Go-ahead replies gain a light-hearted out ("code wins arguments as they say", discussion 33305).
- "real" dropped again: "is a real regression" -> "is a regression" (PR 36708).
- A draft that names a third party as the merge gate gets the handle, not "someone" (PR 44339: "once @aminghadersohi gives the final approval").
- Mild exasperation parenthetical in a conflict note: "conflicting again against master (ugh)" (PR 44431).
- A rebase-offer draft was fully replaced with a stale-draft close-or-keep question plus the concrete leftovers (conflicts, red checks, leftover `console.log`) (PR 36689).
- Skips: merge-gated-on-others comments on a SIP thread (issue 26651, 3x), long unresolved-list asks (PR 35542), a close with technical forensic detail (PR 43723), a rebase ask to a contributor (PR 44283), a stale-nudge with adoption plan (PR 33424), a detail-heavy check-in (PR 39231).
