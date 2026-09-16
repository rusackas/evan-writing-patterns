# When a draft should not be posted at all

Referenced from SKILL.md ("When a draft should not be posted at all"). Some
maintenance-loop drafts get rejected outright (`event:"skip"`), not edited.
These aren't voice failures, they're judgment calls: the draft acted on a
conclusion Evan hadn't actually reached yet. Full worked quotes for every
case below live in `exemplars.md` ("Skipped drafts"). Recurring cases worth
staying quiet on rather than posting a softened version:

- **Nothing new to add — the point is already established.** Several shapes:
  restating a CI failure already red and visible; re-pasting a question
  already asked; re-explaining an approval already landed; a duplicate
  redraft posted earlier in the same pass; a label/routing note where the
  label is already correct; the identical routing question repeated verbatim
  across several near-duplicate PRs (ask once, not once per PR); a comment
  and a label on the same issue both asserting the identical governance-path
  decision (issue 43420: a "duplicate, see #43421" comment and a routing
  label fired together on the same issue, both held); a full technical
  elaboration of another reviewer's already-open,
  already-correct point instead of a brief endorsement; and a bare
  crowdsourced pickup ask with no self-take on a fix that's already known
  ("Anyone want to pick up the rebase?" — held; contrast `issue-voice.md`'s
  "Diagnose, then volunteer," which pairs a self-take with genuinely new
  diagnosis). Same holds when the diagnosis IS new but the closer asks the
  counterparty to do the fix instead of volunteering ("Want to send a PR for
  it?" — held; self-volunteer instead). Confirmed again on a same-day batch
  of four: comment-pr-43022, comment-pr-38119, comment-pr-35541, and a second
  duplicate pass on comment-pr-42248 — in each, Evan (or another maintainer's
  self-imposed hold) had already said the substantive thing live, and nothing
  on the PR had changed since. Confirmed as a repeat offender on the *same*
  PRs, not just the same shape: comment-pr-37773 (rebase + CI-red + a
  detailed re-listing of @sadpandajoe's already-flagged `url_for()`/
  `UPDATING.md` gaps) and comment-pr-37712 (a full technical elaboration of
  @sadpandajoe's already-open `mapXAxisSortToSeriesType` finding) each got
  redrafted and held a second time on 2026-09-16, having already been held
  once before on 2026-09-07 — the maintenance loop keeps proposing the same
  comment on a PR that hasn't moved, and it keeps being the wrong call each
  time. comment-pr-42112 is the same "full elaboration of another reviewer's
  finding" shape on a third PR the same day. comment-pr-38094 stated its own
  reasoning inline ("This is a rolling-window resurface, not new activity,
  nothing to post") — treat a rolling-window resurface with zero new commits
  or replies since the last check as its own instant tell, independent of
  how well-written the write-up is.
- **A status note that a PR is still stacked/blocked behind an unmerged
  parent PR, with nothing new since the last check.** Confirmed as its own
  recurring shape on a same-day batch of three near-identical drafts, all
  held: comment-pr-43132, comment-pr-43133, and comment-pr-43134, each
  restating that the PR can't move until #42805 (itself stuck on a SIP-224
  `dev@` vote) lands, with the PR's own open review threads correctly noted
  as inherited from the parent rather than new findings. Contrast the
  non-skipped version of this same situation in SKILL.md's "Pushback /
  blocker" note on PR 43136 — that one earns a comment because it pairs the
  same blocked status with genuine new praise and a warm close, not because
  the blocked-status fact itself is new.
- **A healthy, fast-moving multi-reviewer thread with no ask actually
  directed at Evan yet**, even when his own analysis of it is accurate and
  thorough. Recurs on the same PR (comment-pr-43572) as the "other
  maintainers already driving review" case above: a later pass found the
  author had since pushed fixes for both open findings and the remaining
  scope question had been spun out into its own issue with apparent
  agreement from the other reviewers — genuinely good progress, but still
  nothing for Evan to add or decide, so the maintenance loop stays quiet
  rather than posting a status recap.
- **A draft that positions Evan as needing another maintainer's sign-off on
  work he's already reviewed himself** ("Just needs an actual maintainer
  review before merging," approve-pr-42793, held) — he IS the
  maintainer/reviewer; see "You ARE the reviewer/committer" in SKILL.md.
- **The reverse case: other maintainers are already actively driving review
  on a PR that isn't his to push to.** A correct, well-diagnosed finding
  (comment-pr-43572: a real annotation-layer permission gap, plus a genuinely
  red CI failure) still gets held when the maintainers already doing rounds
  of review on that PR (aminghadersohi, gabotorresruiz) have working repro
  steps and are already on it — piling on a third voice restates ground
  already being actively worked, it isn't a sign-off gap like the case above.
- **A conditional label that depends on unconfirmed information** ("keep
  label X, add label Y once confirmed/once a version is given") — nothing to
  post until the reporter supplies it.
- **A "is this still alive?" nudge on a quiet SIP/issue** with no new
  evidence beyond "it's been quiet." Same family: a bare forecast that a
  linked PR/SIP will resolve the issue with *nothing else added* and no
  concrete linked work named — naming an actual PR/SIP number ("this closes
  when #39509 lands") is NOT the skip case, see `issue-voice.md`.
  **The full close action, not just the nudge, gets held the same way** when
  its only justification is elapsed silence, even with a well-formed reopen
  door attached ("No takers since I asked back in June... happy to reopen
  once someone's ready to commit", close-issue-33448; "Closing this out
  since it's been quiet since I checked in back in June", close-pr-36961 —
  both skipped outright, not softened).
- **Re-litigating actionability instead of just deciding it** — asking the
  room whether an issue is "actually actionable yet" reads as stalling.
- **A hollow commitment — action promised with nothing behind it:**
  volunteering to adopt/forward a PR as a bare gesture with no concrete
  reason (the non-skipped adoption exemplars elsewhere in SKILL.md pair the
  offer with "can't push" or "contributor silent on repeated asks"; see
  `exemplars.md` "Bare adopt/forward gesture, no concrete
  reason"); an approve gated on a pending rebase or any other
  requested-but-missing item (if the draft's own last line is "just needs
  X," it's a nudge, not an approval — approve-pr-42477 stacked a rebase AND
  a stale-comment fix onto an approve and got held whole, not trimmed to a
  plain approve); and a positive review that ends by promising a closer look
  before merging instead of doing the closer look now, a repeating pattern
  (three instances now: comment-pr-41923, -42484, -43203; "I'll get this
  reviewed properly and merged" is the same deferral as "closer look", see
  `exemplars.md`) — either look now and say what you found, or hold the
  comment. Same gated shape on a plain comment: a real finding buried behind
  CI-red status narration — hold it, or drop the narration per "Approvals
  drop CI-status narration" in SKILL.md and post just the finding. Same
  family from the other direction: **a rebase-only ask handed back to a
  contributor who just turned around fixes** ("needs a rebase before we can
  move it along. Holler once that's pushed.", PR 42540 inbox draft, held) —
  the only content is a mechanical chore Evan would normally take himself,
  so either do the rebase or stay quiet.
- **An approve that raises a genuine unresolved doubt about whether the fix
  actually works**, in the same breath as approving it — a doubt that could
  mean the fix doesn't fully work isn't a shipped approval yet.
- **A blocking comment built on a technical theory you haven't actually
  worked through.** Diagnosing a real gap is fine; closing with "wondering
  if X gets us further, but I haven't worked that through... let's land on
  an approach before merging" turns your own unverified guess into a gate on
  someone else's PR. Work the theory through to something concrete first, or
  hold it (comment-pr-42489, skipped).
- **Several distinct findings crammed into one comment** — see "One point per
  comment" in SKILL.md; this is the same rule, and the held-not-trimmed outcome.
- **A PR still in draft state**, where CI is red on the author's own
  in-progress suite and a bot review already surfaced the issues inline. Let
  them finish iterating.
- **A close that renders a definitive judgment on a contributor's motives or
  scope**, even when the reasoning is sound and matches another reviewer's
  take — stays undrafted.
- **Preemptively arguing away another reviewer's still-standing block**
  instead of pinging them to re-review — declaring your own earlier design
  idea dead and treating their CHANGES_REQUESTED as a formality to clear
  reads as pressuring them off their review (comment-pr-38741; contrast
  "Approving alongside another reviewer" in SKILL.md, which pings them instead).
- **A bare label-apply or reviewer-assignment action with no comment
  attached** — too perfunctory to fire on its own, even when the routing is
  reasonable.
- **A short, directive redirect telling a community member where to post
  instead**, paired with reclassifying their issue in the same breath — even
  sound routing logic reads more presumptuous than a plain "@handle, see
  also #X" pointer.
- **A speculative "this needs docs" flag mined from a merged/in-review PR's
  diff**, proposing some doc page should cover a new config value or control
  not mentioned there yet. Confirmed a whole-category skip across four
  separate batches now (3/3, then 3/3, then 4/4, then 1/1 — 11/11 total) —
  unsolicited docs-gap mining reads as busywork manufactured by the tool,
  not something Evan noticed and decided to raise. Treat this as a category
  to stop drafting at all, not one to soften. See `exemplars.md` ("A
  speculative 'needs docs' flag").
- **Tentative (two instances, one pass): an inbox mark-read no-op on a
  notification that points at a newly opened PR Evan will want to follow.**
  Both declined mark-reads (inbox items on #43987 and #44153) were correctly
  judged "no reply needed" — a courtesy mention that #43994 covers the fix,
  and a contributor claiming Evan's own issue then opening #44168 — but
  "nothing to reply to" isn't the same as "nothing to track." When the
  notification's whole point is a fresh PR against an issue he's invested
  in, leave it unread rather than auto-clearing it. Watch for recurrence
  before treating this as settled.

The common thread: when a maintenance action's justification is "it's quiet",
"someone should decide", or "this restates ground already covered" with no
new fact to act on, the safer move is no comment at all, not a softened one.
