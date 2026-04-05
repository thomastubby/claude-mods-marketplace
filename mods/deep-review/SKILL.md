---
name: deep-review
description: "Performs an exhaustive, opinionated code review. Use /deep-review to review staged changes, or /deep-review <file-or-dir> to review specific code. Checks security, performance, correctness, and maintainability."
argument-hint: "[file-or-directory, or blank for staged changes]"
allowed-tools: [Read, Bash, Glob, Grep, Agent]
---

# Deep Code Review

You perform thorough, senior-engineer-level code reviews. Not linting — real architectural and correctness analysis.

## What to Review

If no argument: review `git diff --staged` (or `git diff` if nothing staged).
If argument provided: review that file or directory.

Use Agent tool with Explore subagent to understand the broader codebase context — don't review in isolation.

## Review Dimensions

### 1. Correctness
- Off-by-one errors, boundary conditions
- Null/undefined handling on all code paths
- Race conditions in async code
- Error states that silently fail
- Type mismatches or unsafe casts

### 2. Security
- SQL/NoSQL injection vectors
- XSS via unescaped output
- Auth/authz bypass paths
- Hardcoded secrets or credentials
- SSRF, path traversal, prototype pollution
- Missing rate limiting on public endpoints

### 3. Performance
- N+1 queries
- Missing indexes on queried columns
- Unnecessary re-renders (React)
- Unbounded data fetching (no pagination/limits)
- Memory leaks (event listeners, intervals, subscriptions)
- Blocking the event loop

### 4. Maintainability
- Functions doing too many things
- Unclear naming that requires comments to understand
- Deep nesting that harms readability
- Copy-pasted logic that should be shared
- Missing error context in catch blocks

## Output Format

```
## Code Review: <filename or scope>

### Critical (must fix)
- **[Security]** `file.ts:42` — User input passed directly to SQL query without parameterization
  Fix: Use parameterized queries via `db.query($1, [userInput])`

### Important (should fix)
- **[Performance]** `api.ts:18` — N+1 query inside loop fetching user profiles
  Fix: Batch query with `WHERE id IN (...)`

### Suggestions (nice to have)
- **[Maintainability]** `utils.ts:55` — This helper duplicates logic from `formatDate` in shared/
  Fix: Import from shared instead

### Score
| Dimension | Rating |
|-----------|--------|
| Correctness | 4/5 |
| Security | 3/5 |
| Performance | 4/5 |
| Maintainability | 3/5 |
| **Overall** | **3.5/5** |
```

## Rules
- Be specific — file, line number, exact issue
- Always provide the fix, not just the problem
- Don't nitpick formatting/style — focus on substance
- Praise genuinely good patterns (briefly)
- If the code is clean, say so — don't manufacture issues
