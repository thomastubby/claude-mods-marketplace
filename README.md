<p align="center">
  <img src="assets/banner.svg" alt="Claude Mods Marketplace" width="100%"/>
</p>

<p align="center">
  <strong>The community-powered customization platform for Claude Desktop.</strong><br/>
  Browse, install, and share mods that transform your Claude experience.
</p>

<p align="center">
  <a href="#-quick-start"><img src="https://img.shields.io/badge/Get_Started-F59E0B?style=for-the-badge&logo=rocket&logoColor=white" alt="Get Started"/></a>
  <a href="#-available-mods"><img src="https://img.shields.io/badge/Browse_24_Mods-1a1a2e?style=for-the-badge&logo=puzzle-piece&logoColor=F59E0B" alt="Browse Mods"/></a>
  <a href="#-modpacks"><img src="https://img.shields.io/badge/Modpacks-0f3460?style=for-the-badge&logo=package&logoColor=F59E0B" alt="Modpacks"/></a>
  <a href="CONTRIBUTING.md"><img src="https://img.shields.io/badge/Contribute-0f3460?style=for-the-badge&logo=github&logoColor=white" alt="Contribute"/></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/mods-24_verified-F59E0B?style=flat-square" alt="24 Verified Mods"/>
  <img src="https://img.shields.io/badge/modpacks-4-D97706?style=flat-square" alt="4 Modpacks"/>
  <img src="https://img.shields.io/badge/categories-7-16213e?style=flat-square" alt="7 Categories"/>
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT License"/>
</p>

---

## What Are Mods?

Mods are **drop-in customizations** for Claude Desktop. Install one and Claude instantly gains new capabilities, changes its response style, or loads domain expertise. No code required.

<table>
<tr>
<td align="center" width="140"><br/><strong>Skills</strong><br/><sub>New slash commands</sub><br/><br/></td>
<td align="center" width="140"><br/><strong>Styles</strong><br/><sub>Change response tone</sub><br/><br/></td>
<td align="center" width="140"><br/><strong>Prompts</strong><br/><sub>Domain expertise</sub><br/><br/></td>
<td align="center" width="140"><br/><strong>Modes</strong><br/><sub>Behavioral overhauls</sub><br/><br/></td>
<td align="center" width="140"><br/><strong>Agents</strong><br/><sub>Custom sub-agents</sub><br/><br/></td>
<td align="center" width="140"><br/><strong>Hooks</strong><br/><sub>Auto-triggered actions</sub><br/><br/></td>
<td align="center" width="140"><br/><strong>Modpacks</strong><br/><sub>Curated bundles</sub><br/><br/></td>
</tr>
</table>

---

## Quick Start

### 1. Clone and Copy Files

```bash
git clone https://github.com/thomastubby/claude-mods-marketplace.git
cd claude-mods-marketplace
```

Copy the mod sources so the marketplace can install mods locally:

```bash
# Create the local mod registry
mkdir -p ~/.claude/plugins/claude-mods
cp registry.json ~/.claude/plugins/claude-mods/
cp -r mods ~/.claude/plugins/claude-mods/mod-sources
cp -r modpacks ~/.claude/plugins/claude-mods/modpacks
```

### 2. Install the Marketplace Plugin

Copy the marketplace plugin into the official plugins directory and register it:

```bash
# Copy plugin files
mkdir -p ~/.claude/plugins/marketplaces/claude-plugins-official/plugins/claude-mods-marketplace/.claude-plugin
mkdir -p ~/.claude/plugins/marketplaces/claude-plugins-official/plugins/claude-mods-marketplace/skills/mods

cp mods/modpack-manager/plugin.json \
   ~/.claude/plugins/marketplaces/claude-plugins-official/plugins/claude-mods-marketplace/.claude-plugin/plugin.json
```

Then add the marketplace entry to the marketplace manifest. Open `~/.claude/plugins/marketplaces/claude-plugins-official/.claude-plugin/marketplace.json` and add this to the `plugins` array:

```json
{
  "name": "claude-mods-marketplace",
  "description": "Browse, install, and manage community mods for Claude Desktop",
  "author": { "name": "Claude Mods" },
  "source": "./plugins/claude-mods-marketplace",
  "category": "productivity"
}
```

Commit the change into the marketplace git repo:

```bash
cd ~/.claude/plugins/marketplaces/claude-plugins-official
git add plugins/claude-mods-marketplace .claude-plugin/marketplace.json
git commit -m "Add Claude Mods Marketplace plugin"
```

### 3. Enable the Plugin

Add the plugin to your enabled plugins in `~/.claude/settings.json`:

```json
{
  "enabledPlugins": {
    "claude-mods-marketplace@claude-plugins-official": true
  }
}
```

If you already have content in `settings.json`, just add the `enabledPlugins` key.

### 4. Restart Claude Desktop

Close and reopen Claude Desktop. Type `/mods` to see the marketplace.

### 5. Browse & Install

```
/mods                             Browse the full marketplace
/mods install no-yapping          Install a mod
/modpack install power-user-pack  Install a bundle of mods at once
```

> **Tip:** After installing mods with skills (slash commands), you'll need to add them to `enabledPlugins` in `settings.json` and restart Claude Desktop for the new commands to appear.

---

## Available Mods

### Skills — New Commands

| Mod | Description |
|-----|-------------|
| **Git Unfuck** `/git-unfuck` | Diagnoses and fixes messy git states \u2014 detached HEAD, botched rebases, wrong-branch commits |
| **Ship It** `/ship-it` | Generates Dockerfiles, CI pipelines, docker-compose, and env configs for your stack |
| **Deep Code Review** `/deep-review` | Senior-level review: security, performance, correctness, maintainability. Rates 1-5. |
| **Auto Documenter** `/auto-doc` | Scans your codebase, generates README, architecture docs, API reference |
| **Explain Like a Diff** `/explain-diff` | Turns git history into changelogs for devs, PMs, and users |
| **Incident Commander** `/incident` | Structured incident response: triage, diagnosis, comms templates, post-mortem |

### Styles — Change How Claude Responds

| Mod | Description |
|-----|-------------|
| **No Yapping** | Eliminates ALL filler, hedging, and sycophancy. Every word earns its place. |
| **Concise Coder** | Minimal responses, maximum code. Zero fluff. |
| **Senior Engineer** | Opinionated, pragmatic, production-focused. Pushes back on bad ideas. |
| **Academic Writer** | Structured sections, citations, formal methodology, confidence levels. |

### Prompts — Pre-loaded Expertise

| Mod | Description |
|-----|-------------|
| **React Expert** | React 19, Next.js 15, TypeScript, Tailwind. Server Components, App Router. |
| **Security Auditor** | OWASP Top 10, CVE awareness, vulnerability scanning, remediation guidance. |
| **Rust Whisperer** | Ownership mental models, async internals, idiomatic patterns. |
| **Startup CTO** | Optimizes for shipping speed, team size, and runway. Monolith first. |
| **Data Pipeline Pro** | dbt, Airflow, Spark, Snowflake, BigQuery mastery. |
| **DevOps Mode** | Docker, Kubernetes, Terraform, CI/CD, monitoring. |
| **Technical Writer** | Diataxis framework, scannable docs, example-rich. Never says "simply." |

### Modes — Behavioral Overhauls

| Mod | Description |
|-----|-------------|
| **Genius Creator** `/genius` | Autonomous builder \u2014 give it an idea, it builds everything until done. |
| **Focus Mode** | Locks you into one task. Resists scope creep. Parks distractions. |
| **Architect Mode** | Refuses to write code. Produces diagrams, ADRs, API contracts, specs. |
| **Devil's Advocate** | Argues against every decision to stress-test your ideas. |
| **Pair Programmer** | Thinks out loud, asks questions, suggests alternatives. |
| **TDD Coach** | Enforces red-green-refactor. Tests first, always. |
| **Teach Me** | Socratic learning \u2014 guides you to discover answers yourself. |

---

## Modpacks

**Modpacks are curated bundles.** Install a complete Claude setup with one command. Save your own setup as a modpack and share it with the community.

| Modpack | Mods | Description |
|---------|------|-------------|
| **Power User Pack** | 8 mods | No Yapping + Genius Mode + Deep Review + Focus Mode + more |
| **Startup Founder Kit** | 5 mods | Startup CTO + Genius Mode + Ship It + No Yapping + Architect |
| **Full Stack Dev Kit** | 6 mods | Concise Coder + React Expert + Deep Review + Ship It + Git Unfuck + Security |
| **Learning Path** | 4 mods | Teach Me + Pair Programmer + TDD Coach + Deep Review |

```
/modpack install power-user-pack    Install 8 mods at once
/modpack save my-setup              Save your current mods as a modpack
/modpack share my-setup             Publish your modpack for others
/modpack list                       Browse available modpacks
```

---

## Commands Reference

```
/mods                          Browse the full marketplace
/mods install <name>           Install a mod
/mods uninstall <name>         Remove a mod
/mods search <query>           Search by keyword
/mods trending                 Most popular this week
/mods new                      Recently added
/mods category <cat>           Filter by category
/mods info <name>              Detailed mod information
/mods installed                List your installed mods

/modpack install <name>        Install a bundle of mods
/modpack save <name>           Save your current setup
/modpack share <name>          Publish your modpack
/modpack list                  Browse modpacks

/create-mod                    Interactive wizard to build a new mod
/publish-mod <name>            Submit a mod to the marketplace via PR
```

---

## Contributing

We welcome community mods! See the full [Contributing Guide](CONTRIBUTING.md).

1. Fork this repo
2. Add your mod to `mods/<your-mod-name>/`
3. Add an entry to `registry.json`
4. Open a PR

Or use **`/publish-mod`** inside Claude Desktop to automate the entire flow.

### Verified Badge

The maintainer may add the **Verified** badge after review. Verified mods show a checkmark in the marketplace and are featured more prominently.

---

## License

MIT

---

<p align="center">
  <img src="assets/logo.svg" width="40" alt="Claude Mods"/>
  <br/>
  <sub>Built for the Claude community</sub>
</p>
