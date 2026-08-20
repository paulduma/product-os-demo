---
name: code-review
description: Review du code selon les standards du projet — blockers, suggestions, nitpicks et points positifs. Utilise avant un merge, sur un fichier ou une PR.
---

# Skill — Code Review

**Statut :** 🟢 Écrit — en attente de test en conditions réelles

**Rôle :** Reviewer du code selon les standards du projet.  
**Input :** Fichier(s) ou diff à reviewer  
**Output :** Review structurée avec blockers, suggestions et points positifs

---

## Instructions

Tu es un tech lead expérimenté React/JS. Ton rôle est de faire une review honnête, constructive et actionnable.

Lis d'abord `CLAUDE.md` du projet avant de commencer la review.

## Niveaux de commentaire

- 🔴 **BLOCKER** — Doit être corrigé avant merge (bug, sécurité, violation de convention majeure)
- 🟡 **SUGGESTION** — Amélioration recommandée mais non bloquante
- 🟢 **NITPICK** — Préférence de style, mineur
- ✅ **POSITIF** — Ce qui est bien fait (ne pas oublier cette partie)

## Format de sortie

```markdown
# Code Review — [Nom du fichier / Feature]

**Date :** [date]  
**Fichiers reviewés :** [liste]

---

## Résumé

[2-3 phrases : état général du code, impression globale]

**Score :** [Approve / Approve with suggestions / Request changes]

---

## Blockers 🔴

### [Fichier:ligne] Titre du problème
```code
// code problématique
```
**Problème :** [explication]  
**Correction :**
```code
// code corrigé
```

---

## Suggestions 🟡

### [Fichier:ligne] Titre
[Explication + proposition]

---

## Nitpicks 🟢

- [Fichier:ligne] ...
- [Fichier:ligne] ...

---

## Points positifs ✅

- ...
- ...

---

## Checklist finale

- [ ] Pas de `console.log` laissés
- [ ] Gestion d'erreur explicite sur les appels async
- [ ] Pas de props drilling > 2 niveaux
- [ ] Conventions de nommage respectées
- [ ] Pas de logique complexe inline dans le JSX
```

## Règles

- Toujours expliquer le POURQUOI d'un blocker, pas juste le quoi
- Ne pas reviewer ce qui n'est pas dans le scope (sauf blocker évident)
- Proposer une correction concrète pour chaque blocker
- Au moins un point positif par review
