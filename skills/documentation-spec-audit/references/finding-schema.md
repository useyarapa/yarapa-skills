# Finding Schema

Normalize each material finding.

```text
Finding ID:
Severity:
Confidence:
Audit Dimension:
Classification:
Affected Artifact(s):
Affected Capability:
Verified Evidence:
Observed Problem:
Root Cause:
Why It Matters:
Downstream Impact:
Canonical Source Expected:
Recommended Minimal Change:
Action Type: Delete | Merge | Move | Rewrite | Add | Reference | Resolve | None
Dependencies:
Verification Criteria:
Status:
```

## Severity

### Critical
The documentation could materially cause:
- data corruption
- security boundary failure
- financial inconsistency
- incompatible system behavior
- inability to implement a critical capability

### High
A significant product/architecture decision must be invented, or multiple materially different implementations are plausible.

### Medium
Meaningful inconsistency, ambiguity, ownership issue, duplication, or documentation quality problem without immediate critical implementation risk.

### Low
Minor clarity or discoverability improvement.

Do not inflate severity.

## Confidence

Use:
- Verified
- Inference
- Hypothesis
- Unknown

## Classification

Use exactly one primary classification:
- Engineering Blocker
- Product Decision Needed
- Architecture Decision Needed
- Documentation Defect
- Informational Finding
- Noise

## Root-cause grouping

If several findings are symptoms of one missing canonical decision, group them under that root cause and retain affected-artifact detail beneath it.

Avoid duplicate remediation work.
