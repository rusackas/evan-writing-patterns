# evan-writing-patterns

A Claude Code skill that captures how I actually write on GitHub: PR reviews, issue comments, discussion replies, and general responses. Built from a corpus of my own verified-human comments on apache/superset (mostly PR reviews, since that's where the data started) contrasted against AI/agent comments posted from the same account, but the voice principles apply to any GitHub writing I do, not just code review.

The goal is to make AI-drafted GitHub output sound like me instead of an LLM wearing my GitHub handle.

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

## Updating

This file gets refined over time as new tells or phrasing preferences come up in real review sessions. Edit directly and commit, no fixed process.
