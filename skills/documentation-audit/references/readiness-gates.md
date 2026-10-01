# Readiness Gates

Use only for a full documentation-readiness audit.

`DOCUMENTATION READY FOR IMPLEMENTATION` requires every applicable gate to pass:

- no unresolved Critical/High authority conflict that changes implementation;
- no implementation-blocking ambiguity or contradiction;
- no material capability requires inventing a product, architecture, integration, security, operational, or ownership decision;
- material capabilities have sufficient authority and ownership;
- material implementation-facing contracts are traceable to justified needs;
- material documented failure controls have evidence appropriate to the claimed closure level;
- no unresolved decision is used as a provisional implementation contract;
- blind-reader reconstruction requires no material undocumented assumption.

If any applicable gate fails, return `DOCUMENTATION NOT READY FOR IMPLEMENTATION` and list only the failed gates plus the exact evidence or decision needed to close them.

Non-blocking findings may remain while documentation is ready. Do not inflate them into blockers.

Never report a readiness percentage unless a denominator and scoring method were defined before the audit.
