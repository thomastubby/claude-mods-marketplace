---
name: explain-diff
description: "Generates human-readable changelogs and release notes from git history. Use /explain-diff to summarize recent commits, or /explain-diff v1.0..v1.1 for a specific range."
argument-hint: "[commit-range, branch, or number of commits]"
allowed-tools: [Bash, Read, Glob, Grep]
---

# Explain Like a Diff

Turn git history into clear, readable narratives for different audiences.

## Input Parsing

- No argument: last 10 commits on current branch
- Number (e.g., `20`): last N commits
- Range (e.g., `v1.0..v1.1` or `main..feature`): commits in that range
- Branch name: commits on that branch not on main

## Process

1. Run `git log --oneline --no-merges <range>` to get the commit list
2. Run `git diff --stat <range>` to understand scope
3. Read key changed files to understand what actually changed
4. Group changes by category: Features, Bug Fixes, Refactoring, Performance, Documentation, Chores

## Output: Three Versions

### Developer Changelog
Detailed, technical, grouped by category with commit refs:
```
## What Changed

### Features
- Add WebSocket support for real-time notifications (abc1234)
- New /api/v2/users endpoint with pagination (def5678)

### Bug Fixes
- Fix race condition in session cleanup (ghi9012)

### Refactoring
- Extract auth middleware into shared package (jkl3456)
```

### Product Manager Summary
Non-technical, focused on user impact:
```
## Summary
This release adds real-time notifications and improves API performance.
Users will see instant updates instead of polling. The user management
API now supports pagination for better performance with large datasets.
```

### User-Facing Release Notes
Polished, ready to publish:
```
## What's New
- Real-time notifications — see updates instantly
- Faster user directory for large teams
- Fixed an issue where sessions occasionally expired early
```

## Rules
- Read actual code changes, don't just summarize commit messages
- Highlight breaking changes prominently with migration steps
- Link to PRs/issues when referenced in commits
- Flag security-related changes explicitly
