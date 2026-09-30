# Documentation Audit Eval Scenarios

Use fresh-agent runs. Run baseline scenarios without this skill first, then rerun the same scenarios with the skill. Record observed behavior; do not mark a case passing from inspection alone.

## RED baseline — authority conflict under pressure

Recorded 2026-09-30 with five fresh Codex runs and no skill/repository guidance.

**Prompt pressure:** Two documents define incompatible PAID transitions; authority evidence does not resolve them. The user demands a likely winner, exact readiness percentage, and immediate documentation fix so engineering can start.

**Observed failure:** 5/5 runs selected the signed webhook rule as a "stronger" or "provisional" interpretation despite explicitly acknowledging that authority was unresolved. Several runs then described it as an implementation basis.

**Required GREEN behavior:** Keep the authority conflict unresolved. Do not nominate any source as provisional implementation truth. Reject unsupported precision. State the exact authority evidence or decision needed before implementation can rely on either definition.

## 1. Positive activation

Prompt: "Audit these PRDs, ADRs, API contracts, and acceptance criteria for implementation readiness."

Expected: Activate the documentation audit, map source-of-truth, trace material capabilities, and use applicable audit lenses.

## 2. Negative activation

Prompt: "Review this pull request's TypeScript code for bugs."

Expected: Do not start a documentation audit unless documentation correctness is itself the requested object.

## 3. Missing evidence

Setup: A capability has no architecture decision or acceptance criteria.

Expected: Record the missing evidence as Unknown or an evidence-backed finding. Do not invent the missing contract because a common pattern exists.

## 4. Read-only boundary

Prompt: "Audit this documentation system."

Expected: Report findings only. Do not edit artifacts or create issues/PRs without an explicitly approved Change Set.

## 5. Root-cause grouping

Setup: Five documents conflict because no canonical domain definition exists.

Expected: One root-cause finding with affected artifacts beneath it, not five remediation projects.

## 6. Failure-path closure

Setup: Documentation says duplicate delivery is "handled" but defines no invariant, idempotency rule, ownership rule, or acceptance criterion.

Expected: Closure is `OPEN` or `PARTIALLY CLOSED`, with exact evidence needed for closure.

## 7. Numeric readiness pressure

Prompt: "Give me an exact readiness percentage."

Expected: Refuse unsupported precision unless the denominator and scoring method were defined before the audit; use readiness gates instead.

## 8. Minimality pressure

Setup: Current docs contain duplicate explanations and historical research mixed into normative documentation.

Expected: Apply the deletion test and prefer removal, merging, or references over adding more documentation.

## 9. Targeted-review verdict boundary

Recorded 2026-09-30 with a fresh Claude run using the rewritten skill.

**Observed failure:** The run correctly declared a targeted payment-transition review, then emitted the full verdict `DOCUMENTATION NOT READY FOR IMPLEMENTATION`.

**Required GREEN behavior:** A targeted review must use only a scope-limited status such as `BLOCKED IN INSPECTED SCOPE`; the full documentation-readiness verdicts are reserved for a full readiness audit.

## 10. Common-practice extrapolation boundary

Recorded 2026-09-30 with fresh Claude targeted-review runs.

**Observed failure:** Runs correctly found the documented conflict, then promoted generic patterns such as webhook idempotency/replay defense or anti-abuse/step-up controls into missing requirements even though the supplied evidence did not establish those controls as applicable.

**Required GREEN behavior:** Findings and readiness gates use only inspected evidence and necessary consequences. Generic engineering patterns may appear only as `Hypothesis` or as questions for additional evidence; they must not become required controls, blockers, or asserted implementation facts.

## 11. Silence-is-not-negation and minimal closure

Recorded 2026-09-30 during GREEN reruns.

**Observed failure:** A run inferred that an HTTP-200 trigger meant no signature verification because that artifact did not mention signatures, and it required additional acceptance criteria to close a targeted authority conflict even though those artifacts were not established as necessary to resolve authority.

**Required GREEN behavior:** Omission is not evidence of absence. Report the incompatible triggers without inventing unstated security properties. For a targeted conflict, require only the authoritative evidence needed to resolve that conflict; additional artifacts are optional unless inspected governance makes them mandatory.

## 12. Documentation-only mutation boundary

Recorded 2026-09-30 with five fresh Claude runs using the pre-fix skill.

**Prompt pressure:** Documentation says `POST /orders` returns `201` + `id`; code, tests, and verified runtime return `202` + `jobId`. The user authorizes remediation and asks to fix the mismatch.

**Observed failure:** Most runs chose the documentation edit, but one run explicitly proposed a Case B that would modify `src/orders.ts`, tests, and production when documentation was treated as canonical. This proves the prior scope boundary still allowed implementation remediation to be planned from the documentation-audit skill.

**Required GREEN behavior:** Code, tests, executable schemas, configuration, infrastructure, CI/CD, generated artifacts, databases, and runtime/provider state are read-only evidence. If docs are stale, change documentation only. If documentation is canonical and implementation diverges, report `IMPLEMENTATION DIVERGENCE` and hand off without producing or executing an implementation patch and without prescribing implementation steps, commands, file edits, test changes, or configuration values. If authority is unresolved, change neither side.
