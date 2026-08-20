# 🧠 Product OS — Démo

> 👁️ **Ceci est une version démo, à but de présentation.** Elle montre l'architecture complète de mon système de travail assisté par IA (skills, agents, docs). Seuls quelques skills représentatifs sont exposés en détail (`create-skill`, `write-spec`, `prd-technical`, `code-review`) — le reste est présent en tant qu'entrée de catalogue (nom, description, rôle) mais son contenu détaillé reste dans la version privée.

Repo central de mon système de travail assisté par IA.  
Contient mes skills, agents, templates et docs de référence.

---

## Structure

```
product-os/
├── .claude-plugin/
│   └── plugin.json      ← Manifeste du plugin ({ "name": "product-os-demo" })
├── skills/               ← Skills Claude Code natifs (code/, product/, <nom>/SKILL.md)
├── agents/               ← Subagents Claude Code natifs (déclencheur + output défini)
├── docs/                 ← Guides de décision et workflows
└── templates/            ← Fichiers à copier/compléter dans chaque nouveau projet
```

---

## Comment utiliser ce repo

### 1. Premier setup (une seule fois)

Clone le repo dans ton home :
```bash
git clone <repo-url> ~/product-os
```

Ajoute dans `.bashrc` / `.zshrc` :
```bash
alias claude-os='claude --plugin-dir ~/product-os'
```

### 2. Usage quotidien (Claude Code)

Depuis n'importe quel repo :
```bash
claude-os
```

Skills et agents sont chargés automatiquement à l'ouverture de session — pas de sync, pas de symlink, pas de packaging. Le dossier `product-os/` est lu tel quel à chaque lancement : toute modif prend effet immédiatement à la session suivante.

```
Décris juste la tâche → Claude choisit le bon skill
```
```
Utilise le skill [nom] pour [tâche]
Utilise l'agent [nom]
```

Skills et agents disponibles : voir [`CLAUDE.md`](CLAUDE.md) (section "Skills disponibles" / "Agents disponibles").

### 3. Usage depuis Claude Chat (web / onglet Chat du Desktop)

```bash
claude plugin package product-os/
```
→ génère un fichier plugin installable. Dans Claude Chat : **"+" → Plugins → uploader le fichier**.

Limites : ça fonctionne pour les skills, pas les agents (Code/Cowork uniquement). Pas de sync live — à chaque évolution de `product-os/`, il faut re-packager et re-uploader.

---

## Flow produit standard

```
Idée
 └→ [skill] write-spec          → spec structurée
 └→ [skill] prd-functional      → PRD fonctionnel
 └→ [skill] prd-technical       → PRD technique (prêt à coder)
 └→ [skill] spec-to-linear      → tickets Linear créés
 └→ [agent] feature-builder     → Claude Code implémente
 └→ [skill] code-review         → review avant merge
```

---

## Ajouter un skill

Copie `templates/new-skill.md` dans `skills/code/<nom-du-skill>/SKILL.md` ou `skills/product/<nom-du-skill>/SKILL.md`, remplis les sections (dont le frontmatter `name`/`description`). Rien d'autre à faire — en mode plugin, le nouveau skill est disponible dès la session `claude-os` suivante.

---

## Statut des skills

🟢 écrit = instructions/format/règles complets, prêt à l'emploi. 🟡 draft = squelette, à rédiger. 👁️ vitrine = contenu détaillé exposé dans cette démo. 🔒 masqué = entrée de catalogue seulement, contenu détaillé dans la version privée.

| Skill | Catégorie | Statut | Démo |
|---|---|---|---|
| [`create-skill`](skills/create-skill/SKILL.md) | Meta | 🟢 écrit | 👁️ vitrine |
| [`init-project`](skills/init-project/SKILL.md) | Meta | 🟢 écrit | 🔒 masqué |
| [`code-review`](skills/code/code-review/SKILL.md) | Code | 🟢 écrit | 👁️ vitrine |
| [`feature-builder`](skills/code/feature-builder/SKILL.md) | Code | 🟢 écrit | 🔒 masqué |
| [`test-writer`](skills/code/test-writer/SKILL.md) | Code | 🟢 écrit | 🔒 masqué |
| [`write-spec`](skills/product/write-spec/SKILL.md) | Product | 🟢 écrit | 👁️ vitrine |
| [`prd-functional`](skills/product/prd-functional/SKILL.md) | Product | 🟢 écrit | 🔒 masqué |
| [`prd-technical`](skills/product/prd-technical/SKILL.md) | Product | 🟢 écrit | 👁️ vitrine |
| [`spec-to-linear`](skills/product/spec-to-linear/SKILL.md) | Product | 🟢 écrit | 🔒 masqué |
| [`benchmark`](skills/product/benchmark/SKILL.md) | Product | 🟢 écrit | 🔒 masqué |
| [`market-sizing`](skills/product/market-sizing/SKILL.md) | Product | 🟢 écrit | 🔒 masqué |
| [`content-comm`](skills/product/content-comm/SKILL.md) | Product | 🟢 écrit | 🔒 masqué |
| [`prd-design`](skills/product/prd-design/SKILL.md) | Product | 🟡 draft | ➖ n/a |
| [`documentation`](skills/product/documentation/SKILL.md) | Product | 🟡 draft | ➖ n/a |
| [`experience-interviewer`](skills/pro/skills_itw/experience-interviewer/SKILL.md) | Pro | 🟢 écrit | 🔒 masqué |
