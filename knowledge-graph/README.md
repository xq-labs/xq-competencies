# Knowledge Graph

The Competency Builder activities as a knowledge graph, for systems that consume nodes and relationships rather than tables. The same activities are available as a single flat table in [`../data/activities.csv`](../data/activities.csv) — this folder is a different shape of the same content, not different content.

Introduced in v1.2.0.

## Files

| File | Records | Description |
|------|---------|-------------|
| `nodes.jsonl` | 88 | 44 `Activity` nodes and 44 `Material` nodes |
| `relationships.jsonl` | 44 | One `hasPart` edge from each Activity to its Material |

Both are [JSON Lines](https://jsonlines.org/): one JSON object per line, UTF-8, newline-terminated. Read them line by line rather than parsing either file as a single document.

```python
import json
nodes = [json.loads(line) for line in open("knowledge-graph/nodes.jsonl")]
edges = [json.loads(line) for line in open("knowledge-graph/relationships.jsonl")]
```

## Shape

Each activity produces exactly one `Activity`, one `Material`, and one `hasPart` edge between them.

```
Activity ──hasPart──> Material
   │                     │
   │                     └── content: the full activity as Markdown
   └── componentSkillId: links into the competency framework
```

**`Activity`** carries the metadata: name, description, `componentSkillId`, grouping, duration, grade levels, language, licence.

**`Material`** carries the teaching content: a self-contained Markdown document with the resource links, setup, description, the full instructional sequence including teacher notes, and attribution. A teacher can run the activity from it without opening the slides.

**Identifiers** are stable and derived from the activity's own id, never from its title:

```
xq:activity:compass_points
xq:material:compass_points
xq:haspart:compass_points
```

An activity renamed in a later release keeps the same identifiers. Re-exporting unchanged data produces byte-identical files.

## Joining to the framework

Every `Activity` carries two identifiers for its parent component skill, so you can join on whichever your system uses:

| Property | Joins to |
|----------|----------|
| `componentSkillId` | `id` in [`../data/component_skills.csv`](../data/component_skills.csv), e.g. `LL.SAw.3.b` |
| `componentSkillCaseUuid` | `case_uuid` in the same file — the identifier the [CASE 1.1 API](https://case.xq.institute/ims/case/v1p1) serves |

`competencyId` and `learnerOutcomeId` are included for the rest of the hierarchy.

## Property reference

### Activity

| Property | Notes |
|----------|-------|
| `name`, `description` | Title and what students learn |
| `componentSkillId`, `componentSkillCaseUuid` | Parent component skill; always present |
| `competencyId`, `learnerOutcomeId` | Rest of the framework chain |
| `curriculumLabel` | Always `Competency Builder` |
| `studentGroupingType` | One of `Individual`, `Pair`, `Small Group`, `Whole Class` |
| `timeRequired` | ISO 8601 duration, e.g. `PT20M`. **Null for 20 of 44** — see below |
| `academicSubject` | Null throughout this release — these activities are subject-agnostic |
| `gradeLevel` | `["9","10","11","12"]` |
| `inLanguage` | `en-US` |
| `educationalUse` | `Instruction` |
| `audience` | `Teacher` |
| `author`, `provider` | `XQ Institute` |
| `license` | CC BY 4.0 URL |
| `gradingRequired`, `submissionRequired` | Both `false` |
| `url` | The activity's page on the XQ Competency Navigator |

### Material

| Property | Notes |
|----------|-------|
| `content` | The full activity as Markdown (331 KB across the 44) |
| `encodingFormat` | `text/markdown` |
| `materialType` | `Document` |
| `role` | `Core` — the activity's primary material |
| `identifier` | Same as the node id |
| `attributionStatement` | XQ attribution, plus a third-party credit where the source material is not XQ's |
| `audience`, `author`, `license`, `inLanguage` | As on the Activity |

## Known gaps

**20 of 44 activities have `timeRequired: null.`** Their runtime is a range — `15-25 min`, `10-12 min` — because it genuinely varies with class size and discussion. ISO 8601 has no range form, and picking a midpoint would assert a precision the source does not have, so the property is null rather than guessed. The human-readable value is in the `run_time` column of [`../data/activities.csv`](../data/activities.csv).

**`academicSubject` is null for every activity.** These build durable skills across subjects; a competency is not a school subject, so none was inferred.

## Content provenance

The `Material.content` Markdown is extracted from each activity's source slide deck, including the teacher guidance that sits off-canvas beside the slides. Every section is traceable to the slide it came from — headings carry a `*(slide N)*` marker — and figures are described in text so the document stands alone without the images.

## Licence

© 2026 XQ Institute. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Where an activity adapts third-party material, its `Material.attributionStatement` names the source; carry that credit through with the XQ attribution when you reuse it.
