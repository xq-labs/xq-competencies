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

## Repository Structure

```
xq-competency-framework/
├── data/                              # Framework data (CSV)
│   ├── README.md                      # Comprehensive data documentation
│   ├── learner_outcomes.csv           # 5 top-level learning goals
│   ├── competencies.csv               # 37 competencies with definitions
│   ├── component_skills.csv           # 115 skills with progression levels
│   └── research_sources.csv           # 139 research citations
├── icons/                             # Competency icons (SVG)
│   └── {id}_{name}.svg               # 37 hexagon icons
├── resources/                         # Research papers (PDF)
│   ├── XQ_Competencies_White_Paper.pdf
│   └── XQ_Competencies_Literature_Review.pdf
├── CHANGELOG.md                       # Version history
├── LICENSE                            # CC BY 4.0
├── NOTICE.md                          # Legal notices
├── README.md                          # This file
└── VERSION                            # Current version and stats
```

### Data

The [`data/`](data/) folder contains the full framework as four relational CSV files. See [`data/README.md`](data/README.md) for complete column documentation, relationships, and usage examples in Python, R, and SQL.

### Icons

The [`icons/`](icons/) folder contains SVG hexagon icons for each of the 37 competencies. Files are named `{competency_id}_{name-slug}.svg` (e.g., `FK.AC.1_artistic-expression.svg`).

### Resources

The [`resources/`](resources/) folder contains foundational research papers:

- **[Framing the XQ Competencies in Research & Practice](resources/XQ_Competencies_White_Paper.pdf)** — A research-based reference for all 37 XQ Competencies, grounded in learning science to support meaningful teaching and learning.

- **[The XQ Competencies: A Comparative Review of Leading Student Learning Frameworks](resources/XQ_Competencies_Literature_Review.pdf)** — A research study by KP Catalysts that finds the XQ Competencies provide a logical, coherent, and actionable framework for student learning.

## Versioning

This repository is versioned using [semantic versioning](https://semver.org/):

- **Major** — competencies or learner outcomes removed, or hierarchy restructured
- **Minor** — new competencies, skills, or learner outcomes added
- **Patch** — descriptions, definitions, or research sources updated

The current version is tracked in the `VERSION` file and as a git tag. See [`CHANGELOG.md`](CHANGELOG.md) for the full version history.

## Working with XQ

Interested in implementing or adapting the XQ Competency Framework? We'd be glad to collaborate.

Contact: [support@xqinstitute.org](mailto:support@xqinstitute.org)
Learn more: [xqsuperschool.org](https://xqsuperschool.org/)

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to share and adapt this material for any purpose, even commercially, as long as you give appropriate credit to **XQ Institute**.

**Attribution:**

> XQ Competency Framework © [XQ Institute](https://xqsuperschool.org/), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

"XQ Institute", "XQ", and associated logos are trademarks of XQ Institute and are not licensed under CC BY 4.0. See [NOTICE.md](NOTICE.md) for additional legal notices.
