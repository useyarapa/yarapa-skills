# Audit Lenses

Use these lenses as a taxonomy, not as fourteen separate passes. Combine evidence gathering whenever one traversal answers several questions.

## 1. Authority / source of truth

Ask:
- Where is each material concept authoritatively defined?
- Are there competing canonicals, stale mirrors, or undocumented precedence rules?
- Can authority be established from evidence rather than guessed?

A source conflict remains open until explicit authority evidence resolves it. Never turn a "more specific" or "more plausible" source into a provisional implementation contract.

## 2. Completeness / implementation readiness

Ask whether each material capability is specified enough to implement without inventing a consequential decision.

Inspect as applicable:
- purpose and user-visible behavior
- inputs, outputs, states, transitions, invariants
- ownership and dependencies
- data and permissions
- integration contracts
- failure, retry, idempotency, and recovery behavior
- acceptance criteria

Do not demand irrelevant implementation detail.

## 3. Consistency / ambiguity / contradiction

Compare sources that describe the same concept.

Look for:
- incompatible behavior or state transitions
- conflicting terminology, ownership, retention, authentication, or integration rules
- vague language that permits materially different implementations

For blocking ambiguity, state the competing interpretations, downstream difference, and exact missing decision.

## 4. Ownership / boundaries

Ask whether every material responsibility has one defensible owner and whether global and local documentation respects that boundary.

Look for:
- overlapping or orphan ownership
- hidden cross-system coupling
- duplicated domain logic
- global docs defining local internals
- local docs redefining global invariants

## 5. Forward and reverse traceability

Forward trace:
Business or Product Need → Capability → Requirement → Domain Rule → Architecture / Contract → Owner → Acceptance Evidence

Reverse trace:
Implementation-facing Construct → Architecture Reason → Requirement → Capability → Business or Product Need

Implementation-facing constructs are evidence endpoints, not writable remediation targets for this skill. Broken material edges are findings. Do not require decorative traceability that changes no decision.

## 6. Failure paths and documented controls

Attack only material paths grounded in inspected evidence or necessary consequences of the documented behavior. Generic industry risks may be recorded as hypotheses or evidence questions, but cannot become findings or fail readiness gates by themselves. Omission of an unstated control is not a grounded failure path unless the documentation explicitly requires that control or the path necessarily follows from the documented behavior.

Examples when evidence makes them applicable:
- duplicate or out-of-order delivery
- partial success
- timeout or retry
- concurrent state changes
- authorization boundary failure
- provider behavior changes
- reconciliation or recovery failure

For each valid path:
1. state the failure path;
2. identify the existing documented control;
3. verify whether that control closes the path;
4. search for bypasses or contradictions.

Classify closure as `CLOSED`, `PARTIALLY CLOSED`, `OPEN`, or `FALSE POSITIVE`.

## 7. Minimality / duplication / noise

Use the deletion test:

> If this content disappeared, what concrete implementation or decision would become impossible or unsafe?

If there is no meaningful answer, treat it as a noise candidate. Prefer one canonical definition plus references over repeated normative copies.

## 8. Blind-reader reconstruction

Ignore tribal knowledge and historical conversation. Reconstruct the intended system from canonical evidence alone.

Record every material point where a competent engineer must guess. A necessary guess is evidence of an unresolved documentation gap, ambiguity, or authority problem.
