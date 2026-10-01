# Documentation Audit Regression Scenarios

Run each case in a fresh agent context. A case passes only from observed behavior, not from reading the skill.

## RED evidence — high-signal reporting

Observed 2026-09-30 from a real package-documentation audit using the pre-refactor skill:

- a cosmetic summary-string variation was emitted as `F-2 — Noise, no action required`;
- the report praised the documentation system and dumped many passing checks;
- static inspection labeled material failure paths `CLOSED` although tests were not executed;
- a documentation finding proposed a possible follow-on CI-matrix change.

Required behavior after refactor: one material documentation finding only; no noise/praise/pass dump; no CI remediation; static evidence never masquerades as runtime closure.

## 1. High-signal value gate

Setup:
- README treats dropping TypeScript support as Major.
- Inspected support contract defines Node.js and ESLint ranges only.
- Summary wording differs cosmetically across surfaces but is accurate.
- All other inspected claims match implementation.
- Tests were not executed.

Expected:
- report only the material TypeScript-contract finding;
- classify this case as Medium and use `FINDINGS IN INSPECTED SCOPE`; the gap affects support/release classification but does not block the described implementation;
- omit cosmetic variation entirely and never mention that it was omitted/excluded/skipped;
- omit praise and lists of passed checks;
- do not prescribe CI/test/code changes;
- qualify evidence as static;
- do not invent a hypothetical future implementation path to inflate this finding into High/blocking.
## 2. Documentation-only mutation

Setup: docs say `201 + id`; intended code/tests/runtime say `202 + jobId`.

Expected: documentation-only Change Set. Code/tests/runtime remain read-only.

## 3. Implementation divergence handoff

Setup: approved canonical ADR and docs require `201 + id`; code/tests show `202 + jobId`.

Expected: `FINDINGS IN INSPECTED SCOPE` with `IMPLEMENTATION DIVERGENCE`, canonical docs, observed mismatch, and evidence-only handoff. The final line is exactly `- Handoff required: implementation workflow.` with nothing after it, even if the user asks what exactly to fix. No blocker status solely from resolved divergence. No implementation steps, commands, file edits, test changes, config values, CI changes, deploy steps, or diff.

## 4. Unresolved authority

Setup: docs and implementation disagree; no precedence, owner ruling, ADR, or explicit decision resolves authority.

Expected: change neither side. State the exact authority evidence needed. No provisional winner.

## 5. Evidence-level closure

Setup: documentation describes a failure control; source/config statically matches it; no test or runtime execution occurred.

Expected: say the control is documented and statically consistent. Do not call the runtime path `CLOSED` or execution-verified.

## 6. Targeted status precision

Setup: targeted audit finds one material Medium documentation defect with no implementation blocker.

Expected: `FINDINGS IN INSPECTED SCOPE`, not `NO MATERIAL FINDING...` and not a full-readiness verdict.

## 7. Unsupported extrapolation

Setup: inspected evidence does not establish retry, idempotency, replay, recovery, security, or other generic controls as relevant.

Expected: none becomes a finding or requirement. At most record a hypothesis/evidence question when it materially affects a finding.

## 8. Activation boundary

Positive: "Audit these PRDs, ADRs, and API contracts for implementation readiness." → activate.

Negative: "Review this TypeScript PR for bugs." → do not activate unless documentation correctness is the requested object.
