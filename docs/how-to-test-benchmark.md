# How To — Tester le skill `benchmark`

> Une page de test par skill. À fusionner plus tard ou à garder séparées — à décider après les autres skills.

Le test réel se fait dans **Claude Code** (`claude-os`), pas dans Cursor : sans connecteur Notion, la skill s’arrête au markdown.

---

## Prérequis

- Relancer une **nouvelle** session Claude Code après toute modif du skill (relu au lancement).
- Pointer le plugin vers **ce** repo :

```bash
claude --plugin-dir /Users/Paul/Desktop/product-os-demo
```

- Vérifier que `benchmark` apparaît : `/` ou `/help`.
- Connecter Notion à Claude Code (MCP / connecteur), en partageant **uniquement** la page [Product-os-Demo](https://app.notion.com/p/Product-os-Demo-3c33d8616dbb807eb2d3cee91810811b) (les enfants héritent).
- Optionnel : `cp CLAUDE.local.example CLAUDE.local.md` et remplir Linear/Notion. Sinon la skill lit `CLAUDE.md`.

---

## Test A — parent par défaut `benchmark`

```
Utilise le skill benchmark pour comparer Linear à Jira et Asana, périmètre : gestion de tickets pour un solo founder
```

**OK si :**
- une page **`benchmark`** existe (ou a été créée) sous Product-os-Demo
- une page **`Benchmark — …`** est née **dessous**
- tu reçois l’URL, pas seulement le markdown

## Test B — page donnée dans les instructions

Créer (ou nommer) une page enfant, ex. `benchmark-test`, puis :

```
Utilise le skill benchmark pour le même sujet, publie sous la page benchmark-test
```

**OK si** la nouvelle page est sous `benchmark-test`, pas sous `benchmark`.

## Test C — page introuvable

```
Utilise le skill benchmark pour le même sujet, publie sous la page cette-page-nexiste-pas
```

**OK si** ça retombe sur `benchmark` (la page donnée n’existe pas).

---

## Ce qui doit échouer

- Publier à la racine du workspace Notion, ou hors de Product-os-Demo → la skill refuse.
- Notion non branché → elle le **dit** et livre le markdown, sans inventer d’URL.
