---
name: init-project
description: Initialise ou remet aux normes un projet avec le Product OS — crée CLAUDE.md depuis le template, vérifie la config Git et Linear. Utilise en créant un nouveau repo, en reprenant un projet existant, ou quand on demande d'"initialiser"/"setup" un projet avec le Product OS.
---

# Skill — Init Project

**Statut :** 🟢 Écrit — en attente de test en conditions réelles

**Rôle :** Faire passer un projet (nouveau ou existant) par la checklist complète d'intégration au Product OS.
**Input :** Chemin du projet (défaut : dossier courant)
**Output :** Rapport de checklist (✅/⚠️/❌) + actions correctives appliquées ou proposées

---

## Instructions

Tu es responsable de l'intégration d'un projet au Product OS. Ton rôle est de vérifier chaque brique, corriger ce qui peut l'être sans risque, et proposer le reste.

Ce skill est **idempotent** : on doit pouvoir le relancer sur un projet déjà à jour sans rien casser.

Skills et agents n'ont rien à faire ici : en mode plugin (`claude --plugin-dir ~/product-os`, alias `claude-os`), ils sont déjà chargés automatiquement dans toute session Claude Code — si ce skill s'exécute, ils le sont forcément aussi.

### Étape 1 — CLAUDE.md du projet

1. Détermine le chemin du projet cible (dossier courant si non précisé)
2. Si `CLAUDE.md` n'existe pas déjà à la racine du projet, lis `${CLAUDE_PLUGIN_ROOT}/templates/CLAUDE.project.md` et écris-le tel quel comme `CLAUDE.md` du projet
3. Si `CLAUDE.md` existe déjà, ne le touche pas — ne jamais écraser un fichier existant
4. Si `CLAUDE.md` vient d'être créé depuis son template, signale-le clairement — il est encore à compléter, ne le laisse pas en `[placeholder]` sans le mentionner

### Étape 2 — Rules Cursor (si le projet utilise Cursor)

1. Demande à l'utilisateur si ce projet est aussi utilisé avec Cursor (un dossier `.cursor/` déjà présent est un signal, mais demande confirmation si ambigu)
2. Si oui :
   - Repère dans `${CLAUDE_PLUGIN_ROOT}/skills/` tous les `SKILL.md` avec `mode: reference` en frontmatter — seuls ceux-là sont transposables (guidance/structure statique, pas d'exécution d'actions que Cursor ne peut pas reproduire)
   - Pour chacun, crée `.cursor/rules/<nom-du-skill>.mdc` dans le projet cible avec le corps du skill (après le frontmatter), précédé d'un en-tête minimal :
     ```
     ---
     description: <description du skill>
     alwaysApply: false
     ---
     ```
   - Ne jamais écraser un `.mdc` déjà présent — signaler s'il existe et semble désynchronisé du skill source
3. Si non, ne rien créer

### Étape 3 — Config Git

Vérifie et corrige (avec confirmation avant toute action visible à l'extérieur) :

- [ ] Le dossier est un repo Git (`git rev-parse --is-inside-work-tree`) → sinon propose `git init`
- [ ] Un remote existe (`git remote -v`) → sinon demande si un repo GitHub doit être créé (ne jamais en créer un sans confirmation explicite)
- [ ] `.gitignore` couvre au minimum `node_modules`, `.env*`, `dist`/`build`, `.DS_Store` → sinon propose de compléter (ne pas écraser un `.gitignore` existant, juste ajouter les lignes manquantes)
- [ ] Il y a au moins un commit initial → sinon signale-le, ne commit jamais sans que l'utilisateur le demande explicitement

### Étape 4 — Config Linear

- Cherche si un projet Linear correspondant existe déjà (`list_projects` / `list_teams`)
- Si aucun ne correspond, demande à l'utilisateur s'il veut en créer un — **ne jamais créer une resource Linear sans confirmation explicite**, c'est visible par toute l'équipe
- Si un projet existe, note son nom/ID pour que `spec-to-linear` et les agents puissent le retrouver plus tard (proposer de le noter dans `CLAUDE.md` du projet)

### Étape 5 — Mémoire globale

Propose (n'applique pas sans validation) la ligne à ajouter dans la table "Projets actifs" de `~/product-os/CLAUDE.md` :
```
| <Nom du projet> | <description courte> | <chemin> | En cours |
```

## Format de sortie

```
📋 Init Project — <nom du projet>

CLAUDE.md projet             ⚠️ créé depuis template — à compléter
Rules Cursor                 ✅ 3 skills `mode: reference` copiés dans .cursor/rules/
Git                          ✅ repo + remote OK
.gitignore                   ❌ manque .env* — proposé, en attente de validation
Linear                       ⚠️ aucun projet trouvé — veux-tu que j'en crée un ?

Prochaines actions :
1. Compléter CLAUDE.md avec le contexte du projet
2. Valider la création du projet Linear (oui/non)
```

## Règles

- Jamais d'action irréversible ou visible de l'extérieur (git init sur un dossier existant avec historique, création de repo GitHub, création de projet Linear/Notion) sans confirmation explicite de l'utilisateur
- Ne jamais écraser `CLAUDE.md`, un `.gitignore` ou un `.mdc` Cursor existant — uniquement compléter ce qui manque
- Ne copier vers `.cursor/rules/` que les skills marqués `mode: reference` — les autres reposent sur l'exécution d'actions (tools) que Cursor ne peut pas reproduire
- Si `${CLAUDE_PLUGIN_ROOT}/templates/CLAUDE.project.md` est introuvable, arrête-toi et signale-le au lieu de deviner un contenu
- Rester concis dans le rapport final — une ligne par item de checklist

## Exemples

### Input
« Utilise le skill init-project, je viens de créer un nouveau repo pour mon side project "focusflow" dans ~/projects/focusflow »

### Output attendu
Le rapport de checklist ci-dessus, avec les items Git/Linear vérifiés pour ce chemin précis, et les actions correctives proposées (pas appliquées) pour tout ce qui touche à Git remote / Linear / GitHub.
