# evan-writing-patterns

A Claude Code skill that captures how I actually write: GitHub PR reviews, issue comments, discussion replies, general responses, and long-form blog posts. Built from three corpora: ~6,000 verified-human PR review comments on apache/superset contrasted against AI/agent comments from the same account, 4,785 issue comments (a distinct register from PR review — see `references/issue-voice.md`), and separately, 39 of my preset.io/blog posts, since long-form writing has a genuinely different rhythm than short GitHub comments and doesn't follow the same rules (see `references/blog-voice.md`).

The goal is to make AI-drafted output sound like me instead of an LLM wearing my handle.

## Layout

The repo is a Claude plugin marketplace holding one plugin, `rusackas-voice`,
which holds one skill:

```
.claude-plugin/marketplace.json     the marketplace (name: evan-writing-patterns)
.claude-plugin/plugin.json          the plugin (name: rusackas-voice)
skills/rusackas-review-voice/       the skill: SKILL.md and references/
```

## Using it

On claude.ai or the desktop app: Customize > Plugins > Add marketplace, enter
`rusackas/evan-writing-patterns`, and turn on "Sync automatically".

In Claude Code, as a plugin:

```
claude plugin marketplace add rusackas/evan-writing-patterns
claude plugin install rusackas-voice@evan-writing-patterns
```

In Claude Code, as a plain skill at a stable path (what the Superset
maintenance tooling expects):

```
git clone https://github.com/rusackas/evan-writing-patterns.git ~/.claude/skill-repos/evan-writing-patterns
ln -s ../skill-repos/evan-writing-patterns/skills/rusackas-review-voice ~/.claude/skills/rusackas-review-voice
```

Use one of the two Claude Code routes, not both, or the skill loads twice.

## Contents

Paths below are relative to `skills/rusackas-review-voice/`.

- `SKILL.md` — the core voice guide: hard numbers, vocabulary/tics, situational playbook, anti-pattern summary.
- `references/exemplars.md` — real comments grouped by situation, for matching tone before writing.
- `references/anti-patterns.md` — the statistical AI tells, with real before/after rewrites.
- `references/apply-able-suggestions.md` — how to post a concrete code fix as a one-click GitHub "Apply suggestion" instead of prose.
- `references/blog-voice.md` — long-form blog voice: genre splits (personal/technical vs. newsletter vs. marketing), vocabulary and structural habits specific to blog writing, and where the short-GitHub-comment rules (like the em-dash rule) do NOT apply.
- `references/issue-voice.md` — GitHub issue-comment voice as distinct from PR review: bug triage style, feature-request redirects, the stale-close template, and why issue comments run longer than PR review comments.

## Updating

The skill is refined as new tells or phrasing preferences come up in real
sessions. Make the change in a worktree off `origin/main`, commit, and push
`HEAD:main`; see "Maintaining this skill" at the end of `SKILL.md`. Leave
`version` out of both manifests so each commit is picked up as an update.
