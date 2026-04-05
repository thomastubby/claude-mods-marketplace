# Claude Mods Marketplace

The community-powered customization platform for Claude Desktop. Browse, install, and share mods that transform your Claude experience.

## What Are Mods?

Mods are drop-in customizations for Claude Desktop. Install one and Claude instantly gains new capabilities, changes its response style, or loads domain expertise.

| Category | What It Does | Example |
|----------|-------------|---------|
| **Skills** | New slash commands | `/auto-doc` generates full project documentation |
| **Styles** | Changes how Claude responds | Concise Coder: zero fluff, maximum code |
| **Prompts** | Pre-loads domain expertise | React Expert: React 19 + Next.js 15 knowledge |
| **Modes** | Behavioral overhauls | Genius Mode: autonomous builder that runs until done |
| **Agents** | Custom sub-agents | Specialized agents Claude can spawn |
| **Hooks** | Auto-triggered behaviors | Linting, formatting, security scanning on events |

## Quick Start

### 1. Install the Marketplace

Copy the `claude-mods` plugin to your Claude plugins directory:

```bash
# Clone this repo
git clone https://github.com/thomastubby/claude-mods-marketplace.git

# Copy the marketplace plugin
cp -r claude-mods-marketplace ~/.claude/plugins/claude-mods
```

Or manually copy the `claude-mods` folder from this repo into `~/.claude/plugins/`.

### 2. Restart Claude Desktop

Close and reopen Claude Desktop to load the new plugins.

### 3. Browse & Install

```
/mods                        Browse the full marketplace
/mods trending               See what's popular this week
/mods install genius-mode    Install a mod
/mods search security        Search by keyword
/mods installed              See your installed mods
```

## Available Mods

### Verified

These mods are reviewed for quality and safety.

| Mod | Category | Description |
|-----|----------|-------------|
| **Genius Creator Mode** | modes | Autonomous builder — give it an idea, it builds everything until done |
| **Concise Coder** | styles | Minimal responses, maximum code, zero fluff |
| **React Expert** | prompts | Deep React 19, Next.js 15, TypeScript expertise |
| **Auto Documenter** | skills | Scans your codebase, generates full documentation |
| **Security Auditor** | prompts | OWASP-aware vulnerability scanner |
| **Pair Programmer** | modes | Thinks out loud, asks questions, collaborates |
| **Senior Engineer** | styles | Opinionated, pragmatic, production-focused |
| **DevOps Mode** | prompts | Infrastructure, CI/CD, Docker, K8s, Terraform |

## Contributing

Want to share your own mod? See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

**Quick version:**

1. Fork this repo
2. Create your mod in `mods/<your-mod-name>/`
3. Add an entry to `registry.json`
4. Open a PR

Or use `/publish-mod` inside Claude Desktop to automate the entire flow.

## Mod Structure

Every mod needs at minimum:

```
mods/your-mod-name/
├── plugin.json          # Required: name, description, author
└── SKILL.md             # For skills/modes: slash command definition
    or
└── CLAUDE.md            # For styles/prompts: behavioral instructions
```

### plugin.json

```json
{
  "name": "your-mod-name",
  "description": "What your mod does",
  "author": {
    "name": "Your Name"
  },
  "version": "1.0.0"
}
```

### SKILL.md (for skills and modes)

```markdown
---
name: your-command
description: "When Claude should invoke this"
argument-hint: "[optional args]"
allowed-tools: [Read, Write, Bash]
---

# Your Skill Name

Instructions for Claude on how to execute this skill.
```

### CLAUDE.md (for styles and prompts)

```markdown
# Your Mod Name

Instructions that modify Claude's behavior, loaded automatically.
```

## License

MIT
