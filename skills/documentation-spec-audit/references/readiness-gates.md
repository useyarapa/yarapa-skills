# Readiness Gates

Do not claim readiness by subjective impression.

A full documentation audit can return `READY FOR SPEC-DRIVEN IMPLEMENTATION` only when all applicable gates pass.

## Required gates

- Zero unresolved Critical contradictions.
- Zero Critical requirements without an owner.
- Zero Critical requirements without downstream trace.
- Zero implementation-blocking ambiguities.
- Zero competing canonical definitions for Critical concepts.
- Zero obsolete artifacts presented as current canonical truth.
- Zero Critical capabilities requiring the engineer or coding agent to invent a material decision.
- Every major capability has identifiable ownership.
- Every major capability passes cross-layer trace.
- Every material Red Team path has either:
  - an existing Blue control,
  - an explicit accepted limitation, or
  - a clearly identified unresolved decision.
- Purple Team verifies that material controls actually close the identified path.
- Blind Reader can reconstruct the intended system without undocumented historical context.

## Result

If any gate fails:

`NOT READY`

State the exact failed gates and the evidence needed to close them.

If all applicable gates pass:

`READY FOR SPEC-DRIVEN IMPLEMENTATION`

Do not use a readiness percentage unless a mathematically defensible denominator and scoring method were defined before the audit.
