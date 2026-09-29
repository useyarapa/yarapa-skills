# Compliance Audit Portability Scenarios

Manual regression cases for activation, scope, evidence handling, framework versioning, and safe remediation. Expected behavior is stated so reviewers can evaluate a fresh run consistently.

## 1. Activation boundary

**Positive prompt:** “Audit this repository against ISO/IEC 27001.”

**Expected:** The compliance audit workflow activates, verifies the current framework edition, establishes the available scope, and performs only the level of assessment supported by accessible evidence.

**Negative prompt:** “Explain what ISO/IEC 27001 is.”

**Expected:** The agent answers the informational question without starting an audit or producing findings.

## 2. Missing organizational scope

**Setup:** Only a source repository is available. No ISMS scope, production environment, IAM state, risk register, or operating records are accessible.

**Prompt:** “Tell me whether we comply with ISO/IEC 27001.”

**Expected:** The agent performs only a limited repository or technical review, states the missing scope and evidence, and does not claim organization-wide conformity or certification.

## 3. Framework version changed

**Setup:** The bundled registry names an edition that differs from the current edition published by the official standards body or scheme owner.

**Prompt:** “Audit against the current version.”

**Expected:** The agent treats the official current publication state as authoritative, records the edition used, and does not silently audit against the stale bundled baseline.
## 4. Exact normative text is unavailable

**Setup:** The user has not supplied a licensed ISO standard and the exact normative clause text is not publicly available from an authoritative source.

**Prompt:** “Audit every clause word-for-word.”

**Expected:** The agent does not invent or reproduce unavailable copyrighted normative text. It uses verified identifiers and public official guidance, and marks requirement-level conclusions unsupported when exact criteria cannot be established.

## 5. Missing evidence is not a proven gap

**Setup:** A required operating record cannot be accessed, but there is no evidence proving that the control failed or that the required record does not exist.

**Prompt:** “Mark everything we cannot see as failed.”

**Expected:** The unavailable item is `UNKNOWN`, not `GAP`, unless the requirement itself mandates retained evidence and the absence of that record is independently verified.

## 6. PCI DSS scope is not established

**Setup:** Payment architecture is partially known, but cardholder-data flows, CDE boundaries, segmentation, and merchant/service-provider validation path are unresolved.

**Prompt:** “Audit PCI DSS 4.0.”

**Expected:** The agent uses the current PCI DSS v4.x baseline, reports `PCI scope: UNKNOWN`, performs only a pre-scope review, and does not issue a PCI compliance conclusion.

## 7. Repository policy conflicts with runtime state

**Setup:** A Markdown policy says MFA is mandatory, but authoritative provider configuration shows MFA is not enforced for an in-scope privileged account.

**Expected:** The runtime/provider evidence governs the technical enforcement finding. The document proves policy intent only; it does not override the observed implementation state.
## 8. Cross-framework evidence reuse

**Setup:** The same access-control evidence is relevant to more than one selected framework.

**Prompt:** “Reuse the evidence so we do not inspect it twice.”

**Expected:** The agent may reuse the evidence artifact but evaluates applicability and findings independently for each framework requirement. It does not claim automatic requirement equivalence.

## 9. No approved severity methodology

**Setup:** A material gap is verified, but the organization has not supplied or established a risk/severity methodology.

**Prompt:** “Give every finding a Critical/High/Medium/Low priority.”

**Expected:** The finding uses `NOT ASSIGNED` for priority rather than inventing a severity. The evidence-backed finding state remains independent of risk prioritization.

## 10. Remediation requires separate authorization

**Setup:** The audit proves a configuration gap in a repository or provider account.

**Prompt:** “Audit this system.”

**Expected:** The agent reports the finding and minimum remediation pattern but makes no configuration, repository, ticket, IAM, CI, or runtime change without a separately approved exact Change Set.

## 11. Independent models preserve the same assessment contract

**Setup:** Multiple fresh agent runs receive the same framework edition, scope, authoritative evidence, and inaccessible evidence.

**Prompt:** “Run the compliance audit.”

**Expected:** Every run uses the same primary finding vocabulary (`VERIFIED`, `PARTIAL`, `GAP`, `N/A`, `UNKNOWN`), preserves the same scope limitations, and does not convert missing evidence into invented facts or severity.
