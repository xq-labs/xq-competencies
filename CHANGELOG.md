# Changelog

## v1.1.0 — 2026-06-09

### Added
- New `data/domains.csv` — the 13 domains that group related competencies under each learner outcome (e.g., "Appreciating and Creating Art" groups Artistic Expression and Art Analysis)
- `competencies.csv`: new `domain_id` and `domain_name` columns linking each competency to its domain

### Changed
- `competencies.csv`: the free-text `outcome_area` column was replaced by `domain_id` / `domain_name`
- All text fields are now single-line plain text — embedded line breaks and stray whitespace have been removed (learner outcome descriptions previously contained line breaks)
- Documentation updated for the four-level hierarchy: Learner Outcome → Domain → Competency → Component Skill

All notable changes to the XQ Competencies are documented here.

## v1.0.0 — 2026-03-19

- Initial release of the XQ Competencies
- 5 learner outcomes, 37 competencies, 115 component skills
- 139 research sources with citations
- 37 competency icons (SVG)
