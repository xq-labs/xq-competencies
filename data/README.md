# Data Documentation

This folder contains the XQ Competency Framework as structured CSV files. The data is exported from the XQ Institute's content management system and represents the complete framework hierarchy.

## Framework Hierarchy

```
Learner Outcome
  └── Competency (with research sources)
        └── Component Skill (with 4 progression levels)
```

The framework contains **5 learner outcomes**, **37 competencies**, **115 component skills**, and **139 research sources**.

## Files

| File | Rows | Description |
|------|------|-------------|
| `learner_outcomes.csv` | 5 | Top-level learning goals |
| `competencies.csv` | 37 | Competencies with definitions, taglines, and descriptions |
| `component_skills.csv` | 115 | Granular skills with 4 progression levels each |
| `research_sources.csv` | 139 | Research citations backing each competency |

## Relationships

The CSV files are relational and can be joined on ID columns:

```
learner_outcomes.csv    →  id
        ↑
competencies.csv        →  id, learner_outcome_id
        ↑
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

## ID Conventions

IDs follow a hierarchical dot notation:

| Level | Pattern | Example |
|-------|---------|---------|
| Learner Outcome | `XX` | `FK` |
| Competency | `XX.YY.N` | `FK.AC.1` |
| Component Skill | `XX.YY.N.a` | `FK.AC.1.a` |

## Learner Outcomes

| ID | Name |
|----|------|
| FK | Holders of Foundational Knowledge |
| FL | Masters of All Fundamental Literacies |
| GC | Generous Collaborators for Tough Problems |
| LL | Learners for Life |
| OT | Original Thinkers for an Uncertain World |

## Usage Examples

### Python (pandas)

```python
import pandas as pd

outcomes = pd.read_csv('learner_outcomes.csv')
competencies = pd.read_csv('competencies.csv')
skills = pd.read_csv('component_skills.csv')
sources = pd.read_csv('research_sources.csv')

# Join skills with their parent competency
skills_with_context = skills.merge(
    competencies[['id', 'outcome_area', 'tagline']],
    left_on='competency_id',
    right_on='id',
    suffixes=('', '_competency')
)

# Get all research for a specific competency
creative_process_sources = sources[sources['competency_id'] == 'OT.Creat.1']
```

### R

```r
library(readr)
outcomes <- read_csv("learner_outcomes.csv")
competencies <- read_csv("competencies.csv")
skills <- read_csv("component_skills.csv")
sources <- read_csv("research_sources.csv")

# Filter skills for a learner outcome
fk_skills <- skills[skills$learner_outcome_id == "FK", ]
```

### SQL (SQLite)

```sql
.import --csv learner_outcomes.csv learner_outcomes
.import --csv competencies.csv competencies
.import --csv component_skills.csv component_skills
.import --csv research_sources.csv research_sources

-- Full hierarchy for a skill
SELECT lo.name AS outcome, c.name AS competency, cs.name AS skill
FROM component_skills cs
JOIN competencies c ON cs.competency_id = c.id
JOIN learner_outcomes lo ON cs.learner_outcome_id = lo.id;
```
