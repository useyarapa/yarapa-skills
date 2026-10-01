# Documentation Audit

Audits product and engineering documentation as a source-of-truth system.

Use it when PRDs, ADRs, architecture docs, API contracts, schemas, acceptance criteria, or knowledge bases must be checked for authority conflicts, ambiguity, traceability, implementation readiness, or mismatch with observed implementation.

## Core boundary

Documentation is the audit and remediation target. Code, tests, configuration, infrastructure, CI/CD, and runtime may be inspected as read-only evidence but are never modified by this skill.

The final report is high-signal: material findings only. Cosmetic variation, praise, pass dumps, optional cleanup, and zero-action noise are omitted.

## Files

- `SKILL.md` — operating contract.
- `assets/report.md` — compact report shape.
- `references/audit-dimensions.md` — analysis lenses.
- `references/finding-schema.md` — material finding schema.
- `references/readiness-gates.md` — full-readiness gates.
- `tests/pressure-scenarios.md` — regression scenarios.
