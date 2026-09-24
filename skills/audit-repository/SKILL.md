---
name: audit-repository
description: Use when auditing a software repository for product or source quality, security, CI/CD, supply-chain integrity, release readiness, compatibility, maintainability, or over-engineering.
---

# Auditing Repositories

## Overview

Perform a **read-only, standards-driven repository audit**. The target is evidence-backed conformity and bounded risk assessment, not perfection, aesthetic cleanup, or making one repository resemble another.

## Mandatory Workflow

1. **Define the evaluation target and purpose.** Identify repository type, product boundaries, consumers, supported runtimes/platforms, delivery model, CI/CD system, and declared contracts. Unknown facts remain `UNKNOWN`.
   - _Done when:_ The target, objective, boundaries, contracts, and unavailable facts are recorded.
2. **Select applicable standards before inspecting for defects.** Read `references/framework-selection.md`.
   - _Done when:_ Each selected or excluded framework has an applicability reason.
3. **Establish evaluation requirements and evidence.** Use explicit product requirements, public contracts, official upstream specifications, runtime evidence, tests, build/release evidence, and provider-side state only when required to verify an applicable control.
   - _Done when:_ Requirements and available or unavailable evidence are mapped to the selected controls.
4. **Evaluate each selected framework/control.** Follow `references/audit-protocol.md`.
   - _Done when:_ Every selected area has a result, evidence reference, and rationale.
5. **Gate every candidate finding.** Use `references/finding-contract.md`. Admit `BLOCKER` or `MATERIAL` findings only when an applicable requirement/control, exact evidence, and concrete consequence are established. Admit an `ADVISORY` only when a documented applicable objective and evidence-backed benefit are established.
   - _Done when:_ Every candidate is either supported by the finding contract or discarded with a reason.
6. **Consolidate common root causes.** Merge repeated symptoms from the same cause; retain an advisory only when it names a distinct objective-linked benefit.
   - _Done when:_ Repeated symptoms are consolidated, advisory objectives are named, and unproven causes are labeled.
7. **Write a decision-first report at the defined scope.** Follow the report order and finding format in `references/finding-contract.md`: put one readiness decision and severity counts first, then findings, scope, and a compact standards/conformity matrix. Keep evidence close to each claim and avoid repeating it across sections.
   - _Done when:_ Every selected area is assessed, each finding has the required evidence and scope fields, and the report states exactly one readiness status.

## Scope Rules

Source code, architecture represented in code, tests, build/package configuration, CI/CD workflows, release/publish automation, dependency handling, artifacts, provenance, and relevant provider-side controls are in scope when applicable.

Repository administration is **not** a general audit target. Labels, topics, issue templates, cosmetic settings, project boards, and preferences are excluded. Branch/ruleset, token permissions, environments, approvals, or trusted publishing may be inspected only when needed to verify a specific CI/CD, SSDF, SLSA, OSPS, or release control.

Audit actions are read-only. Missing provider access means `UNKNOWN`, not failure.

## Authority Order

1. Applicable normative standard/control or explicit product requirement
2. Public API / documented contract
3. Official runtime/framework/package-manager/provider specification
4. Reproducible repository/runtime evidence
5. Applicable ecosystem convention
6. Comparable modern repository, **remediation evidence only**
7. Personal/LLM preference — **no authority**

## Critical Rules

- Difference ≠ defect. Unusual ≠ nonconforming.
- Do not invent thresholds, requirements, supported environments, or threat models.
- Do not treat a reference repository as a specification.
- Do not recommend incidental refactors, normalization, naming cleanup, or architecture changes without a proven finding.
- Prefer official/default mechanisms, then widely adopted proven patterns; bespoke mechanisms require an actual requirement.
- Never claim formal standards compliance without sufficient access to the applicable normative requirements. If only public summaries are available, state **aligned with**, not **compliant with**.
- Use `references/audit-protocol.md` for the termination criteria and `references/finding-contract.md` for the final report.
