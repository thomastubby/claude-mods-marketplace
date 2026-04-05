---
name: modpack
description: "Save, share, and install curated bundles of mods (modpacks). Use /modpack save <name> to snapshot your current mods, /modpack install <name> to install a shared modpack, /modpack list to see available modpacks, /modpack share <name> to publish to the marketplace."
argument-hint: "save <name>|install <name>|list|share <name>|info <name>"
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, AskUserQuestion, TodoWrite]
---

# Modpack Manager

Modpacks are curated bundles of mods — a complete Claude setup in one install. Users can save their current mod configuration as a modpack and share it so others can replicate their exact setup.

## Commands

### `/modpack save <name>`

Snapshots the user's currently installed mods into a modpack file.

1. Scan `~/.claude/plugins/` for all installed mod directories
2. For each directory with a `.claude-plugin/plugin.json`, record the mod name
3. Ask the user for:
   - **Display name** for the modpack (e.g., "Full Stack Developer Kit")
   - **Description** (one compelling sentence)
   - **Tags** (2-5 descriptive words)
4. Save to `~/.claude/modpacks/<name>.json`:

```json
{
  "name": "fullstack-dev-kit",
  "displayName": "Full Stack Developer Kit",
  "description": "Everything a full-stack dev needs — concise responses, React expertise, code review, deployment tools, and git recovery.",
  "author": "<github-username>",
  "version": "1.0.0",
  "createdAt": "<today>",
  "mods": [
    "no-yapping",
    "react-expert",
    "deep-review",
    "ship-it",
    "git-unfuck",
    "security-auditor"
  ]
}
```

5. Confirm:
```
   Saved modpack "Full Stack Developer Kit" with 6 mods:
     no-yapping, react-expert, deep-review,
     ship-it, git-unfuck, security-auditor

   Share it: /modpack share fullstack-dev-kit
```

### `/modpack install <name>`

Installs all mods in a modpack at once.

1. Look for the modpack:
   - First check `~/.claude/modpacks/<name>.json` (local)
   - Then check `~/.claude/plugins/claude-mods/modpacks/<name>.json` (from marketplace)
   - Then check the registry for a modpack entry
2. Read the modpack's `mods` array
3. For each mod, run the same install logic as `/mods install`:
   - Check if already installed (skip if so)
   - Copy from mod-sources into `~/.claude/plugins/<mod-name>/`
4. Report results:

```
   Installed modpack "Full Stack Developer Kit"

   Installed:
     no-yapping, react-expert, deep-review,
     ship-it, git-unfuck, security-auditor

   Already installed (skipped):
     concise-coder

   Restart Claude Desktop to activate all mods.
```

### `/modpack list`

Shows all available modpacks — both local (saved by user) and marketplace (shared by community).

```
   YOUR MODPACKS
    fullstack-dev-kit    6 mods    Full Stack Developer Kit
    data-eng-setup       4 mods    Data Engineering Setup

   MARKETPLACE MODPACKS
    power-user-pack      8 mods    The ultimate power user setup
    startup-founder      5 mods    Ship fast, break nothing
```

### `/modpack info <name>`

Shows detailed modpack info including every mod in the pack.

```
   Full Stack Developer Kit
   by thomastubby | 6 mods | v1.0.0

   Everything a full-stack dev needs — concise responses,
   React expertise, code review, deployment, and git recovery.

   Included Mods:
     1. No Yapping           styles    Eliminates all filler
     2. React Expert         prompts   React 19 + Next.js 15
     3. Deep Code Review     skills    Senior-level code review
     4. Ship It              skills    Production deployment
     5. Git Unfuck           skills    Git disaster recovery
     6. Security Auditor     prompts   OWASP vulnerability scanner

   /modpack install fullstack-dev-kit
```

### `/modpack share <name>`

Publishes a local modpack to the marketplace GitHub repo via PR.

1. Read the modpack from `~/.claude/modpacks/<name>.json`
2. Verify all mods in the pack exist in the marketplace registry
3. Fork the marketplace repo (if not already forked)
4. Add the modpack file to `modpacks/<name>.json` in the repo
5. Add a modpack entry to `registry.json`
6. Open a PR

```
   Shared "Full Stack Developer Kit" to the marketplace!
   PR: https://github.com/thomastubby/claude-mods-marketplace/pull/42

   Once merged, anyone can install it with:
   /modpack install fullstack-dev-kit
```

## Modpack Registry Entry Format

Modpacks appear in the registry alongside regular mods:

```json
{
  "name": "fullstack-dev-kit",
  "displayName": "Full Stack Developer Kit",
  "description": "Everything a full-stack dev needs",
  "author": "thomastubby",
  "category": "modpacks",
  "tags": ["fullstack", "react", "devops"],
  "version": "1.0.0",
  "verified": false,
  "downloads": 0,
  "stars": 0,
  "createdAt": "2026-04-05",
  "updatedAt": "2026-04-05",
  "weeklyDownloads": 0,
  "path": "modpacks/fullstack-dev-kit",
  "mods": ["no-yapping", "react-expert", "deep-review", "ship-it", "git-unfuck", "security-auditor"]
}
```

## Rules

- When saving, only include mods that exist in the marketplace registry (not custom local-only plugins)
- When installing, gracefully handle mods that aren't available (warn and skip)
- Modpacks should have 3-10 mods — warn if outside this range
- Always show what will be installed before doing it
- Create `~/.claude/modpacks/` directory if it doesn't exist
