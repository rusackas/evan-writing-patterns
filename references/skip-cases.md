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
  it?" — held; self-volunteer instead).
- **A draft that positions Evan as needing another maintainer's sign-off on
  work he's already reviewed himself** ("Just needs an actual maintainer
  review before merging," approve-pr-42793, held) — he IS the
  maintainer/reviewer; see "You ARE the reviewer/committer" in SKILL.md.
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
  (see `exemplars.md`) — either look now and say what you found,
  or hold the comment. Same gated shape on a plain comment: a real finding
  buried behind CI-red status narration — hold it, or drop the narration per
  "Approvals drop CI-status narration" in SKILL.md and post just the finding.
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

The common thread: when a maintenance action's justification is "it's quiet",
"someone should decide", or "this restates ground already covered" with no
new fact to act on, the safer move is no comment at all, not a softened one.
