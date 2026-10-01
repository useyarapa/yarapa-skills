# Audit Lenses

Use lenses to find material documentation defects. Lenses are internal analysis tools, not mandatory report sections.

## 1. Authority and consistency

Check:
- which artifact is canonical for each material decision;
- conflicting or stale definitions;
- ambiguity that permits materially different implementations;
- undocumented precedence.

Authority must come from evidence. Detail, recency, plausibility, or implementation specificity does not establish authority.

## 2. Completeness and readiness

Ask whether an engineer can implement the material capability without inventing a consequential decision.

Inspect only what the capability requires: behavior, states, contracts, ownership, dependencies, permissions, failure behavior, and acceptance evidence.

Do not require generic best practices that inspected evidence does not make relevant.

## 3. Traceability and ownership

Trace material intent to implementation-facing contracts and back to justified needs.

Implementation-facing code, tests, configuration, and runtime are read-only evidence endpoints. They are never remediation targets for this skill.
## 4. Failure paths

Inspect only failure paths grounded in documented behavior or necessary consequences of it.

For a relevant path, identify the documented control and the evidence level supporting it.

- Documentation only → report the control as documented.
- Source/config inspected → report static consistency if supported.
- Test/runtime observed → report execution evidence if supported.

Do not call a runtime path `CLOSED` from static inspection alone.

## 5. Minimality and blind-reader test

Ask:
- must a competent engineer guess a material decision?
- does duplicated text create competing authority?
- would removing this content change a decision, readiness, remediation, or verification requirement?

If removal changes nothing material, omit the observation from the final report.
