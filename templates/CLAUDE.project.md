# CLAUDE.md — [Nom du projet]

> Mémoire technique du projet. Lu par Claude Code au démarrage de chaque session.
> Mettre à jour après chaque décision d'architecture importante.

---

## Présentation du projet

**Description :** [Ce que fait ce projet en 2 lignes]  
**Statut :** [En développement / Beta / Production]  
**URL :** [si applicable]

## Stack

- React + Vite + JavaScript
- [Router : React Router v6 / TanStack Router / ...]
- [State : Zustand / Jotai / Context / ...]
- [UI : Tailwind / shadcn / MUI / ...]
- [Auth : ...]
- [API : REST / GraphQL / tRPC / ...]
- [Backend : ...]
- [DB : ...]

## Structure du projet

```
src/
├── components/     ← Composants réutilisables
├── pages/          ← Pages / routes
├── hooks/          ← Hooks custom
├── lib/            ← Utilitaires, helpers
├── api/            ← Appels API
├── store/          ← State global (si applicable)
└── types/          ← Types partagés (si applicable)
```

## Conventions spécifiques à ce projet

[Ajoute ici ce qui est différent des conventions globales de ton Product OS]

- ...

## Domaine métier

[Explique le domaine en quelques lignes pour que Claude comprenne le contexte]

**Entités principales :**
- [Entity A] : [description]
- [Entity B] : [description]

**Flux principaux :**
1. [Flux 1]
2. [Flux 2]

## Endpoints API principaux

| Endpoint | Méthode | Description |
|---|---|---|
| `/api/...` | GET | ... |
| `/api/...` | POST | ... |

## Variables d'environnement

```
VITE_API_URL=
VITE_AUTH_URL=
# Ne jamais mettre les valeurs ici — juste les noms
```

## Décisions d'architecture

| Date | Décision | Raison |
|---|---|---|
| ... | ... | ... |

## Dette technique connue

| Zone | Description | Priorité |
|---|---|---|
| ... | ... | Faible / Moyen / Élevé |

## Ce qu'il ne faut PAS faire dans ce projet

- [Anti-pattern spécifique 1]
- [Anti-pattern spécifique 2]

## Commandes utiles

```bash
npm run dev          # Démarrer le dev server
npm run build        # Build production
npm run test         # Lancer les tests
npm run lint         # Lint
```

## Contexte global

Ce projet fait partie de mon Product OS. Pour le contexte global (outils, projets, acronymes) :  
`~/product-os/CLAUDE.md`

Les skills et agents de `~/product-os` sont chargés automatiquement dès que Claude Code est lancé avec `claude --plugin-dir ~/product-os` (alias `claude-os`) — pas besoin de chemin.
