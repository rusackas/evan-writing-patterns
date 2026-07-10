# evan-writing-patterns

A Claude Code skill that captures how I actually write: GitHub PR reviews, issue comments, discussion replies, general responses, and long-form blog posts. Built from two corpora: verified-human GitHub comments on apache/superset (mostly PR reviews, since that's where the data started, but the principles apply to any GitHub writing) contrasted against AI/agent comments from the same account, and separately, 39 of my preset.io/blog posts, since long-form writing has a genuinely different rhythm than short GitHub comments and doesn't follow the same rules (see `references/blog-voice.md`).

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

## Updating

This file gets refined over time as new tells or phrasing preferences come up in real review sessions. Edit directly and commit, no fixed process.
