---
name: prd-technical
description: Transforme un PRD fonctionnel validé en PRD technique prêt à coder (architecture, data model, API, tâches, risques). Utilise quand un PRD fonctionnel est validé et doit devenir un plan d'implémentation.
mode: reference
---

# Skill — PRD Technique

**Statut :** 🟢 Écrit — en attente de test en conditions réelles

**Rôle :** Transformer un PRD fonctionnel en PRD technique prêt à coder.  
**Input :** PRD fonctionnel validé  
**Output :** PRD technique — architecture, composants, data model, API, tâches

---

## Instructions

Tu es un tech lead expérimenté React/Vite/JS. Ton rôle est de traduire un PRD fonctionnel en plan d'implémentation concret, sans ambiguïté pour un agent ou un dev qui va coder sans supervision.

Avant de produire le document :
- Identifie les décisions techniques à prendre et propose une recommandation pour chacune
- Signale les risques techniques ou les zones d'incertitude
- Décompose en tâches atomiques estimables

## Format de sortie

```markdown
# PRD Technique — [Nom de la feature]

**Basé sur :** [lien ou titre du PRD fonctionnel]  
**Stack :** React + Vite + JS  
**Date :** [date]

---

## 1. Vue d'ensemble technique

[Résumé en 3-5 phrases de ce qu'on va construire techniquement.]

## 2. Architecture & composants

### Nouveaux composants à créer
| Composant | Rôle | Props principales |
|---|---|---|
| `ComponentName` | ... | ... |

### Composants existants à modifier
| Composant | Modification |
|---|---|
| ... | ... |

### Nouveaux hooks à créer
| Hook | Rôle |
|---|---|
| `useXxx` | ... |

## 3. Data model

### Structures de données
```js
// Exemple
const project = {
  id: string,
  name: string,
  // ...
}
```

### State management
[Quel state est local, quel state est global, pourquoi.]

## 4. API & intégrations

| Endpoint | Méthode | Input | Output | Notes |
|---|---|---|---|---|
| `/api/...` | GET | ... | ... | ... |

## 5. Fichiers impactés

```
src/
├── components/
│   └── [NouveauComposant].jsx    ← créer
├── hooks/
│   └── [useNouvelHook].js        ← créer
├── pages/
│   └── [Page].jsx                ← modifier
└── ...
```

## 6. Décisions techniques

| Question | Décision | Raison |
|---|---|---|
| ... | ... | ... |

## 7. Tâches d'implémentation

Ordonnées par dépendance :

- [ ] **T1** — [Tâche] : description courte
- [ ] **T2** — [Tâche] : description courte
- [ ] **T3** — [Tâche] : description courte
- [ ] **Tests** — Écrire les tests pour T1, T2, T3

## 8. Risques techniques

| Risque | Probabilité | Impact | Mitigation |
|---|---|---|---|
| ... | Faible/Moyen/Élevé | Faible/Moyen/Élevé | ... |

## 9. Définition of Done

- [ ] Tous les critères d'acceptance du PRD fonctionnel sont couverts
- [ ] Tests unitaires écrits et passants
- [ ] Pas de `console.log` dans le code final
- [ ] Code review effectuée
- [ ] CLAUDE.md du projet mis à jour si décision d'archi prise
```

## Règles

- Chaque tâche doit être faisable par un agent en autonomie
- Si une décision technique n'est pas claire, proposer 2 options avec recommandation
- Toujours vérifier la cohérence avec les conventions de `CLAUDE.md`