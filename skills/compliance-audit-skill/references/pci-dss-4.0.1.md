# PCI DSS v4.0.1 Audit Profile

Baseline: PCI DSS v4.0.1. Verify the current PCI SSC document library before each audit.

## Scope gate — mandatory

Do not make a PCI DSS compliance conclusion until cardholder-data environment (CDE) scope is established.

Establish:

- whether the entity is a merchant, service provider, or both;
- payment channels and acceptance methods;
- account-data flows;
- where cardholder data and sensitive authentication data are received, processed, stored, or transmitted;
- CDE system components;
- systems connected to or able to impact the CDE;
- segmentation controls and validation evidence;
- third-party service providers and responsibility allocation;
- applicable validation method (e.g. SAQ/ROC path) based on authoritative PCI/acquirer guidance.

If those are unknown, output `PCI scope: UNKNOWN` and perform only a pre-scope technical review.

## Requirement-domain coverage

Assess the current PCI DSS v4.0.1 requirements using the official standard as the normative source. Organize evidence around the twelve requirement families:

1. network security controls;
2. secure configurations;
3. protection of stored account data;
4. cryptographic protection during transmission over open/public networks;
5. protection from malicious software;
6. secure systems and software;
7. access restriction by business need;
8. user identification and authentication;
9. physical access restriction;
10. logging and monitoring;
11. regular security testing;
12. organizational security policies/programs.

These labels are navigational summaries; always use the official PCI DSS v4.0.1 requirement and testing procedure for exact assessment criteria.

## PCI-specific evidence rules

- Validate technical controls in the CDE, not merely enterprise defaults.
- Treat segmentation as a security boundary claim that requires evidence/testing.
- Do not assume tokenization, hosted payment pages, or a PSP automatically removes all PCI scope.
- Verify third-party responsibility and evidence; outsourcing does not automatically transfer all responsibility.
- Distinguish Defined Approach from Customized Approach where applicable.
- For requirements with periodic frequencies, verify the required recurring evidence in the audit period.
- Verify targeted risk analyses when the standard requires them for flexible frequencies or applicability.
- Check that controls that became effective after the v4.0 transition dates are actually operational; do not rely on an old transition-state interpretation.

## Validation/certification language

Do not say "PCI certified" unless that exact status is substantiated. PCI DSS validation commonly uses artifacts such as SAQs, ROCs, and AOCs according to the entity/validation path. A technical gap assessment is not an Attestation of Compliance.

## Evidence examples

- CDE inventory/data-flow diagrams;
- firewall/network-security-control rules and reviews;
- hardened configuration baselines;
- PAN storage/displays/retention controls;
- TLS/cryptographic configuration;
- anti-malware/endpoint controls where applicable;
- SDLC, code review, vulnerability remediation, WAF/app-layer protections where applicable;
- IAM, MFA, privileged access and account lifecycle;
- physical-security evidence where in scope;
- audit logs, centralized monitoring and review evidence;
- ASV scans, internal/external scans, penetration tests, segmentation tests where applicable;
- incident-response and policy/training evidence;
- TPSP responsibility matrix and attestations.
