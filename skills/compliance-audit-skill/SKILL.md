---
name: compliance-audit-skill
description: Evidence-driven internal audit and gap assessment for ISO management-system standards and PCI DSS. Use for ISO/IEC 27001, ISO/IEC 27002, ISO/IEC 27701, ISO 22301, ISO/IEC 42001, ISO/IEC 20000-1, ISO 31000, ISO 9001, PCI DSS v4.x, cross-framework evidence mapping, repository/cloud/runtime control verification, readiness reviews, and remediation planning. Read-only by default; never claim certification or compliance without sufficient scope and evidence.
license: MIT
---

# Compliance Audit

Audit standards using **current scope + current system state + operating evidence**, not assumptions.

Core workflow:

**Observe -> Verify -> Source of Truth -> Requirement -> Evidence -> Finding -> Proven Gap -> Minimal Remediation -> Re-verify**

This skill is for internal audits, gap assessments, technical control reviews, certification-readiness reviews, and evidence collection. It does **not** replace an accredited certification audit, Qualified Security Assessor (QSA), legal advice, or a formal attestation.

## 1. Non-negotiable rules

1. **Read-only by default.** Audit, inspect, search, and report. Do not modify repositories, cloud resources, policies, tickets, CI, IAM, or runtime unless the user separately approves an exact Change Set.
2. **Verify the standard version before auditing.** Use the official standards body or scheme owner as source of truth. Do not silently use an older edition.
3. **Never invent requirement text.** ISO standards are copyrighted and often licensed. If the full normative text is not available, use clause/control identifiers and public official summaries only. Ask for the user's licensed copy when exact requirement-level assessment needs text that is not publicly available.
4. **Scope before conclusions.** No audit conclusion without a defined organizational, technical, and temporal scope.
5. **Evidence beats documentation.** A policy proves policy existence; it does not prove runtime enforcement. A configuration proves configuration; it does not prove effective operation over time.
6. **No certification claims.** Never say "ISO certified", "PCI compliant", "passes certification", or equivalent unless the claim is independently established by the appropriate authorized assessment/certification evidence.
7. **No automatic cross-framework equivalence.** Reuse evidence across frameworks, but assess each requirement separately.
8. **No guessing.** Missing evidence is `UNKNOWN`, not compliant and not non-compliant.
9. **Current state first.** Inspect current configuration/runtime/provider state first. Use history, logs, tickets, and samples when a requirement needs evidence of operation over time.
10. **Stop when evidence is sufficient.** Do not create bespoke controls where the standard, vendor, or a widely adopted proven implementation already exists.

## 2. Finding vocabulary

Every assessed item must use exactly one primary state:

- `VERIFIED` — sufficient evidence supports the requirement for the assessed scope and period.
- `PARTIAL` — some required elements are supported, but material evidence or implementation is incomplete.
- `GAP` — evidence demonstrates a requirement is not met in the assessed scope.
- `N/A` — requirement is not applicable, with explicit scope/applicability justification.
- `UNKNOWN` — evidence is insufficient or inaccessible; no conclusion is justified.

Additionally label reasoning as needed:

- `Inference` — supported interpretation, but not directly proven.
- `Hypothesis` — plausible explanation requiring verification.
- `Unknown` — missing fact/evidence.

Do not convert `UNKNOWN` into `GAP` merely because evidence is absent, unless the requirement itself requires retained documented evidence and the absence of that required record is verified.

## 3. Supported framework profiles

Read `references/framework-registry.md` first. Then load only the relevant profile(s).

Primary profiles:

- ISO/IEC 27001:2022 + Amd 1:2024 — ISMS requirements.
- ISO/IEC 27002:2022 — information-security control guidance; not independently certifiable.
- ISO/IEC 27701:2025 — PIMS requirements and guidance.
- ISO 22301:2019 + Amd 1:2024 — BCMS requirements; revision may be underway, so verify current publication state.
- ISO/IEC 42001:2023 — AI management system.
- ISO/IEC 20000-1:2018 — service management system.
- ISO 31000:2018 — risk-management guidance; not a certifiable management-system requirements standard.
- ISO 9001:2026 — quality management system.
- PCI DSS v4.0.1 — payment account data security.

For ISO/IEC 27001 load `references/iso-27001.md`.
For PCI DSS load `references/pci-dss-4.0.1.md`.
For other ISO profiles load `references/iso-frameworks.md`.

## 4. Audit modes

Choose the smallest mode that answers the user:

### A. Repository audit
Use when evidence is limited to source repositories, CI/CD configuration, dependency manifests, IaC, tests, and documentation.

Mandatory limitation: repository evidence alone cannot establish organization-wide ISO conformity or PCI DSS compliance.

### B. Technical-control audit
Adds live infrastructure/provider/IAM/network/runtime/configuration/logging evidence.

### C. Operating-effectiveness audit
Adds time-bounded samples showing controls operated repeatedly: access reviews, incident records, patch/vulnerability cycles, backups/restores, training, change approvals, internal audits, management reviews, etc.

### D. Certification/readiness gap assessment
Adds management-system evidence and formally defined scope. Output is readiness/gaps only unless authorized certification evidence exists.

### E. Cross-framework mapping
Map the same evidence to multiple frameworks while keeping independent findings per requirement.

## 5. Required pre-audit scope

Establish and record:

- audit objective;
- framework + exact edition/version;
- organization/business unit/product/service in scope;
- repositories/applications/accounts/cloud tenants/environments in scope;
- data types and regulated data in scope;
- third parties/service providers in scope;
- production vs non-production boundaries;
- audit period or evidence window;
- exclusions and their justification;
- authoritative systems for policies, execution, runtime, IAM, incidents, and evidence;
- unavailable evidence/access constraints.

If scope is not established, perform only a **limited technical review** and state the limitation prominently.

## 6. Evidence hierarchy

Prefer stronger evidence when multiple sources conflict:

1. live runtime/provider/IAM/network state;
2. machine-enforced configuration and policy;
3. execution records/logs/monitoring/audit trails;
4. CI/CD and repository configuration;
5. approved policies/procedures/risk records;
6. tickets, reviews, approvals, reports, training records;
7. interviews or uncorroborated statements.

The hierarchy is contextual: a management-system requirement may require an approved record as the authoritative evidence, while a technical enforcement claim requires technical evidence.

For each piece of evidence record:

- source/system;
- exact object/path/resource;
- observed value/state;
- timestamp or evidence period;
- scope relevance;
- whether it proves design, implementation, or operating effectiveness.

## 7. Assessment procedure

For each applicable requirement/control:

1. Identify the exact framework identifier.
2. Determine applicability to the defined scope.
3. State the expected evidence type without copying proprietary normative text.
4. Collect current evidence.
5. If ongoing operation matters, sample historical/period evidence.
6. Compare evidence with the requirement.
7. Record `VERIFIED`, `PARTIAL`, `GAP`, `N/A`, or `UNKNOWN`.
8. Separate verified facts from inference/hypothesis.
9. Identify root cause only when supported by evidence.
10. Recommend the minimum proven remediation pattern; do not execute it.

## 8. Technical audit expectations

When available, inspect relevant evidence such as:

- identity provider, MFA, SSO, privileged access, service accounts;
- cloud IAM, organization/account boundaries, network controls, security groups/firewalls;
- encryption configuration and key-management state;
- secret storage and rotation mechanisms;
- asset/service inventory and ownership;
- CI/CD branch protections, required checks, artifact provenance, deployment permissions;
- dependency/SBOM/vulnerability scanning and remediation records;
- application security testing and secure development controls;
- centralized logs, alerting, retention, clock synchronization, audit trails;
- backups, restore tests, recovery objectives, continuity evidence;
- incident-response procedures and incident records;
- change-management records;
- data flows, retention/deletion, privacy roles, processors/subprocessors;
- vendor/service-provider evidence;
- policies, risk registers, treatment plans, Statement of Applicability where relevant;
- internal audit, management review, objectives/metrics, corrective actions.

Do not mark a control `VERIFIED` based only on a markdown document if runtime enforcement is material.

## 9. Root-cause standard

Use this order:

- `Fact`: observed state.
- `Symptom`: resulting failure/exposure.
- `Inference`: interpretation supported by evidence.
- `Hypothesis`: unverified possible cause.
- `Verified root cause`: cause demonstrated by config, runtime state, logs, reproducible test, or authoritative record.

Do not call a hypothesis a root cause.

## 10. Reporting

Use `assets/report.md` for the final report and `assets/finding.md` for each material finding.

Minimum report sections:

1. Executive scope and conclusion limits.
2. Standard editions used.
3. Evidence sources and evidence window.
4. Coverage summary by framework/domain.
5. Findings table.
6. Detailed evidence-backed findings.
7. Unknowns / inaccessible evidence.
8. Cross-framework evidence reuse, if applicable.
9. Remediation backlog ordered by prerequisite/causal dependency, not cosmetic severity alone.
10. Re-verification plan.

Never report a percentage such as "87% compliant" unless the framework itself defines that metric and the calculation is justified. Prefer counts of assessed states and uncovered scope.

## 11. Remediation rules

Recommend official/default behavior first, then a widely adopted proven pattern. Bespoke control design is last resort.

A remediation recommendation must include:

- affected system/object/control;
- current verified state;
- target state;
- evidence for the gap;
- expected impact;
- side effects/dependencies;
- rollback or reversal strategy when relevant;
- verification criteria;
- untouched scope.

Do not modify anything until the user approves a concrete Change Set.

## 12. Re-verification

After any approved remediation is performed by an authorized actor:

1. re-read current state;
2. verify only approved fields/resources changed;
3. repeat the original evidence test;
4. verify operating evidence if the requirement cannot be proven immediately;
5. update the finding state without erasing the previous evidence trail.

If verification is incomplete, state: `ยังไม่เสร็จ`.
## 13. Copyright and standards-text handling

- Do not reproduce full ISO clauses, Annex A controls, or substantial copyrighted standard text.
- Use identifiers, short names where publicly available, and your own audit/evidence procedure.
- If the user supplies a licensed copy, analyze it for the user's audit but avoid redistributing substantial portions.
- Link to official standards-body pages for edition/version verification.
