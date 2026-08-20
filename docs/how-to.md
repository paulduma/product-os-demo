# How To — Utiliser le Product OS au quotidien

> Référence rapide. À relire si tu as un doute sur le setup, pas besoin de redemander.

---

## Le modèle mental

Deux catégories de fichiers, deux comportements différents :

| | Skills & agents Claude Code | `CLAUDE.md` |
|---|---|---|
| **Nature** | Façon de travailler (revoir du code, rédiger, planifier...) — indépendante du projet | Spécifique à chaque projet (contexte, conventions, décisions) |
| **Où ils vivent** | `~/product-os/skills/`, `~/product-os/agents/` — lus directement, jamais copiés ailleurs | dans chaque projet |
| **Comment ils arrivent là** | Chargés à chaque lancement via `claude --plugin-dir ~/product-os` (alias `claude-os`) | **copié depuis un template une seule fois** par le skill `init-project` (jamais écrasé ensuite) |
| **Portée** | Globale — dispo dans n'importe quel repo tant que tu lances `claude-os` | Un jeu de valeurs différent par projet |
| **Mise à jour** | Immédiate : le dossier est relu à chaque session, pas de cache à invalider | Modifie-le **directement dans le projet** — `product-os` ne contient que le template initial |
| **Nouveau fichier ajouté** | Rien à faire — dispo dès la session `claude-os` suivante | Créé automatiquement au premier `init-project` sur un nouveau projet |

En clair : **skills/agents = ta façon de travailler, lue en direct depuis `~/product-os`, dispo partout dès que tu lances `claude-os`. `CLAUDE.md` = propre à chaque projet, à remplir et modifier localement.**

---

## Setup one-shot (déjà fait)

- Repo dans `~/product-os` (Git fonctionnel, remote GitHub perso)
- Alias dans `.zshrc` : `alias claude-os='claude --plugin-dir ~/product-os'`

Si un jour tu bosses sur une autre machine : cloner `product-os` dans `~/product-os` sur cette machine, ajouter le même alias dans son `.zshrc`/`.bashrc`. Ça ne se propage pas tout seul entre machines.

---

## Quand tu ajoutes ou modifies un skill/agent dans `~/product-os`

Rien à faire — pas de sync, pas de symlink. Le dossier est lu tel quel à chaque lancement de `claude-os`, donc la modif est visible dès la prochaine session.

---

## Quand tu démarres ou reprends un projet

Dans une session `claude-os`, à la racine du projet :
```
Utilise le skill init-project
```
Ça crée `CLAUDE.md` depuis le template (sans écraser ce qui existe déjà), vérifie Git et Linear, et te donne un rapport ✅/⚠️/❌ avec ce qu'il reste à compléter.

---

## Usage quotidien

Dans n'importe quel projet, lancé avec `claude-os`, Claude Code découvre skills et agents tout seul. Deux façons de les invoquer :

```
Décris juste la tâche → Claude choisit le bon skill
```
```
Utilise le skill [nom] pour [tâche]
Utilise l'agent [nom]
```

Skills et agents disponibles : voir `~/product-os/CLAUDE.md` (section "Skills disponibles" / "Agents disponibles").

---

## Usage depuis Claude Chat (web)

Pas de `--plugin-dir` côté Chat. Il faut packager et uploader :
```bash
claude plugin package ~/product-os
```
Puis dans Claude Chat : **"+" → Plugins → uploader le fichier**. Fonctionne pour les skills, pas pour les agents. Pas de sync live — re-packager et re-uploader à chaque évolution du repo.

---

## Si quelque chose ne marche pas

- **Un skill n'apparaît pas** → vérifie que la session a bien été lancée avec `claude-os` (donc `--plugin-dir ~/product-os`) et pas juste `claude`
- **`~/product-os` a été déplacé/renommé** → mets à jour l'alias `claude-os` dans `.zshrc`/`.bashrc` avec le nouveau chemin
- **`CLAUDE.md` d'un projet est resté en placeholder** → normal, `init-project` ne l'écrase jamais une fois créé, il faut le compléter à la main
