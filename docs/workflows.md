# Workflows — Boucles de travail

## Boucle matin (5 min)

```
Ouvrir Claude Cowork
→ "start"
→ Lire le brief du jour (tâches prioritaires + contexte)
→ Identifier les 3 priorités
→ C'est parti
```

## Boucle feature complète

```
1. Idée
   └→ Cowork : "Utilise l'agent spec-to-ticket — voici l'idée : [...]"

2. Spec validée
   └→ Cowork génère PRD fonctionnel → PRD technique → tickets Linear

3. Implémentation
   └→ Terminal : "claude" à la racine du projet
   └→ "Lis CLAUDE.md. Utilise le skill feature-builder
       pour implémenter [ticket Linear]"
   └→ Claude Code travaille en autonomie

4. Finitions
   └→ Claude Code pour les retouches UI / ajustements visuels

5. Review
   └→ Claude Code : "Utilise le skill code-review sur les fichiers modifiés"

6. Tests
   └→ Claude Code : "Utilise le skill test-writer"

7. Clôture
   └→ Cowork : "Mets à jour les tickets Linear et note les décisions dans Notion"
```

## Boucle soir (5 min)

```
Cowork :
"Mets à jour Linear avec ce qui a été fait aujourd'hui.
 Note les décisions importantes dans Notion.
 Prépare le contexte pour demain."
```

## Boucle weekly (lundi matin, 10 min)

```
Cowork : "Utilise l'agent weekly-review"
→ Lire le rapport
→ Valider les 3 priorités de la semaine
→ Ajuster le backlog si besoin
```

## Boucle nouveau projet

```
1. Créer le repo
2. `claude-os` à la racine du projet : "Utilise le skill init-project"
   → checklist Git + Linear, CLAUDE.md créé si absent
3. Compléter CLAUDE.md (signalé par le skill si vide)
4. "Lis CLAUDE.md. On commence."
```

## Boucle content (LinkedIn / Newsletter)

```
Cowork :
"Utilise le skill content-comm
 Sujet : [sujet]
 Canal : [LinkedIn / newsletter / les deux]
 Contexte : [ce qui s'est passé / ce qu'on veut partager]"
→ Itérer sur le draft
→ Copier / publier
```
