# XQ Competency Framework

A durable skill framework for high school education, developed by [XQ Institute](https://xqsuperschool.org/).

## About

Today's young people are growing up in an increasingly complex world, and the ways they learn are evolving accordingly.

Recent advances in neuroscience, cognitive psychology, and the learning sciences have shed new light on how adolescents learn. Adolescence is a time of great cognitive malleability and growth. Learning across all domains — academic, cognitive, social, and emotional — is deeply affected by relationships, a sense of belonging, and engagement in rigorous and relevant learning experiences. All these domains are deeply intertwined.

At XQ, we believe that when high schools design experiences for their students that honor this rich complexity, students become more engaged, explore more deeply, and ultimately develop the knowledge, skills, and mindsets they need to succeed in college, career, and beyond.

Explore the full framework interactively at the [XQ Competency Navigator](https://xqcompetencies.xqsuperschool.org/).

Learn more about XQ's approach to learning at [learning.xq.institute](http://learning.xq.institute/).

## Framework Structure

The XQ Competency Framework is organized as a three-level hierarchy:

```
Learner Outcome
  └── Competency (with research sources)
        └── Component Skill (with 4 progression levels)
```

### Learner Outcomes

| ID | Learner Outcome |
|----|-----------------|
| FK | Holders of Foundational Knowledge |
| FL | Masters of All Fundamental Literacies |
| GC | Generous Collaborators for Tough Problems |
| LL | Learners for Life |
| OT | Original Thinkers for an Uncertain World |

Each learner outcome contains multiple **competencies** (37 total), which in turn contain **component skills** (115 total) — each with four progression levels: Emerging, Developing, Proficient, and Applying.

Every competency is backed by **research sources** (139 total) linking to peer-reviewed literature and foundational texts.

## Files

| File | Description |
|------|-------------|
| `learner_outcomes.csv` | 5 top-level learning goals |
| `competencies.csv` | 37 competencies with definitions, taglines, and descriptions |
| `component_skills.csv` | 115 granular skills with 4 progression levels each |
| `research_sources.csv` | 139 research citations backing each competency |
| `icons/` | SVG icons for each competency |
| `VERSION` | Current version, release date, and stats |
| `LICENSE` | CC BY 4.0 license text |

## CSV Relationships

The CSV files are relational and can be joined on ID columns:

```
learner_outcomes.csv    →  id
competencies.csv        →  id, learner_outcome_id
component_skills.csv    →  id, competency_id, learner_outcome_id
research_sources.csv    →  competency_id
```

Human-readable `competency_name` columns are included in `component_skills.csv` and `research_sources.csv` for convenience.

## Column Reference

### learner_outcomes.csv

| Column | Description |
|--------|-------------|
| `id` | Unique identifier (e.g., `FK`) |
| `name` | Learner outcome name |
| `description` | Full description |

### competencies.csv

| Column | Description |
|--------|-------------|
| `id` | Unique identifier (e.g., `FK.AC.1`) |
| `learner_outcome_id` | Parent learner outcome ID |
| `outcome_area` | Outcome area grouping |
| `name` | Competency name |
| `tagline` | Short description |
| `description` | Full description |
| `catchphrase` | Catchphrase headline |
| `catchphrase_description` | Catchphrase detail |
| `definition` | Formal definition |
| `definition_headline` | Definition headline |
| `resources_url` | Link to external resources |
| `icon_filename` | Filename in `icons/` folder |

### component_skills.csv

| Column | Description |
|--------|-------------|
| `id` | Unique identifier (e.g., `FK.AC.1.a`) |
| `competency_id` | Parent competency ID |
| `competency_name` | Parent competency name |
| `learner_outcome_id` | Top-level learner outcome ID |
| `name` | Skill name |
| `description` | Skill description |
| `example` | Real-world example |
| `progression_level_1_emerging` | Level 1: Emerging |
| `progression_level_2_developing` | Level 2: Developing |
| `progression_level_3_proficient` | Level 3: Proficient |
| `progression_level_4_applying` | Level 4: Applying |

### research_sources.csv

| Column | Description |
|--------|-------------|
| `competency_id` | Parent competency ID |
| `competency_name` | Parent competency name |
| `title` | Source title |
| `url` | DOI or source URL |
| `citation` | Full citation |
| `summary` | Why this source supports the competency |

## Versioning

This repository is versioned using [semantic versioning](https://semver.org/):

- **Major** — competencies or learner outcomes removed, or hierarchy restructured
- **Minor** — new competencies, skills, or learner outcomes added
- **Patch** — descriptions, definitions, or research sources updated

The current version is tracked in the `VERSION` file and as a git tag.

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to share and adapt this material for any purpose, even commercially, as long as you give appropriate credit to **XQ Institute**.

**Suggested attribution:**

> XQ Competency Framework by [XQ Institute](https://xqsuperschool.org/), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
