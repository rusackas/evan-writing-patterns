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
