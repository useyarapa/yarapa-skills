# Material Finding Schema

Only findings that pass the Value Gate in `SKILL.md` are reportable.

## Severity

- **Critical** — documentation can directly drive destructive, security-critical, financially inconsistent, or incompatible behavior.
- **High** — a concrete action explicitly requested now cannot proceed without inventing a material decision.
- **Medium** — a material documentation defect changes a release, consumer, ownership, remediation, handoff, or verification decision without blocking an explicitly requested action.

Do not emit Low, Informational, or Noise findings.

`IMPLEMENTATION DIVERGENCE` is a separate classification, not documentation severity. It is not a documentation blocker unless a separate unresolved documentation finding exists.

## Evidence level

Use the strongest observed level: **Documented**, **Static**, or **Execution**. Never present Static evidence as Execution evidence.

## Grouping

Group symptoms only when evidence supports one root cause. Otherwise keep the cause `Unknown` and group only by the same unresolved decision.
