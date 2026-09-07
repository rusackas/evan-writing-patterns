# Issue voice: GitHub issue comments (as distinct from PR review)

Built from a corpus of 4,785 issue comments Evan posted before 2025-07-10
(distinct from the ~6,000-comment PR-review corpus everything else in this
skill is built from), 99.2% on apache/superset with a long tail of ~17
other repos back to 2016. Same voice, same person, but issue threads pull
for different material than PR review does, and it shows: median comment
length here is **35 words**, notably longer than the 24-word PR-review
median. This file covers what's actually different.

## Why issue comments run longer

Four things fill the extra words, none of which come up in PR review:

- **A near-fixed stale-close template**, reused for years with only the
  version number changing:
  > "I'm not sure if this is still an issue in current versions of Superset
  > (3.x). If it is, we can re-open this, or feel free to open a new issue
  > with updated context and a reproducible case using example data. We're
  > no longer supporting Superset 2.x or prior, and it's been a while since
  > this thread saw any activity, so I'm closing this as stale."

  Use this shape (not verbatim, swap the version/timeframe) whenever
  closing a genuinely stale bug report - it's ~55 words on its own, which
  alone explains a chunk of the length gap. Always pairs an explicit reopen
  path with the close; never a bare "won't fix" or "closing as stale" with
  no door left open.
- **Numbered/bulleted diagnostic triage**, something PR review never needs
  since the PR itself is the reproduction:
  > "1) Is there a reason not to use virtualenv?... 2) Is there anything in
  > particular you're doing, procedurally... 3) Would the docker
  > installation be more useful... 4) What kind of machine / OS / python
  > version setup are you running? 5) What version of Superset are you
  > running?"
- **Walking non-committers through basic steps** (cloning, editing CSS,
  terminal commands) that a PR reviewer would never need spelled out.
- **Explaining *why* something is being redirected** - bug vs. feature
  request, Issue vs. Discussion vs. SIP vs. `dev@` mailing list. PR review
  has no equivalent "wrong venue" redirect; issues do, constantly.

## Issue-specific situations

**Bug triage**: rapid-fire numbered or bulleted diagnostic questions (see
above). Consistently demands repro steps or example data before going
further - "we can't fix it if we can't replicate it." Often opens with a
confusion-first admission before the questions start: "I don't quite
understand the issue...", "I might be a little confused here...", "A few
things to disambiguate....".

**Feature requests**: never a flat no. The consistent pattern is disambiguate
(bug vs. feature) then redirect with the process explained, not just named:
> "This is more of a feature request than a bug, so I'll convert it to a
> Discussion."

Heavier SIP/governance vocabulary shows up here than anywhere in PR review:
"[DISCUSS] thread", "the `dev@` list", "lazy consensus", "Town Hall", "Ideas
thread", and even self-assigning SIP numbers inline ("I'm numbering this as
SIP-97").

**Less-technical / non-committer users**: register visibly softens compared
to PR review - more step-by-step, more explicit patience markers ("Hope
this helps!", "I don't quite understand the issue... can you confirm").
This shift doesn't happen in PR review because a PR author is already
inside the codebase; an issue reporter often isn't.

**Stale/duplicate closing**: the single most distinctive issue-only
behavior is the stale-close template above. Always paired with an explicit
reopen path. "Say the word" shows up here as plain "let me know" rather
than specifically a rebase offer: "just say the word, and I/we can re-open
it!"

**Forecasting that a linked PR/SIP will close the thread**: fine to post, and
not the blanket-skip case an earlier version of this skill claimed. When the
forecast names concrete linked work (not just "someone's working on it"), it
gets posted, usually after only an em-dash cleanup, and sometimes with an
added warm/playful line if reviewers are still needed. Draft "Thanks @atrsa —
#39509 takes the cursor route, which looks like the only shape Elastic's SQL
allows. Reviews welcome over there; this closes when it lands." → final
swaps the em-dash for a period, otherwise unchanged (apache/superset#24563).
Draft "SIP-216 passed the process gate and the DB-side rollup POC in #41184
covers both table and pivot totals — this thread closes when that merges."
→ final drops the em-dash *and* appends "...but I'm still seeking reviewers!
Please jump in, the water's perfect ;)" (apache/superset#25747) — the
forecast stands, but a bare "this closes when it lands" reads too flat/final
on its own when the linked work still needs eyes, so it gets an actual ask
plus some personality tacked on. (A *bare* forecast with no linked PR/issue
number and nothing else added is the case still worth holding — see
`SKILL.md`'s skip list.)

The same "don't leave it flat" instinct fires even when the linked PR isn't
fully done yet, or when the forecast is quietly settling a disagreement
between other commenters in the thread — two more closer variants beyond the
"reviewers welcome" one above:

> Draft: "Looks like the root cause got nailed down without needing a fresh
> repro — #43113 fixes the tooltip not passing the per-metric formatter key
> the way the series-label path does. That should cover both the
> percent-metric case here and @Prokos's Time Comparison scenario too."
> Final: em-dash swapped for a period, plus "...Time Comparison scenario
> too. Just needs a little PR touchup... almost there." appended.
> _(issue 33757 — the linked PR isn't merge-ready, so "almost there" reports
> real remaining work rather than declaring the issue closed.)_

> Draft: "The `onlyTotal` placement bug is fixed in #43238 — value labels now
> key off stackDimension so the total lands on the right stack group instead
> of always the last one. Should settle what @jpchev and @beliaev-maksim
> were going back and forth on above."
> Final: em-dash swapped for a period, plus "...going back and forth on
> above, but take a look and see what you think." appended.
> _(issue 33882 — when the fix's job is settling a dispute between other
> people in the thread, "should settle X" doesn't stand alone; it gets an
> invitation for the actual disputants to confirm rather than Evan declaring
> the debate over on their behalf.)_

When you redirect a thread to linked work, frame the close as an *invitation to
the reader* rather than a narration of your own plan. Draft "There's a draft PR
(#42150) fixing guest charts with missing or stale `query_context`... Following
that one instead of re-diagnosing here." → final "...Please feel free to
review/test there." (apache/superset#31872) — "Following that one instead of
re-diagnosing here" is about what *you're* doing; "please feel free to
review/test there" hands the reader something to do, which reads warmer and
keeps them engaged with the linked fix.

**Architecture questions can go far past the 35-word median.** When a report
turns on a genuinely open design question (not a triage-able bug), Evan will
trade brevity for a real root-cause trace: name the exact code path with
backticked identifiers, then lay out the open design questions as actual
prose questions (not a numbered list) rather than proposing a fix outright.
A ~230-word rewrite of a much shorter "let's move this to Discussion" draft
did exactly this on apache/superset#33900 (2026-09-07) — traced the bug to
`CategoricalColorNamespace.getScale(colorScheme)` being called fresh per
sub-chart, asked whether sub-charts should share one label-to-color mapping
and at what scope, whether seeding a shared map from a dashboard chart would
leak into `map_label_colors`, and whether there's a clean way to hand a scale
down into a child's `transformProps` versus a `superset-ui-core` API change
every plugin would feel — closing on a wry "Curious which way you'd lean,
since this is squarely in the color scheme architecture, which is...
complicated." The length is earned by the actual technical depth, not
padding; don't reach for this shape on a normal bug report or triage
question, where the median-length rules still apply.

**Security-sensitive reports**: tone shift confirmed, matches the PR-review
"dry, direct, no humor" rule on security exactly:
> "If you do see this (or anything else) as a true security vulnerability,
> it should be reported to security@superset.apache.org rather than posted
> as a public issue."

## Vocabulary/tics not covered by the PR-review corpus

- **Closing-reason typology specific to issues**: "won't fix", "discarded",
  "not-planned", "stale", "duplicate" - a PR has no equivalent taxonomy,
  it's just merged, closed, or in conflict.
- **Version-qualifier hedge in nearly every troubleshooting/closing
  comment**: "in current versions (3.x)", "on `master`", "2.0.1 or newer".
  A PR is pinned to one branch state and doesn't need this; an issue could
  be reported against any historical version.
- **`@dosu-bot` posted as the entire comment body**, zero other content,
  three separate times in the sample (2024-07-30, 2024-08-23, 2024-05-13).
  A real, minimal, issue-only tic: summoning the bot with nothing else
  attached, not even a question. Use sparingly and only when the situation
  actually calls for outsourcing triage to the bot.

## Diagnose, then volunteer

When a bug-triage comment does real root-cause diagnosis, the closing line
often flips from routing the fix to someone else into a short, hedged,
first-person offer to take it on. Drafts ending "worth a look from whoever
owns X" / "worth reviving... if anyone wants to pick it up" get a trailing
volunteer clause instead - "Taking a look myself...", "Looking into it...",
"Seeing if I can track down a fix.", "I'll see what I can do..." The tail is
appended after the diagnosis, not a replacement for it, and it's an intent,
not a status update - don't overcommit it into a guaranteed outcome or a
deadline; if you haven't started, "Looking into it..." is honest, "Fixed,
PR incoming" is not (see `anti-patterns.md` Tell #7).

> Reproducible as described, the summary row formatter isn't picking up the
> per-column number format. Worth a look from whoever owns the table chart
> plugin.
> → ...same per-column number format. Taking a look at opening a PR, I
> hope. (issue #39587)

> ...Might be worth teaching `downloadAsPdf`/`downloadAsImage` to force a
> full render before capturing, same as the bot path already does.
> → ...same as the bot path already does. Seeing if I can track down a
> fix. (issue #29719)

The same tail applies specifically to "I'll open a PR for this" when the
draft otherwise stopped cold on the diagnosis, with no tail at all:

> No `.npmrc` anywhere in the tree right now, so nothing stops `npm install`
> from grabbing a package published minutes ago. Matching Dependabot's
> existing 7-day cooldown in an `.npmrc` seems like a cheap add.
> → ...seems like a cheap add. I'll see about opening a PR on Superset
> itself. (issue #42983)

> Both rules are off in `oxlint.json` right now, so there's no number to
> trend against the "no any" goal we already claim to be working toward. A
> ratchet - on for directories already clean, reported elsewhere - seems
> like the way to start rather than a flag day.
> → ...working toward. I'll see about a Superset PR here... why not... (the
> ratchet-vs-flag-day reasoning got cut along with the tail added, issue
> #42984)

Note the second example also trims the reasoning for *how* to fix it once
the self-take tail is added - the volunteer offer can replace a paragraph of
justification, not just cap it.

Conversely, ending a genuine new-diagnosis comment by asking the reporter or
the crowd to send the fix, instead of volunteering yourself, is the skip
case, not a softened one - see "When a draft should not be posted at all" in
`SKILL.md`.

The self-take tail also rides along in its lightest form on a plain "up for
grabs" note — even when you're inviting the crowd to take it, tack on that you
might, rather than fully handing it off:

> ...`pivot_df` in `client_processing.py` is where the multiple Rows fields
> collapse into one column. Up for grabs if anyone wants to take a swing at it.
> → ...take a swing at it... or I might. (issue #32369)

> Still no PR here after over a year of reports. The `DATETIME(<col>)`
> computed-column workaround... is the real fix until someone traces why
> Google Sheets columns aren't typed as temporal in the first place. Still
> hitting this on a recent version?
> → ...in the first place. Assuming this is still the case in 6.x? Looking
> into it... (issue #30413)

The same instinct cuts the other direction on who gets *assigned* the fix: a
draft that named the reporter and told them to do it ("@NavinAsokan go for
it, an override of `get_schema_names`... would fix it") got the assignment
cut, keeping only the technical suggestion, unaddressed to anyone in
particular (issue #30678). Directing a specific reporter to go implement the
fix reads bossy; leaving it open, or taking it on yourself, doesn't.

## Voice evolution: pre-2020 reads differently

The ~17 non-superset repos (2016-2026 long tail) show a real shift.
**2016-2018** comments (strongloop/loopback, vitalets/angular-xeditable,
johnwalley/d3-simple-slider) are plain, functional, generic-OSS-commenter
voice: zero personality markers, no ellipsis-hesitation, no
self-deprecation, no emoticons:
> "Thanks... that explains why I couldn't find the code. I guess I'm out of
> luck... I'll close the issue, but if there's a solution you're aware of,
> let me know." (2017-02-13)

By **2020+**, even on other people's repos, the voice is fully consistent
with the rest of this skill - e.g. on mozilla/fxa in 2024: "Oh, almost
forgot to mention, we're using po2json 0.4.5, the 'newest' version :D".

**Treat 2016-2018 material as pre-voice and exclude it from exemplars.**
The documented voice crystallizes around 2020, which lines up with when
Evan's apache/superset involvement (and the rest of this skill's corpus)
picks up.

## Real outliers worth using as exemplars verbatim

> "Also worth mentioning: The `evans` github user is not me and has nothing
> to do with this project. Poor guy gets pinged all the time by this
> community. ;)" (2023-02-02)

> "CC @eschutho for input or confirmation of closability (which _should_ be
> a word)." (2022-12-20)

> "To say what everyone says in open source, contributions welcome/encouraged!"
> (2024-04-08) - self-aware acknowledgment of his own cliché, worth noting
> as a model for how to use a stock open-source phrase without it reading
> flat: name that it's a cliché rather than just deploying it earnestly.

> "Closing the issue due to a successful vote! 🎉 Thank you for taking this
> on!" (2022-01-04)

## Scope note

The em-dash rate in this corpus is 0.23% (11/4,785) - consistent with the
PR-review corpus's 0.4%. Unlike blog writing (see `blog-voice.md`), issue
comments do NOT need a correction to the em-dash rule; treat it the same
as PR review.
