---
name: documentation-spec-audit
description: Evidence-driven audit of documentation and specification ecosystems for source-of-truth, traceability, contradictions, ownership, failure-path controls, and implementation readiness. Use when auditing PRDs, architecture docs, Notion or knowledge bases, umbrella or repo-local documentation, ADRs, API contracts, schemas, or acceptance criteria, or when deciding whether documentation is ready for spec-driven implementation. Read-only by default; not for code-only reviews, runtime incident response, or penetration testing unless documentation correctness is the primary object.
license: MIT
---

# Documentation Spec Audit

Audit documentation as an engineering source-of-truth system.

The objective is not maximum documentation. The objective is the **minimum sufficient canonical documentation** that lets an engineer or coding agent implement the intended system without inventing material product, domain, architectural, integration, security, operational, or ownership decisions.

## 1. Operating contract

Use evidence-driven reasoning. Always separate:

- **Verified** — directly supported by inspected evidence.
- **Inference** — strongly implied but not explicitly defined.
- **Hypothesis** — plausible issue requiring more evidence.
- **Unknown** — required information is absent or cannot be established.

Do not present inference or hypothesis as fact.

Do not invent requirements, policies, controls, architecture, governance, or user disclosures merely because they are common practice.

For any section, rule, or artifact ask:

> Who consumes this information, and what decision or implementation action depends on it?

If no meaningful downstream consumer exists, treat it as a noise candidate.

## 2. Read-only mode

Audit, inspect, and report. Do not edit, create, delete, rename, move, merge, archive, open issues, create PRs, change Notion, or modify source code unless the user explicitly authorizes an exact Change Set.

Before proposing a write, state:

- system / object / field or file
- current → proposed
- evidence
- expected impact
- rollback
- untouched scope
- completion criteria

Wait for approval before writing.

## 3. Scope discovery

Before judging quality, identify the actual documentation layers and sources available.

Typical layers:

- business / product knowledge
- Notion or knowledge base
- umbrella / organization-wide docs
- architecture docs
- repo-local docs
- ADRs
- API / integration contracts
- schemas / configuration
- acceptance criteria / tests
- implementation
- runtime/provider facts

Do not assume all knowledge belongs in an umbrella repository.

For every artifact identify:

- name and location
- scope
- apparent owner
- status if known
- inbound/outbound references
- whether canonical, derivative, historical, duplicated, stale, or obsolete

When multiple documentation systems exist, establish the source-of-truth graph before remediation.

## 4. Audit workflow

Run the audit as one evidence-preserving loop:

1. **Inventory** — map the documentation layers, artifacts, and source-of-truth graph (section 3).
2. **Dimensions** — assess all fourteen dimensions in `references/audit-dimensions.md` as one traversal, combining evidence gathering where a single pass supports several dimensions.
3. **Red → Blue → Purple loop** — attack the specification, classify existing controls, verify closure (section 5).
4. **Blind-reader reconstruction** — rebuild the intended system from canonical documentation alone (section 6).
5. **Re-check** — repeat the affected portions of the graph until the stop condition (section 10) is met.

## 5. Red, Blue, and Purple loop

### Red Team

Attack the specification itself, using the attack surface of the Red Team dimension in `references/audit-dimensions.md`.

Try to prove that a competent engineer following the documents literally could produce materially wrong behavior.

Do not invent unrealistic attacks to inflate findings.

### Blue Team

For every valid Red finding, inspect whether the existing documentation defines a sufficient control, using the control types and classification of the Blue Team dimension in `references/audit-dimensions.md`.

Do not invent a mitigation merely to close a finding.

### Purple Team

Verify whether the documented defense actually closes the Red path. For each material Red finding:

1. state the failure path
2. identify existing defense
3. test whether it closes the path
4. search for bypasses and downstream contradictions
5. check whether the defense creates new ambiguity or coupling
6. verify the control across affected documentation layers

Classify: `CLOSED`, `PARTIALLY CLOSED`, `OPEN`, or `FALSE POSITIVE`.

A sentence saying "handled" is not closure. The defense must be traceable into a contract, invariant, ownership rule, architecture decision, or acceptance criterion.

## 6. Blind-reader reconstruction

After the main audit, discard historical context and author intent, and reconstruct the intended system from canonical documentation alone using the Blind Reader dimension in `references/audit-dimensions.md`.

Record every point where reconstruction requires guessing. Historical conversation or tribal knowledge does not count as canonical evidence.

## 7. Trace as a graph

Trace important capabilities through the documentation graph in both directions: capability down to acceptance evidence, and implementation-facing artifacts back up to the business need. The trace chains for each dimension are in `references/audit-dimensions.md`.

Broken edges are findings.

## 8. Root cause discipline

Do not create multiple remediation projects for symptoms with the same cause.

Example: if five documents disagree because no canonical domain definition exists, report one root cause — missing canonical domain definition — then list affected artifacts and consequences.

Prefer repairing the canonical source and references over patching every duplicate copy.

## 9. Finding quality

Normalize every material finding with `references/finding-schema.md`; its severity, confidence, and classification vocabularies are the only accepted values.

Do not inflate severity. Not every uncertainty is a blocker.

Valid remediation is often not adding text. It may be to delete, merge, move, replace with a reference, shorten, mark historical, declare the canonical source, resolve the contradiction, or add only the missing normative requirement.

## 10. Stop condition

Repeat only the affected portions of the audit until no new Critical or High root-cause findings emerge from the same graph, and further passes produce only repetition, cosmetic issues, or low-value commentary.

Then return the verdict using the readiness gates in `references/readiness-gates.md`.

## 11. Reporting

Return the final report using `assets/report.md`, in its section order.

- The verdict is `READY FOR SPEC-DRIVEN IMPLEMENTATION` or `NOT READY`, with exact blockers.
- Group findings by root cause, deduplicated.
- Order the remediation plan by dependency and root cause, not by file, and do not execute remediation.
- State the exact evidence required to close each blocker.

Grade the result by correctness, determinism, traceability, clarity, ownership, minimality, and implementation readiness — never by documentation volume.
