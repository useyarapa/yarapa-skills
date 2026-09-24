# Standards-Driven Audit Protocol

Use ISO/IEC 25040:2024 as the evaluation-process authority. The working protocol below operationalizes that evaluation without inventing repository-specific quality criteria.

## 1. Evaluation definition

Record before defect hunting:

- target repository/product and explicit exclusions
- audit objective: release readiness, quality assessment, security, supply chain, etc.
- stakeholders/consumers
- supported runtime/platform/package/deployment model
- CI/CD and release path
- explicit contracts and quality requirements
- selected standards and why each applies
- evidence sources available and unavailable

Never silently broaden scope.

## 2. Quality model

Classify product-quality concerns under ISO/IEC 25010:2023 characteristics where applicable:

- functional suitability
- performance efficiency
- compatibility
- interaction capability
- reliability
- security
- maintainability
- flexibility
- safety

Do not manufacture a defect merely to populate every characteristic. Mark characteristics `NOT APPLICABLE` when justified.

## 3. Source-code evaluation

Use ISO/IEC 5055:2021 as the source-code measurement authority where its measures are applicable. Focus on evidence of architectural/coding weaknesses that create operational risk or excessive cost, not on taste.

Do not invent a numerical threshold. A metric threshold needs an applicable requirement, standard basis, contractual criterion, documented project baseline, or defensible comparative baseline.

When exact ISO/IEC 5055 normative measures are unavailable, classify the audit as `ALIGNED` and avoid fabricated measure identifiers or claims of ISO compliance.

## 4. Product-quality measurement

Use ISO/IEC 25023:2016 when a quantitative measure is appropriate. Do not convert a measure into pass/fail without an established acceptance criterion. If no acceptance criterion exists, report the measurement and its interpretation separately.

Use ISO/IEC 25030:2019 when missing/ambiguous quality requirements prevent a defensible conformity decision.

## 5. CI/CD and secure-development evaluation

Apply NIST SSDF v1.1 to applicable secure-development practices. Evaluate evidence such as:

- development/build/release roles and trust boundaries
- automated verification gates
- vulnerability and dependency handling
- secrets and credentials in automation
- workflow execution of untrusted input/code
- release/publish authentication
- secure build/release configuration
- vulnerability response evidence where in scope

Do not score controls whose required organizational/provider evidence is unavailable; mark them `UNKNOWN`.

## 6. Software supply-chain evaluation

Apply SLSA v1.2 to applicable Source and Build tracks. Evaluate the actual source/build path and supporting evidence for integrity, provenance/attestations, isolation or tamper resistance, and verification as required by the selected SLSA target.

Do not assign a SLSA level unless every requirement for that exact level/track has been verified from the approved specification.

## 7. OSS and application-security overlays

For applicable OSS projects, evaluate OSPS Baseline controls against a declared OSPS maturity level. Do not choose a higher level merely to generate findings.

For applicable web applications/services, evaluate ASVS 5.0.0 requirements relevant to the architecture and target verification level. Cite versioned ASVS requirement identifiers when available.

## 8. Technology-specific contract evaluation

Use official upstream specifications/documentation to verify:

- package/public API and exports
- runtime/platform compatibility
- compiler/framework semantics
- build/package contents
- release/publish behavior
- CI-provider behavior

Comparable repositories cannot override upstream behavior or explicit product contracts.

## 9. Root-cause and remediation

A finding must trace:

`requirement/control → evidence → observed behavior → impact → root cause (if proven) → smallest remediation`

Use modern comparable projects only after a finding exists, to identify a proven remediation pattern when official/default behavior is insufficient.

## 10. Termination

Stop when:

- every selected framework/control area has a recorded result: `CONFORMING`, `NONCONFORMING`, `INCONCLUSIVE`, `UNKNOWN`, `NOT APPLICABLE`, or framework-level `ALIGNED` when formal conformance cannot be claimed;
- suspected material issues have been verified, downgraded, or discarded;
- repeated symptoms have been consolidated;
- remaining observations are stylistic, speculative, or outside the evaluation requirements.

The stop condition is **completion of the defined evaluation**, not zero findings and not “nothing left to improve.”
