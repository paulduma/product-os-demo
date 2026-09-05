---
name: build
description: Résout une cible Linear (Milestone ou Issue) en liste d'unités à implémenter, applique l'idempotence (ignore ce qui est déjà en In Review), et lit chaque unité au format write-spec comme source de vérité. C'est le brief chargé par l'agent `build` avant toute exécution — pas de git, pas de gate qualité, pas de sync Linear ici.
---

# Skill — Build

**Statut :** 🟢 Ready — en attente de test en conditions réelles

**Rôle :** Transformer un lien Linear (Milestone ou Issue) en liste d'unités de travail concrètes à implémenter, en excluant ce qui est déjà traité ou hors périmètre.
**Input :** Un lien Linear (URL Milestone ou URL Issue)
**Output :** Liste ordonnée des unités à traiter, chacune avec son contenu structuré (Contexte / Comportement attendu / Hors scope / Done quand / Pistes d'implémentation)

---

## Instructions

Tu prépares le terrain pour l'agent `build`, qui va ensuite implémenter chaque unité. Ton job ici s'arrête à la résolution de la liste et à la lecture des tickets — pas à l'exécution.

### Étape 1 — Détecter le mode

Un seul lien Linear en entrée. Résous-le avec les tools Linear (`get_milestone` / `get_issue`) pour déterminer sa nature — ne devine jamais à partir de la forme de l'URL ou de l'ID.

- **Lien = Milestone** → **mode Milestone**. Les unités à traiter = toutes les issues de ce milestone dont le statut n'est ni `Done` ni `Cancelled`.
- **Lien = Issue** → **mode Issue**. Si cette issue a des sub-issues, les unités = ces sub-issues. Si elle n'en a pas, l'unité unique = l'issue elle-même.

### Étape 2 — Appliquer l'idempotence

Un run peut être relancé plusieurs fois sur le même milestone (ex : après une review partielle). Avant de figer la liste des unités à traiter :

- Vérifie le statut actuel de chaque unité candidate.
- Une unité déjà passée en **In Review** par un run précédent n'est **pas** retraitée — elle sort de la liste, sans être comptée comme un échec ou un blocage.
- Une unité déjà `Done` ou `Cancelled` est exclue (cf. étape 1, mode Milestone).
- Ne restent dans la liste finale que les unités dans un état "à faire" (`Todo` / `Planned` / autre unstarted du workspace — voir `${CLAUDE_PLUGIN_ROOT}/references/linear.md` pour les conventions de statut).

Ce mécanisme est ce qui permet de relancer l'agent sur un même milestone sans dupliquer du travail déjà envoyé en review.

### Étape 3 — Lire chaque unité comme source de vérité

Chaque unité retenue (issue ou sub-issue) est un ticket produit par `write-spec` : lis-le tel quel, ne le résume pas et ne le réinterprète pas. C'est lui qui fait autorité sur ce qu'il faut construire, pas la mémoire de la conversation ni le titre seul.

Le format attendu, section par section :

- **Contexte** — pourquoi ce ticket existe
- **Comportement attendu** — ce que le système doit faire
- **Hors scope** — ce qu'il ne faut explicitement pas faire
- **Done quand** — la checklist qui définit "terminé"
- **Pistes d'implémentation** — fichiers, contraintes, pièges connus

Si un ticket retenu n'a pas ce format (description vide, sections manquantes, contenu qui ressemble à une idée brute non specée) : signale-le plutôt que d'improviser un scope à sa place. Ne construis jamais sur un ticket dont le contenu est ambigu.

### Hors scope de ce skill

Ce skill ne fait que résoudre la liste et lire les tickets. Il ne couvre pas :

- La résolution fine de repo/projet cible et l'exclusion technique des unités (voir le skill/agent de résolution de cible)
- L'exécution réelle : git (branches, commits, PR)
- Le gate qualité (tests, lint)
- La synchronisation Linear (changements de statut, commentaires)

Ces étapes vivent dans l'agent `build` et les autres pièces du milestone "Agent build".

---

## Format de sortie

```markdown
## Cible

**Lien reçu :** [URL]
**Type détecté :** Milestone | Issue
**Mode :** Milestone | Issue

## Unités à traiter

| # | Unité | Statut actuel | Action |
|---|---|---|---|
| 1 | (feat) … — TES-XX | Todo | À traiter |
| 2 | (feat) … — TES-YY | In Review | Ignorée (déjà traitée par un run précédent) |
| 3 | (fix) … — TES-ZZ | Cancelled | Exclue |

## Unité 1 — [Titre] ([ID])

### Contexte
[repris du ticket]

### Comportement attendu
[repris du ticket]

### Hors scope
[repris du ticket]

### Done quand
[repris du ticket]

### Pistes d'implémentation
[repris du ticket]
```

Répète le bloc "Unité N" pour chaque unité à traiter (celles marquées "À traiter" seulement).

---

## Règles

- Ne jamais deviner le mode (Milestone vs Issue) — toujours résoudre le lien via les tools Linear avant de décider
- Ne jamais retraiter une unité déjà en `In Review` : c'est le contrat d'idempotence, il protège des runs relancés
- Ne jamais halluciner ou résumer le contenu d'un ticket — le lire depuis Linear tel quel, section par section
- Un ticket qui n'a pas le format write-spec (Contexte / Comportement attendu / Hors scope / Done quand / Pistes d'implémentation) est signalé, pas complété à la place de l'auteur
- Ce skill s'arrête à la liste des unités et à leur lecture — pas de git, pas de tests/lint, pas de changement de statut Linear ici
- Si Linear est indisponible : le dire, ne pas inventer d'unités ni de contenu de ticket
