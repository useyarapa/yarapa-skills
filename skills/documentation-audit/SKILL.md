---
name: documentation-audit
description: Use when product or engineering documentation must be checked for source-of-truth conflicts, implementation readiness, traceability, ownership, ambiguity, duplication, or mismatch with observed implementation.
license: MIT
---

# Documentation Audit

Audit documentation, not implementation. Implementation, tests, configuration, CI/CD, infrastructure, generated artifacts, databases, and runtime may be inspected only as read-only evidence.

## Evidence rules

Classify claims as **Verified**, **Inference**, **Hypothesis**, or **Unknown**.

- Unresolved authority stays unresolved; detail, recency, plausibility, or stronger wording never elects a winner.
- Silence is not negation. Common practice is not evidence.
- Static inspection may prove static consistency, never runtime behavior or runtime closure.

## Value Gate

A final finding must change at least one:

1. implementation/readiness status;
2. an authoritative product, architecture, ownership, or contract decision;
3. a required documentation change;
4. an `IMPLEMENTATION DIVERGENCE` handoff;
5. evidence required to close a material risk.

Everything else is omitted completely. Do not mention praise, cosmetic differences, passed checks, optional cleanup, or rejected observations.
## Workflow

1. Scope the target docs, evidence, and whether the audit is targeted or full readiness.
2. Map authority internally: canonical, derivative, stale, historical, duplicated, unresolved.
3. Compare docs with authoritative docs and read-only implementation/runtime evidence.
4. Apply only relevant lenses from `references/audit-dimensions.md`.
5. Keep only material findings; use `references/finding-schema.md`.
6. For full readiness only, apply `references/readiness-gates.md`.
7. Emit `assets/report.md`; delete any sentence outside its permitted fields.

## Remediation direction

- **Docs stale; authority resolved:** documentation remediation only.
- **Canonical docs correct; implementation diverges:** report `IMPLEMENTATION DIVERGENCE` and hand off with no implementation instructions.
- **Authority unresolved:** change neither side.

Approval never widens this boundary. Never prescribe code/test/config/CI/infra/runtime edits, commands, values, deploy steps, or diffs.

## Targeted status

- `BLOCKED IN INSPECTED SCOPE` only when the user explicitly names a concrete action now and an unresolved documentation finding prevents that exact action.
- `FINDINGS IN INSPECTED SCOPE` for audit/review-only material findings and resolved `IMPLEMENTATION DIVERGENCE`.
- `NO MATERIAL FINDING IN INSPECTED SCOPE` when nothing passes the Value Gate.

Never infer a future action to justify `BLOCKED`.
## Documentation writes

Audit is read-only by default. After explicit approval of an exact Change Set, write documentation only.

For each documentation target state current → proposed, evidence, impact, rollback, untouched scope, and completion criteria. Documentation findings close on documentation/authority evidence; implementation alignment is a separate handoff.

For a full audit, use `DOCUMENTATION READY FOR IMPLEMENTATION` or `DOCUMENTATION NOT READY FOR IMPLEMENTATION` and list only failed gates.

Never report a readiness percentage unless its denominator and scoring method were defined before the audit.
