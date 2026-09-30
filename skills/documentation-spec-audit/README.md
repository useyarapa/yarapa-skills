# Documentation Spec Audit

## Purpose

Audit a documentation and specification ecosystem as an engineering source-of-truth system and report whether it is ready for spec-driven implementation.

## When to use

Use this skill when the user asks to audit documentation or specifications — PRDs, architecture docs, Notion or knowledge bases, umbrella or repo-local documentation, ADRs, API contracts, schemas, or acceptance criteria — or to decide whether documentation is ready for spec-driven implementation.

## Behavior

The skill inventories the documentation layers, establishes the source-of-truth graph, and assesses fourteen evidence-driven dimensions as one loop, including the Red Team attack on the specification, Blue Team control classification, Purple Team closure verification, and a blind-reader reconstruction from canonical documentation alone. Findings are normalized by root cause with verified evidence separated from inference, hypothesis, and unknowns.

## Safety and write boundary

Auditing is read-only. The skill does not edit, create, delete, move, or merge any artifact, or open issues or pull requests, unless the user explicitly authorizes an exact Change Set. It does not invent requirements, controls, or mitigations to close findings, and it claims readiness only through the readiness gates in `references/readiness-gates.md`.

## Files

- `SKILL.md` — authoritative agent workflow and audit contract.
- `assets/report.md` — final report template.
- `references/audit-dimensions.md` — the fourteen audit dimensions.
- `references/finding-schema.md` — finding normalization schema.
- `references/readiness-gates.md` — readiness gates and verdict rules.
- `tests/pressure-scenarios.md` — manual regression scenarios for activation, evidence handling, and portability.
