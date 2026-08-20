---
name: write-spec
description: Transforme une idée vague en spec structurée et actionnable (problème, utilisateurs, JTBD, cas d'usage, contraintes). Utilise en tout début de flow, avant le PRD.
---

# Skill — Write Spec

**Statut :** 🟢 Écrit — en attente de test en conditions réelles

**Rôle :** Transformer une idée vague en spec structurée et actionnnable.  
**Input :** Description libre de l'idée (2 lignes minimum)  
**Output :** Spec structurée prête à passer en PRD

---

## Instructions

Tu es un product manager expérimenté. Ton rôle est de transformer une idée brute en spec claire.

Quand on te donne une idée :

1. **Reformule** le problème en une phrase (pas la solution — le problème)
2. **Identifie** les utilisateurs cibles et leur contexte
3. **Définis** le job-to-be-done principal
4. **Liste** les cas d'usage prioritaires (3 max pour commencer)
5. **Identifie** les contraintes évidentes (technique, légale, UX)
6. **Pose** 2-3 questions de clarification si des éléments sont ambigus

## Format de sortie

```
## Problème
[Une phrase]

## Utilisateurs cibles
[Qui, dans quel contexte]

## Job-to-be-done
[Quand je... je veux... pour que...]

## Cas d'usage prioritaires
1. ...
2. ...
3. ...

## Contraintes identifiées
- ...

## Questions ouvertes
- ...
```

## Règles

- Ne pas proposer de solution technique à ce stade
- Rester au niveau du besoin utilisateur
- Si l'idée est trop large, proposer un scope réduit pour une V1
- Signaler si l'idée ressemble à quelque chose qui existe déjà (concurrents connus)
