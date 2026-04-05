<p align="center">
  <img src="assets/banner.svg" alt="Claude Mods Marketplace" width="100%"/>
</p>

<p align="center">
  <strong>The community-powered customization platform for Claude Desktop.</strong><br/>
  Browse, install, and share mods that transform your Claude experience.
</p>

<p align="center">
  <a href="#-quick-start"><img src="https://img.shields.io/badge/Get_Started-F59E0B?style=for-the-badge&logo=rocket&logoColor=white" alt="Get Started"/></a>
  <a href="#-available-mods"><img src="https://img.shields.io/badge/Browse_Mods-1a1a2e?style=for-the-badge&logo=puzzle-piece&logoColor=F59E0B" alt="Browse Mods"/></a>
  <a href="CONTRIBUTING.md"><img src="https://img.shields.io/badge/Contribute-0f3460?style=for-the-badge&logo=github&logoColor=white" alt="Contribute"/></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/mods-8_verified-F59E0B?style=flat-square" alt="8 Verified Mods"/>
  <img src="https://img.shields.io/badge/categories-6-16213e?style=flat-square" alt="6 Categories"/>
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT License"/>
  <img src="https://img.shields.io/badge/community-open_source-blue?style=flat-square" alt="Open Source"/>
</p>

---

## What Are Mods?

Mods are **drop-in customizations** for Claude Desktop. Install one and Claude instantly gains new capabilities, changes its response style, or loads domain expertise. No code required.

<table>
<tr>
<td align="center" width="160"><br/><strong>Skills</strong><br/><sub>New slash commands</sub><br/><br/></td>
<td align="center" width="160"><br/><strong>Styles</strong><br/><sub>Change response tone</sub><br/><br/></td>
<td align="center" width="160"><br/><strong>Prompts</strong><br/><sub>Domain expertise</sub><br/><br/></td>
<td align="center" width="160"><br/><strong>Modes</strong><br/><sub>Behavioral overhauls</sub><br/><br/></td>
<td align="center" width="160"><br/><strong>Agents</strong><br/><sub>Custom sub-agents</sub><br/><br/></td>
<td align="center" width="160"><br/><strong>Hooks</strong><br/><sub>Auto-triggered actions</sub><br/><br/></td>
</tr>
</table>

---

## Quick Start

### 1. Install the Marketplace

```bash
# Clone this repo
git clone https://github.com/thomastubby/claude-mods-marketplace.git

# Copy the marketplace plugin into Claude's plugin directory
cp -r claude-mods-marketplace ~/.claude/plugins/claude-mods
```

### 2. Restart Claude Desktop

Close and reopen Claude Desktop to load the marketplace.

### 3. Browse & Install

```
/mods                        Browse the full marketplace
/mods trending               See what's popular this week
/mods install genius-mode    Install a mod
/mods search security        Search by keyword
/mods installed              See your installed mods
```

That's it. One command to browse, one command to install.

---

## Available Mods

### Verified Mods

> Reviewed for quality and safety by the maintainer.

<table>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★★-F59E0B?style=flat-square&logo=star&logoColor=white" alt="5 stars"/>
</td>
<td>
<strong>Genius Creator Mode</strong> &nbsp; <code>modes</code><br/>
<sub>Autonomous feature builder — give it an idea, it plans, codes, tests, and iterates until done. Zero hand-holding.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★★-F59E0B?style=flat-square&logo=star&logoColor=white" alt="5 stars"/>
</td>
<td>
<strong>Concise Coder</strong> &nbsp; <code>styles</code><br/>
<sub>Minimal responses, maximum code. No fluff, no filler, no hand-holding — just clean output.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★☆-F59E0B?style=flat-square&logo=star&logoColor=white" alt="4 stars"/>
</td>
<td>
<strong>React Expert</strong> &nbsp; <code>prompts</code><br/>
<sub>Deep React 19, Next.js 15, TypeScript, and Tailwind expertise pre-loaded. Server Components, App Router, modern patterns.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★☆-F59E0B?style=flat-square&logo=star&logoColor=white" alt="4 stars"/>
</td>
<td>
<strong>Auto Documenter</strong> &nbsp; <code>skills</code><br/>
<sub>Scans your entire codebase and generates README, architecture docs, API reference, and setup guides.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★★-F59E0B?style=flat-square&logo=star&logoColor=white" alt="5 stars"/>
</td>
<td>
<strong>Security Auditor</strong> &nbsp; <code>prompts</code><br/>
<sub>OWASP-aware code scanner. Finds vulnerabilities, suggests fixes, checks dependencies for known CVEs.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★☆-F59E0B?style=flat-square&logo=star&logoColor=white" alt="4 stars"/>
</td>
<td>
<strong>Pair Programmer</strong> &nbsp; <code>modes</code><br/>
<sub>Thinks out loud, asks clarifying questions, suggests alternatives. Like pairing with a senior dev.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★★-F59E0B?style=flat-square&logo=star&logoColor=white" alt="5 stars"/>
</td>
<td>
<strong>Senior Engineer</strong> &nbsp; <code>styles</code><br/>
<sub>Opinionated, pragmatic, production-focused. Reviews code like a staff engineer. Ship-quality feedback.</sub>
</td>
</tr>
<tr>
<td width="50" align="center">
<img src="https://img.shields.io/badge/★★★★☆-F59E0B?style=flat-square&logo=star&logoColor=white" alt="4 stars"/>
</td>
<td>
<strong>DevOps Mode</strong> &nbsp; <code>prompts</code><br/>
<sub>Infrastructure, CI/CD, Docker, Kubernetes, Terraform expertise. Thinks in pipelines and deploys.</sub>
</td>
</tr>
</table>

---

## How It Works

```
/mods                          Full marketplace with featured & trending
/mods install <name>           Download and install a mod
/mods uninstall <name>         Remove an installed mod
/mods search <query>           Search by keyword
/mods trending                 Most popular this week
/mods new                      Recently added
/mods popular                  All-time most installed
/mods category <cat>           Filter by category
/mods info <name>              Detailed mod information
/mods installed                List your installed mods
/mods update <name>            Update to latest version
```

### Create Your Own

```
/create-mod                    Interactive wizard to build a new mod
/publish-mod <name>            Package and submit to the marketplace via PR
```

---

## Contributing

We welcome community mods! See the full [Contributing Guide](CONTRIBUTING.md) for details.

**Quick version:**

1. Fork this repo
2. Add your mod to `mods/<your-mod-name>/`
3. Add an entry to `registry.json`
4. Open a PR

Or just use **`/publish-mod`** inside Claude Desktop — it automates the entire flow.

### Mod Structure

```
mods/your-mod-name/
├── plugin.json       # Required: name, description, author
├── SKILL.md          # For skills/modes: slash command definition
└── CLAUDE.md         # For styles/prompts: behavioral instructions
```

### Verified Badge

The maintainer may add the **Verified** badge to your mod after review. Verified mods are reviewed for quality and safety, and are featured more prominently in the marketplace.

---

## License

MIT

---

<p align="center">
  <img src="assets/logo.svg" width="40" alt="Claude Mods"/>
  <br/>
  <sub>Built for the Claude community</sub>
</p>
