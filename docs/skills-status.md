# Statut des skills

> 👁️ Dépôt de démo — le contenu détaillé n'est exposé que pour `create-skill`, `write-spec`, `prd-technical` et `code-review`. Le reste apparaît ici comme entrée de catalogue (référence de fichiers annexes ci-dessous non présents dans cette version).

> Vue d'ensemble de tous les skills du repo. Deux axes suivis séparément :
> le **contenu** du skill (rédigé ou encore un squelette) et sa
> **validation** en usage réel (personne ne le sait mieux que toi).
> Mets à jour la colonne Test au fur et à mesure que tu utilises chaque
> skill en conditions réelles.

**Légende contenu**
- 🟡 `draft` — squelette posé, pas encore rédigé, pas utilisable tel quel
- 🟢 `écrit` — instructions/format/règles complets, prêt à être utilisé

**Légende test**
- ⚪ `pending test` — pas encore utilisé en conditions réelles
- 🔵 `testing` — utilisé, en cours d'ajustement suite à un usage réel
- ✅ `validé` — comportement stable confirmé sur plusieurs usages
- ➖ `n/a` — pas applicable tant que le skill est en draft

---

## Meta

| Skill | Description | Statut | Test | Améliorations |
|---|---|---|---|---|
| [`create-skill`](../skills/create-skill/SKILL.md) | Crée ou complète un skill Claude réutilisable pour ce repo | 🟢 écrit | ⚪ pending test | |
| [`init-project`](../skills/init-project/SKILL.md) | Initialise/remet aux normes un projet avec le Product OS | 🟢 écrit | ⚪ pending test | |

## Code

| Skill | Description | Statut | Test | Améliorations |
|---|---|---|---|---|
| [`code-review`](../skills/code/code-review/SKILL.md) | Review d'un fichier ou d'une PR selon les standards du projet | 🟢 écrit | ⚪ pending test | |
| [`feature-builder`](../skills/code/feature-builder/SKILL.md) | Implémente une feature complète depuis un PRD technique | 🟢 écrit | ⚪ pending test | |
| [`test-writer`](../skills/code/test-writer/SKILL.md) | Génère les tests unitaires après une feature | 🟢 écrit | ⚪ pending test | |

## Product

| Skill | Description | Statut | Test | Améliorations |
|---|---|---|---|---|
| [`write-spec`](../skills/product/write-spec/SKILL.md) | Idée vague → spec structurée | 🟢 écrit | ⚪ pending test | |
| [`prd-functional`](../skills/product/prd-functional/SKILL.md) | Spec → PRD fonctionnel | 🟢 écrit | ⚪ pending test | |
| [`prd-technical`](../skills/product/prd-technical/SKILL.md) | PRD fonctionnel → PRD technique | 🟢 écrit | ⚪ pending test | |
| [`spec-to-linear`](../skills/product/spec-to-linear/SKILL.md) | PRD → tickets Linear structurés | 🟢 écrit | ⚪ pending test | |
| [`benchmark`](../skills/product/benchmark/SKILL.md) | Analyse concurrentielle structurée | 🟢 écrit | ⚪ pending test | A un `howto.md` pour l'exporter vers Claude Cowork |
| [`market-sizing`](../skills/product/market-sizing/SKILL.md) | Estimation TAM/SAM/SOM d'un marché | 🟢 écrit | ⚪ pending test | |
| [`content-comm`](../skills/product/content-comm/SKILL.md) | Sujet/update → contenu LinkedIn ou newsletter | 🟢 écrit | ⚪ pending test | |
| [`prd-design`](../skills/product/prd-design/SKILL.md) | *Placeholder* — brief flou → prompt design structuré | 🟡 draft | ➖ n/a | Squelette à écrire, contenu quasi vide |
| [`documentation`](../skills/product/documentation/SKILL.md) | *Placeholder* — répond aux questions sur le code/specs actuelles | 🟡 draft | ➖ n/a | Squelette à écrire, contenu quasi vide |

## Pro

| Skill | Description | Statut | Test | Améliorations |
|---|---|---|---|---|
| [`experience-interviewer`](../skills/pro/skills_itw/experience-interviewer/SKILL.md) | Interview approfondie → `experiences.md` source de vérité carrière | 🟢 écrit | ⚪ pending test | Le plus complet du repo : `references/question_bank.md` + `assets/template.md` + `howto.md` pour Cowork |

---

## Quand tu ajoutes un nouveau skill

Ajoute une ligne dans la catégorie correspondante avec statut `🟡 draft` et
test `➖ n/a` par défaut, puis fais-la passer à `🟢 écrit` / `⚪ pending test`
une fois le contenu rédigé — voir `README.md` section "Ajouter un skill"
pour la procédure de création.
