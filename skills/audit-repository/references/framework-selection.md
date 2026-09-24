# Framework Selection

Select frameworks by applicability. More frameworks do not make an audit stronger; correct scope and evidence do.

Before each audit, verify current editions against `sources.md` when internet access is available.

## Mandatory backbone

| Area                        | Authority                                                  | Apply when                                                      |
| --------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------- |
| Evaluation process          | ISO/IEC 25040:2024 — SQuaRE Quality evaluation framework   | Every software repository audit                                 |
| Product quality model       | ISO/IEC 25010:2023 — Product quality model                 | Every software/ICT product audit                                |
| Source-code quality         | ISO/IEC 5055:2021 — Automated source code quality measures | Source code is in scope                                         |
| Product quality measurement | ISO/IEC 25023:2016                                         | Quantitative product-quality measures are needed and applicable |
| Quality requirements        | ISO/IEC 25030:2019                                         | Quality requirements must be elicited, normalized, or traced    |

ISO/IEC 25023:2016 remains current as of 2026-09 but is under revision. Verify the current published edition before a future audit.

## CI/CD and secure-development overlay

| Area                        | Authority                         | Apply when                                                                                            |
| --------------------------- | --------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Secure software development | NIST SP 800-218 SSDF v1.1         | CI/CD, development workflow, release security, vulnerability prevention/response are in scope         |
| Software supply chain       | SLSA v1.2 Approved Specification  | Source integrity, build integrity, provenance, artifacts, attestations, or release trust are in scope |
| OSS project security        | OpenSSF OSPS Baseline v2026.08.28 | Public/open-source projects where its maturity model is applicable                                    |

Do not substitute OpenSSF Scorecard for the standards above. Scorecard may provide supporting evidence, not the controlling framework.

## Application-security overlay

Use **OWASP ASVS 5.0.0** for web applications/services where technical application-security controls are actually applicable.

Do not apply ASVS wholesale to an ESLint config, pure library, documentation repo, or other target with no relevant web-application attack surface.

## Official ecosystem contracts

After selecting standards, use authoritative upstream documentation for technology-specific correctness, for example:

- language/runtime specifications
- Node.js/package-manager/package metadata rules
- framework and compiler documentation
- CI provider documentation
- artifact registry/publisher documentation
- operating-system/platform contracts

These sources define implementation behavior that generic quality standards intentionally do not.

## Provider-side settings

Provider-side state is in scope only when a selected control requires it. Examples include required checks, workflow token permissions, protected environments, approval gates, branch/ruleset enforcement, and trusted publishing.

If provider-side state cannot be read, report the control as `UNKNOWN` or `INCONCLUSIVE`. Do not infer nonconformity from repository files alone.

## Formal-claim rule

Public abstracts and summaries are sufficient to select and organize a framework, but not to assert full formal conformance to proprietary normative text.

Use:

- `ALIGNED` when the audit is organized using the framework but full normative requirements were not available.
- `CONFORMING` / `NONCONFORMING` only when the exact applicable requirement/control is available and evaluated with sufficient evidence.
