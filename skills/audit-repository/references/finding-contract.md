# Finding and Report Contract

Use this contract to decide which observations qualify as findings and to make the final report easy to scan. Put the decision and findings first; keep evidence precise and avoid repeating it across sections.

## Finding gate

An observation becomes a finding only when all required fields are supported.

Use the single finding format below. Keep one finding per root cause, and include both affected and untouched scope.

- For `BLOCKER` or `MATERIAL`, establish an applicable requirement/control, precise evidence, and a concrete consequence.
- For `ADVISORY`, establish a documented applicable objective and an evidence-backed benefit. Use `NOT APPLICABLE` for root cause when no defect exists.
- Discard candidates that meet neither gate.

## Status semantics

- `CONFORMING` — an exact applicable requirement/control or documented product objective is available and evidence demonstrates satisfaction; an `ADVISORY` may identify a further improvement with a proven benefit.
- `NONCONFORMING` — exact applicable requirement/control is available and evidence demonstrates violation.
- `INCONCLUSIVE` — relevant evidence exists but is insufficient or conflicting.
- `UNKNOWN` — required evidence is unavailable.
- `NOT APPLICABLE` — control does not apply to the target, with reason.
- `ALIGNED` — framework-level assessment guides the evaluation, but formal conformance cannot be claimed from available normative material. Use it in the standards table, never as an individual-finding status.

Never convert `UNKNOWN` to `NONCONFORMING`.

## Severity semantics

Severity is assigned **after** conformity/evidence assessment.

- `BLOCKER` — demonstrated issue prevents correct release/deployment/publishing/supported use, violates a mandatory critical control, or creates unacceptable security/correctness risk within the declared requirements/threat model.
- `MATERIAL` — demonstrated non-blocking but meaningful operational, security, reliability, compatibility, supply-chain, maintenance, or consumer cost.
- `ADVISORY` — evidence-backed improvement tied to an applicable objective, but current state remains acceptable.

Stylistic preferences, speculative future concerns, arbitrary consistency, and “another project does it differently” are not `ADVISORY`; discard them.

## Final report format

Use this order so readers can understand the outcome before the audit detail:

```markdown
# Repository audit: <target>

## Decision

**<BLOCKED | READY WITH MATERIAL DEBT | READY | INCONCLUSIVE>** — <one-sentence reason>
<Finding counts by severity; mention validation that materially affects the decision.>

## Findings

<Findings ordered BLOCKER, MATERIAL, ADVISORY; use the format below.>

## Scope and product

<Target, purpose, exclusions, product type, consumers, runtime/platform, delivery model,
CI/CD system, critical contracts, evidence sources, and unavailable evidence.>

## Standards and conformity

| Framework / control area  | Applicability and formal claim                          | Result / evidence                              |
| ------------------------- | ------------------------------------------------------- | ---------------------------------------------- |
| <name, version, and area> | <why it applies; CONFORMANCE EVALUATED or ALIGNED> | <status, short reason, and evidence reference> |

## Unknowns and evidence gaps

- <Unavailable evidence> — <decision it prevents>.

## Discarded observations

- <Important candidate> — <why it did not qualify as a finding>.
```

Keep the decision near the top and state exactly one readiness status:

- `BLOCKED` — at least one unresolved BLOCKER.
- `READY WITH MATERIAL DEBT` — no BLOCKER; MATERIAL findings remain.
- `READY` — no unresolved BLOCKER or MATERIAL finding within scope.
- `INCONCLUSIVE` — missing or contradictory evidence prevents a readiness determination.

Write `No qualifying findings.` when there are none. Write `None identified.` under Unknowns when no material evidence gap remains. Omit Discarded Observations when there are no important candidates to explain. Do not repeat a finding's full evidence in the conformity table; use a short evidence reference there. Keep paragraphs short, use bullets for multiple items, and link to exact files, lines, or external sources near the claim they support. Avoid raw evidence dumps and wide tables; the conformity matrix is the only required table.

### Finding format

Use one block per root cause. Keep the title specific and the metadata on one line; omit the quality characteristic only when it does not apply.

```markdown
### [<ID>] <Short, specific title>

`<SEVERITY>` · `<EVALUATION STATUS>` · `<EVIDENCE CONFIDENCE>` · `<QUALITY CHARACTERISTIC>`

- **Standard:** <exact framework and version>
- **Requirement / expected state:** <applicable requirement and expected behavior>
- **Evidence / observed state:** <precise evidence reference and what happens>
- **Impact:** <concrete consequence, or evidence-backed benefit for an advisory>
- **Root cause:** <proven cause, labeled inference/hypothesis, or NOT APPLICABLE>
- **Minimal remediation:** <smallest maintainable corrective action>
- **Affected scope:** <exact file, module, workflow, or provider control>
- **Untouched scope:** <adjacent areas that do not need change>
```

Retain every field above, using `UNKNOWN` or `NOT APPLICABLE` where the contract defines those values. Do not combine the affected and untouched scopes. Keep each value concise; put supporting detail in linked evidence rather than repeating it in prose.

ADVISORY findings do not block `READY`.

## Read-only rule

An audit report does not authorize edits. Do not change code, workflows, settings, branches, releases, labels, permissions, or provider configuration unless the user separately approves an explicit Change Set.
