# Setup Linear

Référence de hiérarchie et conventions pour toute skill créant ou éditant des projects/issues dans Linear (`spec-to-linear`, `write-spec`, etc.).

Le workspace Linear précis à utiliser est donné par le `CLAUDE.local.md` du projet en cours — ne jamais le déduire ou le deviner ici.

## Contexte du workspace

- Workspace unique, partagé entre tous les projects (setup indie hacking multi-produits, pas mono-produit).
- Pas de Teams.

## Hiérarchie

- **Project** = un produit/tentative distinct (app, webapp, product-os, repo de script adhoc...). Équivaut à un repo git.
- **Milestone** = une phase d'itération à l'intérieur d'un Project (ex : landing, MVP, v0...). Regroupe un bundle de features.
- **Issue** = une feature appartenant à un Milestone.
- **Sub-issue (subtask)** = découpage d'une Issue en tâches.

## Conventions

### Milestone
- Titre libre, représente une étape du process.
- Description courte et synthétique de ce qui va être fait.
- Toujours une target date.

### Issue
- Titre préfixé par un identifiant entre parenthèses reprenant les conventions classiques : `(feat)`, `(fix)`, `(chore)`, etc.
- Label correspondant au même type que le préfixe.
- Description jamais vide. Le contenu exact (structure, niveau de détail) est défini par la skill qui rédige l'issue (`write-spec`, `spec-to-linear`), pas ici.

### Sub-issue
- Titre = phrase courte et claire décrivant l'étape/tâche.

Priorités et statuts du workflow : gérés par la skill qui crée/édite l'item, pas définis ici.
