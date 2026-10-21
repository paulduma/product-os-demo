# 🧠 Product OS — Demo

> 👁️ **[WIP] This is a demo version, meant for presentation.** It shows the architecture of an AI operating system that I created for a personal usage, to which I have extended it to a professional usage. 
It contains a set of skills, workflows and documentation that is meant to be used for projects you're working on, alone or with your teams.
Only 4 representative skills are displayed in detail in that repo (`create-skill`, `write-spec`, `benchmark`, `init-project`); the rest (other skills, agents) lives in the private version and does not appear here.

---

## Structure

This product-os has the following architecture
```
product-os/
├── .claude-plugin/
│   └── plugin.json      ← Plugin manifest ({ "name": "product-os-demo" })
├── skills/               ← Native Claude Code skills (<name>/SKILL.md) — 4 showcase skills in this demo
├── agents/               ← Empty in this demo — agents stay in the private version
├── docs/                 ← Decision guides, documentation on your context
└── templates/            ← Files to copy/fill in for each new project
```
---

## How to use this repo

For Product Managers working on prototypes but not pushing real code in production, I sugested cloning this repository locally with the following organization
```
root-folder/             ← e.g Desktop/Projects
├── product-os/          ← clone this repo here
├── codebase/            ← the company full repositories, cloned and indexed here for context
└── new_project/         ← the current project or prototype they're working on
```
They can then open a claude session from their new project folder, with a set up to read the product-os and codebase and use it for the skills and context. Here's how to set it up that way below

### 1. First-time setup (once only)

Clone the repo into your home directory (adjust the path if you put it somewhere else — the alias below must point to the same place):
```bash
git clone <repo-url> ~/product-os
```

Find your shell:
```bash
echo $SHELL
```
- `/bin/zsh` (default on recent macOS) → file to edit: `~/.zshrc`
- `/bin/bash` → file to edit: `~/.bashrc` (or `~/.bash_profile`)

Add the alias at the end of the file:
```bash
echo "alias claude-os='claude --plugin-dir ~/product-os'" >> ~/.zshrc
```
(replace `~/product-os` with the real path if the repo lives elsewhere)

Reload the shell so the alias is recognized (or open a new terminal):
```bash
source ~/.zshrc
```

Check that the alias is defined:
```bash
alias claude-os
# → claude-os='claude --plugin-dir ~/product-os'
```

Check that skills load: run `claude-os` from any folder, then type `/` in the prompt — the repo's skills should appear in the menu (namespaced as `product-os:<name>` if they collide with a native Claude Code skill). `/help` also lists everything that is loaded. `/plugin` opens the plugin manager if you need to debug a load that fails.

### 2. Daily use (Claude Code)

From any repo:
```bash
claude-os
```

Skills and agents load automatically when the session opens — no sync, no symlink, no packaging. The `product-os/` folder is read as-is on every launch: any change takes effect immediately in the next session.

```
Just describe the task → Claude picks the right skill
```
```
Use the skill [name] for [task]
Use the agent [name]
```

Available skills and agents: see [`CLAUDE.md`](CLAUDE.md) ("Available skills" / "Available agents" sections).

### 3. Use from Claude Chat (web / Desktop Chat tab)

```bash
claude plugin package product-os/
```
→ produces an installable plugin file. In Claude Chat: **"+" → Plugins → upload the file**.

Limits: this works for skills, not agents (Code/Cowork only). No live sync — each time `product-os/` changes, you need to re-package and re-upload.

---

## Standard product flow

```
Idea
 └→ [skill] write-spec          → structured spec                        (demo)
 └→ [skill] prd-functional      → functional PRD                         (full version)
 └→ [skill] prd-technical       → technical PRD (ready to code)          (full version)
 └→ [skill] spec-to-linear      → Linear tickets created                 (full version)
 └→ [agent] feature-builder     → Claude Code implements                 (full version)
 └→ [skill] code-review         → review before merge                    (full version)
```

Upstream of the flow, independently: `[skill] benchmark` → structured competitive analysis *(demo)*.

---

## Adding a skill

Copy `templates/new-skill.md` into `skills/<skill-name>/SKILL.md`, then fill in the sections (including the `name`/`description` frontmatter). Nothing else to do — in plugin mode, the new skill is available from the next `claude-os` session.

---

## Skill status

🟢 Ready = instructions, format, and rules are complete and ready to use. The other skills in the full system (Meta, Code, Product, Pro) live in the private version and do not appear in this demo.

| Skill | Category | Status |
|---|---|---|
| [`create-skill`](skills/create-skill/SKILL.md) | Meta | 🟢 Ready |
| [`init-project`](skills/init-project/SKILL.md) | Meta | 🟢 Ready |
| [`write-spec`](skills/write-spec/SKILL.md) | Product | 🟢 Ready |
| [`benchmark`](skills/benchmark/SKILL.md) | Product | 🟢 Ready |
