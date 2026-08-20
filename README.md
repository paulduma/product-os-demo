# 🧠 Product OS — Démo

> 👁️ **Ceci est une version démo, à but de présentation.** Elle montre l'architecture de mon système de travail assisté par IA (skills, docs). Seuls 4 skills représentatifs sont exposés en détail (`create-skill`, `write-spec`, `benchmark`, `init-project`) — le reste (autres skills, agents) vit dans la version privée et n'apparaît pas ici.

Repo central de mon système de travail assisté par IA.  
Contient mes skills, agents, templates et docs de référence.

---

## Structure

```
product-os/
├── .claude-plugin/
│   └── plugin.json      ← Manifeste du plugin ({ "name": "product-os-demo" })
├── skills/               ← Skills Claude Code natifs (<nom>/SKILL.md) — 4 skills vitrine dans cette démo
├── agents/               ← Vide dans cette démo — les agents restent dans la version privée
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
 └→ [skill] write-spec          → spec structurée                     (démo)
 └→ [skill] prd-functional      → PRD fonctionnel                     (version complète)
 └→ [skill] prd-technical       → PRD technique (prêt à coder)        (version complète)
 └→ [skill] spec-to-linear      → tickets Linear créés                (version complète)
 └→ [agent] feature-builder     → Claude Code implémente              (version complète)
 └→ [skill] code-review         → review avant merge                  (version complète)
```

En amont du flow, indépendamment : `[skill] benchmark` → analyse concurrentielle structurée *(démo)*.

---

## Ajouter un skill

Copie `templates/new-skill.md` dans `skills/<nom-du-skill>/SKILL.md`, remplis les sections (dont le frontmatter `name`/`description`). Rien d'autre à faire — en mode plugin, le nouveau skill est disponible dès la session `claude-os` suivante.

---

## Statut des skills

🟢 écrit = instructions/format/règles complets, prêt à l'emploi. Les autres skills du système complet (Meta, Code, Product, Pro) vivent dans la version privée et n'apparaissent pas dans cette démo.

| Skill | Catégorie | Statut |
|---|---|---|
| [`create-skill`](skills/create-skill/SKILL.md) | Meta | 🟢 écrit |
| [`init-project`](skills/init-project/SKILL.md) | Meta | 🟢 écrit |
| [`write-spec`](skills/write-spec/SKILL.md) | Product | 🟢 écrit |
| [`benchmark`](skills/benchmark/SKILL.md) | Product | 🟢 écrit |
