# Documentation Audit Report

Output starts with `## Result` and uses only these sections:

1. `Result`
2. `Material findings` when findings exist
3. `Documentation Change Set` only for requested/approved documentation writes

## Result

- Scope: audited documentation/capability only
- Status:
- Material findings: <count> (<blocker count> blockers)

With zero findings, stop here.

## Material findings

For a documentation finding:

### <ID> — <Severity> — <Title>

- Evidence: only evidence that directly supports this finding; include confidence/evidence level only when material. Do not mention unexecuted tests unless runtime evidence is required for this finding.
- Problem:
- Why it matters: direct consequence in inspected/requested scope only.
- Authority: `RESOLVED` | `UNRESOLVED` | `N/A`
- Required decision/evidence: only when needed.
- Documentation action: only when target and direction are authorized.
- Close when:
Optional fields are omitted, never filled with `None`, `N/A`, or commentary.

For unresolved authority, `Close when` states the required authority/evidence state, not solution branches.

For implementation divergence use exactly:

### <ID> — IMPLEMENTATION DIVERGENCE — <Title>

- Canonical documentation: <authority and required behavior>
- Observed mismatch: <read-only evidence only>
- Why it matters: <direct mismatch only>
- Handoff required: implementation workflow.

That handoff line is a hard stop.

## Documentation Change Set

Every target is documentation. State current → proposed, evidence, impact, rollback, untouched scope, and completion criteria.

Delete content whose only purpose is to say something was checked, passed, skipped, excluded, omitted, correct, non-actionable, or not reported. Emit no text before `## Result` or after the terminal field.
