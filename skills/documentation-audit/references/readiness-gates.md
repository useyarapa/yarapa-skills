# Readiness Gates

Use these gates only for a full implementation-readiness audit. Do not claim system-wide readiness from a targeted review.

A result can be `DOCUMENTATION READY FOR IMPLEMENTATION` only when every applicable gate passes.

## Required gates

- Zero unresolved Critical or High source-of-truth conflicts that can change implementation behavior.
- Zero implementation-blocking ambiguities or contradictions.
- Zero material capabilities that require an engineer or coding agent to invent a product, domain, architecture, integration, security, operational, or ownership decision.
- Every material capability has an identifiable authoritative source and owner.
- Every material capability has sufficient forward trace to implementation-facing contracts and acceptance evidence.
- Every material implementation-facing construct has sufficient reverse justification.
- Every material failure path is either closed by a documented control or covered by an explicitly authorized accepted limitation.
- No unresolved decision is being used as a "provisional", "likely", or "working" implementation contract.
- No obsolete or derivative artifact is presented as current canonical truth.
- Blind-reader reconstruction does not require material undocumented assumptions.

## Result

If any applicable gate fails:

`DOCUMENTATION NOT READY FOR IMPLEMENTATION`

State the failed gates and the exact evidence or authoritative decision required to close them.

If all applicable gates pass:

`DOCUMENTATION READY FOR IMPLEMENTATION`

Do not use a readiness percentage unless a denominator and scoring method were defined before the audit.
