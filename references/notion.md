# Setup Notion

Référence de portée et conventions pour toute skill lisant ou écrivant dans Notion.

La page racine Notion à utiliser est donnée par le `CLAUDE.md` global (table Outils, entrée Notion) — ne jamais la déduire ou la deviner ici.

## Portée (non négociable)

Ce n'est **pas** un accès au workspace Notion entier. C'est un arbre unique : une page parent et ses descendants.

- **Racine autorisée :** page **Product-os-Demo**
  - URL : https://app.notion.com/p/Product-os-Demo-3c33d8616dbb807eb2d3cee91810811b
  - Page ID : `3c33d861-6dbb-807e-b2d3-cee91810811b`
- **Autorisé :** cette page, et toute page dont elle est un ancêtre (enfants, petits-enfants, etc.).
- **Interdit :** toute autre page du même espace Notion — pages sœurs, autres branches, racine du workspace, recherches globales.
- Ne jamais lister, chercher, lire, éditer, déplacer ou créer hors de cet arbre.
- Toute page créée doit avoir pour parent cette racine **ou** l'un de ses descendants.
- Si un outil Notion renvoie une page hors arbre : l'ignorer, ne pas la lire ni la modifier, et le signaler.

## Accès technique

Les règles ci-dessus contraignent le comportement des skills. Pour que l'intégration / le connecteur Notion n'ait *physiquement* accès qu'à cet arbre : partager **uniquement** cette page parent avec la connexion (les pages enfants héritent). Ne pas connecter le workspace entier.

## Conventions

- Rester sous la racine Product-os-Demo ; ne pas "remonter" vers le workspace.
- Préférer lister les enfants de la racine (ou d'une page déjà dans l'arbre) plutôt qu'une recherche workspace-wide.
- Ne jamais utiliser un `parent` / `page_id` qui n'est pas la racine ou un descendant déjà vérifié.
