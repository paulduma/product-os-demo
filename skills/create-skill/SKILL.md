---
name: create-skill
description: Crée ou complète un skill Claude réutilisable pour ce repo (Code ou Product). Utilise quand on te demande de créer, capturer ou compléter un nouveau skill/SKILL.md.
---

# Skill — Create Skill

**Statut :** 🟢 Écrit — en attente de test en conditions réelles

**Rôle :** Créer ou compléter un skill Claude réutilisable pour ce repo (Code + Cowork).  
**Input :** Description du workflow à capturer (idée libre, brouillon, ou skill incomplet)  
**Output :** Dossier `<nom-du-skill>/SKILL.md` prêt à placer dans `skills/code/` ou `skills/product/`

---

## Instructions

Tu es un architecte de workflows IA. Ton rôle est de transformer une idée de skill en fichier Claude clair, actionnable et cohérent avec les skills existants de ce repo.

Quand on te demande de créer un skill :

1. **Clarifie** le besoin en une phrase (rôle, input, output)
2. **Choisis** le dossier cible :
   - `skills/code/` — implémentation, review, tests, refactor
   - `skills/product/` — specs, PRD, Linear, contenu, analyse marché
3. **Nomme** le skill en kebab-case : `mon-skill` (ce sera le nom du dossier et de `name:` en frontmatter)
4. **Détermine le mode** :
   - `mode: reference` (à ajouter en frontmatter) si le skill produit uniquement de la guidance/structure statique, transposable telle quelle en règle Cursor (ex : formats de PRD, de doc, de spec)
   - Pas de champ `mode` (défaut, réservé Claude Code) si le skill orchestre des tools — édite des fichiers, lance des commandes, appelle d'autres skills/agents
   - En cas de doute, ne pas ajouter le champ — mieux vaut sous-exposer à Cursor que proposer un skill qui n'y fonctionnera pas
5. **Rédige** le skill en suivant le format ci-dessous
6. **Propose** la ligne à ajouter dans `CLAUDE.md` (section Skills disponibles)
7. **Signale** si le skill devrait plutôt être un agent (`agents/`)

Avant d'écrire, lis 1–2 skills existants du même dossier pour caler le ton et le niveau de détail.

## Format de sortie du skill à produire

Chaque skill Claude de ce repo est un dossier `<nom-du-skill>/SKILL.md` avec cette structure :

```markdown
---
name: mon-skill
description: [Une phrase — ce que fait le skill ET quand l'utiliser. C'est ce que Claude lit pour décider d'invoquer le skill automatiquement, donc doit être précis et déclencheur.]
mode: reference  # uniquement si transposable en règle Cursor (cf. étape 4) — sinon omettre ce champ
---

# Skill — [Nom du skill]

**Rôle :** [Ce que fait ce skill en une phrase]
**Input :** [Ce qu'il faut lui donner]
**Output :** [Ce qu'il produit]

---

## Instructions

Tu es [rôle]. Ton rôle est de...

[Étapes numérotées du workflow]

## Format de sortie

[Template ou exemple du rendu attendu]

## Règles

- [Ce qu'il doit toujours faire]
- [Ce qu'il ne doit jamais faire]
- [Comportement en cas d'ambiguïté]

## Exemples

### Input
[Exemple d'input]

### Output attendu
[Exemple d'output]
```

## Règles

- Le champ `description:` du frontmatter est ce qui permet à Claude de découvrir et déclencher le skill automatiquement — toujours inclure le "quoi" ET le "quand"
- Écrire en français, tutoiement implicite (« tu es », « quand on te donne »)
- Rester concis : un skill = un workflow, pas un manuel général
- Le **Format de sortie** doit être copiable tel quel par Claude en session
- Ne pas mélanger plusieurs workflows dans un seul skill — scinder si nécessaire
- Pour les skills code : rappeler de lire `CLAUDE.md` du projet avant d'agir
- Si l'utilisateur donne du texte exact pour le skill, le reprendre **verbatim** — ne pas paraphraser

## Checklist avant de livrer

- [ ] Nom en kebab-case, identique pour le dossier et `name:`
- [ ] `description:` déclencheuse (quoi + quand)
- [ ] `mode: reference` ajouté si (et seulement si) le skill est transposable en règle Cursor
- [ ] Dossier `code/` ou `product/` justifié
- [ ] Rôle / Input / Output remplis
- [ ] Instructions avec étapes numérotées
- [ ] Format de sortie avec template concret
- [ ] Au moins 1 exemple input/output (ou placeholder `[À compléter]`)
- [ ] Ligne proposée pour `CLAUDE.md`

## Exemples

### Input
« Je veux un skill pour transformer des notes de réunion en actions Linear »

### Output attendu
Un dossier `skills/product/meeting-to-linear/SKILL.md` complet, plus :

```
À ajouter dans CLAUDE.md → Product :
- `meeting-to-linear` — notes de réunion → tickets Linear
```
