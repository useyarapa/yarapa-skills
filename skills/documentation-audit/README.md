# Documentation Audit

## Purpose

Audit product and engineering documentation as a source-of-truth system and determine whether the inspected documentation is sufficient for implementation without material guessing.

## When to use

Use this skill for PRDs, architecture docs, ADRs, API contracts, schemas, acceptance criteria, knowledge bases, and other documentation that governs implementation behavior.

Do not use it for code-only review, implementation changes, incident debugging, or compliance auditing unless documentation correctness is the primary object.

## Behavior

The skill maps authority, traces material capabilities, finds contradictions and ambiguity, checks ownership and failure-path controls, groups findings by root cause, and applies readiness gates only when a full documentation-readiness audit is in scope.

It never resolves an authority conflict by choosing the more detailed, newer, safer-looking, or more plausible source. Missing authority evidence remains unresolved until explicit evidence or an authorized decision resolves it.

## Safety and write boundary

Auditing is read-only by default. The skill does not edit documentation, code, issues, pull requests, or external systems unless the user explicitly approves an exact Change Set.

## Files

- `SKILL.md` — authoritative audit workflow and boundaries.
- `assets/report.md` — compact report structure.
- `references/audit-dimensions.md` — audit-lens taxonomy.
- `references/finding-schema.md` — finding normalization schema.
- `references/readiness-gates.md` — documentation-readiness gates.
- `tests/pressure-scenarios.md` — RED/GREEN eval scenarios.
