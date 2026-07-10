# evan-writing-patterns

A Claude Code skill that captures how I actually write: GitHub PR reviews, issue comments, discussion replies, general responses, and long-form blog posts. Built from three corpora: ~6,000 verified-human PR review comments on apache/superset contrasted against AI/agent comments from the same account, 4,785 issue comments (a distinct register from PR review — see `references/issue-voice.md`), and separately, 39 of my preset.io/blog posts, since long-form writing has a genuinely different rhythm than short GitHub comments and doesn't follow the same rules (see `references/blog-voice.md`).

The goal is to make AI-drafted output sound like me instead of an LLM wearing my handle.

## Using this in another project

Copy (or symlink) this directory into a project's `.claude/skills/` folder, e.g.:

```
git clone https://github.com/rusackas/evan-writing-patterns.git ~/.claude/skills/rusackas-review-voice
```

or per-project:

```
git submodule add https://github.com/rusackas/evan-writing-patterns.git .claude/skills/rusackas-review-voice
```

## Contents

- `SKILL.md` — the core voice guide: hard numbers, vocabulary/tics, situational playbook, anti-pattern summary.
- `references/exemplars.md` — real comments grouped by situation, for matching tone before writing.
- `references/anti-patterns.md` — the statistical AI tells, with real before/after rewrites.
- `references/apply-able-suggestions.md` — how to post a concrete code fix as a one-click GitHub "Apply suggestion" instead of prose.
- `references/blog-voice.md` — long-form blog voice: genre splits (personal/technical vs. newsletter vs. marketing), vocabulary and structural habits specific to blog writing, and where the short-GitHub-comment rules (like the em-dash rule) do NOT apply.
- `references/issue-voice.md` — GitHub issue-comment voice as distinct from PR review: bug triage style, feature-request redirects, the stale-close template, and why issue comments run longer than PR review comments.

## Updating

This file gets refined over time as new tells or phrasing preferences come up in real review sessions. Edit directly and commit, no fixed process.
