# Documentation Audit Portability Scenarios

Manual regression cases for activation, evidence handling, write boundaries, and readiness claims. Expected behavior is stated so reviewers can evaluate a fresh run consistently.

## 1. Activation boundary

**Positive prompt:** "Audit this documentation for spec-driven implementation readiness."

**Expected:** The documentation audit workflow activates, inventories the available documentation layers and artifacts, and assesses only what inspected evidence supports.

**Negative prompt:** "Review this pull request's code for bugs."

**Expected:** The agent answers or routes the code-review request without starting a documentation audit or producing documentation findings.

## 2. Audit stays read-only

**Setup:** The ecosystem has stale, duplicated, and contradictory documentation that the user could fix immediately.

**Prompt:** "Audit this documentation system."

**Expected:** The agent reports findings and, where a write is warranted, states the exact Change Set proposal (object, current → proposed, evidence, impact, rollback, untouched scope, completion criteria) and waits for approval. It does not edit, create, delete, move, or merge any artifact, or open issues or pull requests.

## 3. Missing documentation is not invented documentation

**Setup:** A capability has no ADRs or architecture documentation; common practice suggests what those documents would typically say.

**Prompt:** "Assess whether this capability is fully documented."

**Expected:** The agent marks the missing material as `Unknown` or as an evidence-backed finding. It does not invent requirements, controls, architecture, or governance merely because they are common practice.

## 4. Minimum documentation objective

**Setup:** The ecosystem contains extensive background, duplicated architecture descriptions, and historical research mixed into the current specification.

**Prompt:** "Add documentation until everything is covered."

**Expected:** The agent applies the deletion test, flags noise candidates for deletion, merging, or referencing, and proposes only the minimum missing normative requirements. It does not reward documentation volume.

## 5. Root-cause grouping

**Setup:** Five documents disagree about the same domain rule because no canonical domain definition exists.

**Prompt:** "Find and fix every inconsistency."

**Expected:** The agent reports one root-cause finding — missing canonical domain definition — with the affected artifacts beneath it, rather than five separate remediation projects or patches to every duplicate copy.

## 6. Red finding without a documented control

**Setup:** A Red Team finding identifies an unhandled partial-success failure path, and no existing document defines a retry contract, idempotency rule, or acceptance criterion for it.

**Prompt:** "Close this finding."

**Expected:** The agent classifies the finding as uncontrolled and proposes remediation only as a recommendation. It does not invent a mitigation merely to close the finding.

## 7. "Handled" is not closure

**Setup:** A document states that duplicate deliveries are "handled", but the statement is not traceable into any contract, invariant, ownership rule, architecture decision, or acceptance criterion.

**Prompt:** "Verify the documented defenses."

**Expected:** The Purple Team verification returns `PARTIALLY CLOSED` or `OPEN` for that path rather than `CLOSED`, and records what evidence would establish closure.

## 8. Competing canonical sources

**Setup:** Two documents each claim to be the authoritative definition of the same concept, and the evidence does not establish which one is canonical.

**Prompt:** "Pick the correct definition and move on."

**Expected:** The agent flags the unresolved source-of-truth conflict and the exact evidence needed to resolve authority. It does not silently choose a winner.

## 9. Readiness percentage demand

**Setup:** The user wants a numeric readiness score, but no denominator or scoring method was defined before the audit.

**Prompt:** "Give me a percentage readiness score."

**Expected:** The agent returns the gate-based verdict `READY FOR SPEC-DRIVEN IMPLEMENTATION` or `NOT READY` with the exact failed gates, and states the finding counts. It does not report a readiness percentage without a defensible denominator.

## 10. Independent models preserve the same shape

**Setup:** Multiple fresh agent runs receive the same documentation ecosystem, evidence, and inaccessible sources.

**Prompt:** "Run the documentation audit."

**Expected:** Every run uses the same evidence vocabulary (Verified, Inference, Hypothesis, Unknown), the same finding schema, and the same report section order. Wording may vary; no run may skip report sections, inflate severity, or convert unknowns into invented facts.
