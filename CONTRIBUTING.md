# Contributing to Claude Mods Marketplace

Thanks for building a mod! Here's how to get it into the marketplace.

## Creating a Mod

### Option A: Use the wizard (recommended)

In Claude Desktop, run:

```
/create-mod
```

This walks you through everything interactively.

### Option B: Manual creation

1. **Create a folder** in `mods/` with your mod name (kebab-case):
   ```
   mods/my-awesome-mod/
   ```

2. **Add `plugin.json`**:
   ```json
   {
     "name": "my-awesome-mod",
     "description": "One sentence describing what it does",
     "author": {
       "name": "Your GitHub Username"
     },
     "version": "1.0.0"
   }
   ```

3. **Add your mod file(s)**:
   - `SKILL.md` — for slash commands (skills, modes)
   - `CLAUDE.md` — for behavioral changes (styles, prompts)
   - Both — for modes that have a command AND change behavior

4. **Add an entry to `registry.json`**:
   ```json
   {
     "name": "my-awesome-mod",
     "displayName": "My Awesome Mod",
     "description": "One compelling sentence — this is what people see first",
     "author": "your-github-username",
     "category": "skills",
     "tags": ["tag1", "tag2", "tag3"],
     "version": "1.0.0",
     "verified": false,
     "downloads": 0,
     "stars": 0,
     "createdAt": "2026-04-05",
     "updatedAt": "2026-04-05",
     "weeklyDownloads": 0,
     "path": "mods/my-awesome-mod",
     "files": [
       { "src": "plugin.json", "dest": ".claude-plugin/plugin.json" },
       { "src": "SKILL.md", "dest": "skills/my-awesome-mod/SKILL.md" }
     ]
   }
   ```

## Submitting

### Option A: Use `/publish-mod` (recommended)

In Claude Desktop:
```
/publish-mod my-awesome-mod
```

This forks the repo, adds your mod, and opens a PR automatically.

### Option B: Manual PR

1. Fork this repo
2. Create a branch: `git checkout -b add-mod-my-awesome-mod`
3. Add your mod folder and update `registry.json`
4. Push and open a PR

## Quality Guidelines

Your mod is more likely to get merged (and verified) if it:

- **Has a clear, specific description** — "Makes Claude respond in haiku" not "Changes responses"
- **Does one thing well** — Focused mods are better than kitchen-sink mods
- **Has tested instructions** — Run your mod and verify Claude follows the instructions correctly
- **Uses proper frontmatter** — All required fields present and correct
- **Doesn't conflict** — Doesn't override other mods' functionality

## Categories

| Category | Use When | Main File |
|----------|----------|-----------|
| `skills` | Adding a new slash command | `SKILL.md` |
| `styles` | Changing response format/tone | `CLAUDE.md` |
| `prompts` | Pre-loading domain knowledge | `CLAUDE.md` |
| `modes` | Behavioral overhaul + command | Both |
| `agents` | Custom sub-agent | `agents/*.md` |
| `hooks` | Event-triggered automation | `hooks/hooks.json` |

## Verified Badge

The repo maintainer may add `"verified": true` to your mod after review. Verified mods:
- Are reviewed for quality and safety
- Show a checkmark in the marketplace
- Are more likely to be featured

## Files Reference

### `files` array in registry.json

Maps source files to their install destination:

```json
"files": [
  { "src": "plugin.json", "dest": ".claude-plugin/plugin.json" },
  { "src": "CLAUDE.md", "dest": "CLAUDE.md" },
  { "src": "SKILL.md", "dest": "skills/mod-name/SKILL.md" }
]
```

- `src` — filename in the `mods/<name>/` folder
- `dest` — path inside `~/.claude/plugins/<name>/` where it gets installed

## Questions?

Open an issue or ask in Claude Desktop using `/mods`.
