---
name: documentation-audit
description: Use when auditing product or engineering documentation such as PRDs, architecture docs, ADRs, API contracts, schemas, acceptance criteria, or knowledge bases for source-of-truth conflicts, implementation readiness, traceability, ownership, ambiguity, duplication, or failure-path gaps. Code, tests, configuration, infrastructure, and runtime may be inspected as read-only evidence, but this skill never modifies implementation.
license: MIT
---

# Documentation Audit

Audit documentation as an engineering source-of-truth system.

The objective is the minimum sufficient canonical documentation that lets an engineer or coding agent implement intended behavior without inventing material product, domain, architecture, integration, security, operational, or ownership decisions.

## Operating contract

Classify reasoning explicitly:

- **Verified** — directly supported by inspected evidence.
- **Inference** — supported interpretation, not explicitly defined.
- **Hypothesis** — plausible explanation requiring verification.
- **Unknown** — required information cannot be established.

Use inspected evidence only. Do not invent missing requirements, controls, architecture, ownership, or acceptance criteria because they are common practice.

When explaining impact, separate consequences directly entailed by the evidence from generic engineering possibilities. Common patterns such as retries, idempotency, replay defense, compensating controls, or recovery mechanisms are not findings or readiness requirements unless inspected evidence establishes that they apply. They may be labeled as hypotheses or evidence questions only.

Do not treat silence as negation. If one artifact omits a constraint stated elsewhere, omission alone is not evidence that the constraint is absent from the system. Report only the direct conflict, ambiguity, or authority gap that the inspected text establishes. Do not relabel behavior as a security, authorization, financial, or operational property unless the evidence establishes that classification.

An unresolved authority conflict stays unresolved. Never choose a "likely", "stronger", or "provisional" winner and turn it into an implementation assumption. State the competing definitions, the missing authority evidence, and the exact evidence or decision required to resolve them.

Audit is read-only by default. Even after approval, this skill may modify documentation only. Source code, tests, executable schemas, configuration, infrastructure-as-code, CI/CD, generated artifacts, databases, and runtime/provider state are read-only evidence and are never mutation targets for this skill.

If authoritative documentation is correct but implementation diverges, report `IMPLEMENTATION DIVERGENCE` with the observed mismatch and canonical documentation evidence, then hand off to an implementation workflow. Do not edit, patch, rewrite, refactor, test-fix, configure, deploy, or prescribe implementation steps, commands, file edits, replacement code, test changes, configuration values, or an executable diff from this skill. The handoff states what diverges and which documentation is authoritative, not how to implement the fix.

## Workflow

1. **Scope** — establish the audit objective, available evidence, inaccessible sources, and whether the request is targeted or a full readiness audit.
2. **Map authority** — inventory relevant artifacts and identify canonical, derivative, historical, duplicated, stale, or unresolved sources.
3. **Trace capabilities** — follow material capabilities from upstream intent to implementation-facing contracts and acceptance evidence, then reverse-trace implementation-facing constructs back to justified needs. Implementation evidence may confirm or contradict documentation, but remains read-only.
4. **Challenge the documentation** — use the applicable lenses in `references/audit-dimensions.md`. For a full readiness audit, cover every applicable lens; for a targeted audit, use only the affected lenses.
5. **Verify failure paths** — for each material failure path, identify the existing documented control and determine whether it closes the path. Do not invent a mitigation to make a finding pass.
6. **Normalize root causes** — use `references/finding-schema.md`; group symptoms only when a causal root cause is supported by evidence. If causality is not established, keep root cause `Unknown` and group by the shared unresolved decision or conflict without claiming causation.
7. **Judge readiness** — apply `references/readiness-gates.md` only when implementation readiness is in scope.
8. **Report** — use `assets/report.md`; recommend the smallest evidence-backed documentation remediation and stop when further review yields only repetition or cosmetic commentary. In a targeted review, require only the evidence necessary to close the inspected finding; do not add ADRs, tests, owner records, or other artifacts unless existing governance/evidence makes them necessary. When the required fix is outside documentation, report the divergence and handoff instead of designing or executing that fix.

## Authority and closure rules

A conflicting source cannot be repaired by silently preferring the more detailed, newer-looking, safer-looking, or more implementation-specific document. Resolve authority through explicit evidence.

"Handled", "supported", or similar prose is not closure by itself. A material control must be traceable to a contract, invariant, ownership rule, architecture decision, acceptance criterion, or other authoritative documentation.

Missing evidence is not automatically a defect. Record what is unknown and why it matters. Escalate severity only when the missing or conflicting decision can materially change implementation or safety.

## Write boundary

This skill has a one-way mutation boundary: **evidence may come from documentation or implementation, but writes may target documentation only**.

When documentation remediation requires a write, state the approved documentation target, current → proposed state, evidence, expected impact, rollback, untouched scope, and completion criteria. Re-read current state immediately before writing and verify the resulting state afterward.

Never include source code, tests, executable schemas, configuration, infrastructure, CI/CD, generated artifacts, databases, or runtime/provider state in the writable Change Set. If those need changes, record `IMPLEMENTATION DIVERGENCE`, identify the mismatching observed state and authoritative documentation, and stop at handoff without implementation instructions.

## Reporting rules

Do not report a readiness percentage unless a denominator and scoring method were defined before the audit.

For a full readiness audit, the verdict is `DOCUMENTATION READY FOR IMPLEMENTATION` or `DOCUMENTATION NOT READY FOR IMPLEMENTATION` with exact failed gates. For a targeted review, never emit either full-readiness verdict. Use a scope-limited status such as `BLOCKED IN INSPECTED SCOPE` or `NO BLOCKER FOUND IN INSPECTED SCOPE`, and do not generalize to uninspected documentation.
