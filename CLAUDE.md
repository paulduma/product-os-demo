# 🧠 CLAUDE.md — Mémoire globale

> Fichier lu par Claude Code au démarrage de chaque session.
> Mis à jour manuellement après chaque changement structurant.

---

## Qui je suis

Product/CEO solo. Je travaille sur des SaaS et projets persos.
Mon objectif : être décideur + validateur. Les agents font 80% de l'exécution répétitive.

## Mes outils

| Outil | Rôle |
|---|---|
| Claude Code | Features complètes, multi-fichiers, tâches autonomes |
| Claude Cowork | Specs, PRD, Notion, Linear, orchestration |
| Notion | Documentation, base de connaissance |
| Linear | Tickets, backlog, sprints |

## Stack commune à tous mes projets

- React + Vite + JavaScript
- [Ajoute : router, state manager, lib UI, auth, etc.]

## Projets actifs

<!-- À compléter -->
| Projet | Description courte | Repo | Statut |
|---|---|---|---|
| Projet A | ... | ~/projects/... | En cours |
| Projet B | ... | ~/projects/... | En cours |

## Acronymes & termes métier

<!-- À compléter avec tes vrais acronymes -->
| Terme | Signification |
|---|---|
| ... | ... |

## Personnes clés

<!-- À compléter -->
| Nom/Pseudo | Rôle |
|---|---|
| ... | ... |

## Règles de travail

- Toujours lire `CLAUDE.md` du projet avant de toucher au code
- Toujours demander confirmation avant de modifier plus de 3 fichiers
- Ne jamais supprimer de code sans confirmation explicite
- Signaler les dettes techniques rencontrées sans les corriger sauf demande

## Skills disponibles

Source : `~/product-os/skills/`. Chargés automatiquement à chaque session Claude Code lancée avec `claude --plugin-dir ~/product-os` (alias `claude-os`) — pas besoin de chemin, Claude les invoque lui-même ou sur demande : *"Utilise le skill [nom] pour [tâche]"*

### Meta
- `create-skill` — créer ou compléter un skill Claude pour ce repo
- `init-project` — checklist d'intégration d'un projet au Product OS (CLAUDE.md, Git, Linear)

### Code
- `code-review` — review d'un fichier ou d'une PR
- `test-writer` — génère les tests après une feature
- `feature-builder` — implémente une feature depuis une spec

### Product
- `write-spec` — idée vague → spec structurée
- `prd-functional` — spec → PRD fonctionnel
- `prd-technical` — PRD fonctionnel → PRD technique
- `spec-to-linear` — PRD → tickets Linear
- `benchmark` — analyse concurrentielle structurée
- `market-sizing` — estimation de marché
- `content-comm` — contenu LinkedIn / newsletter
- `prd-design` — *placeholder, à compléter*
- `documentation` — *placeholder, à compléter*

## Agents disponibles

Source : `~/product-os/agents/`. Chargés automatiquement en mode plugin (`claude-os`), disponibles nativement comme subagents.

- `weekly-review` — chaque lundi matin
- `spec-to-ticket` — idée → spec → tickets Linear
- `stakeholder-update` — tickets fermés → update partageable

## Historique des décisions importantes

<!-- À compléter au fil du temps -->
| Date | Décision | Raison |
|---|---|---|
| ... | ... | ... |
