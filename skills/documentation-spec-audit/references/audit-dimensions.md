# Audit Dimensions

Use all fourteen dimensions when the task is a full documentation audit. Combine evidence gathering where possible; do not manufacture fourteen separate passes if one traversal can support several dimensions.

## 1. Completeness Audit

Question: What necessary information is absent?

Trace:
Business Goal
→ Capability
→ Requirement
→ User Journey / Flow
→ Domain Rule
→ Architecture
→ Integration Contract
→ Repository Ownership
→ Data
→ Failure Handling
→ Acceptance Criteria

Look for missing:
- capabilities
- flows
- states and transitions
- error cases
- ownership
- integration behavior
- relevant security constraints
- operational/recovery behavior
- acceptance criteria
- required assumptions

Do not infer that something is required merely because it is industry-common.

## 2. Consistency Audit

Question: Do sources describing the same concept agree?

Compare:
- terminology and naming
- state models
- responsibilities
- product behavior
- architecture
- data ownership
- repository ownership
- interfaces
- security rules
- integration behavior
- failure behavior

Detect semantic drift.

Do not automatically choose a winner when sources disagree. Identify the canonical source or flag unresolved conflict.

## 3. Traceability Audit

Question: Can requirements be followed downstream to implementation intent and proof?

Typical path:
Business Goal
→ Capability
→ Requirement
→ User Flow
→ Domain Rule
→ Architecture
→ Service
→ Repository
→ Contract
→ Acceptance Criterion / Test

Identify:
- requirement without downstream specification
- user flow unsupported by architecture
- architecture decision without real constraint
- test without requirement
- service without capability justification

## 4. Source-of-Truth Audit

Question: Where is each important concept authoritatively defined?

Evaluate:
- product requirement
- business rule
- domain model
- terminology
- API contract
- architecture invariant
- repository ownership
- provider constraint
- security rule
- deployment behavior

Find:
- competing canonicals
- accidental copies
- stale mirrors
- unclear authority
- obsolete references

Prefer references over duplicate normative copies.

## 5. Duplication / Noise Audit

Question: Does this content materially help a consumer make a decision or implement correctly?

Find:
- repeated explanations
- unnecessary background
- historical research mixed into current spec
- duplicated architecture descriptions
- policy text with no consumer
- obvious statements
- audit-only concerns exposed to engineers without need
- uncertainty turned into permanent policy

Deletion test:

> If this content disappeared, what concrete implementation or decision would become impossible or unsafe?

If no meaningful answer exists, mark as a noise candidate.

## 6. Ambiguity Audit

Question: Could two competent engineers implement materially different systems while both believing they followed the spec?

Inspect vague words such as:
- should
- may
- normally
- appropriate
- secure
- scalable
- robust
- flexible
- standard
- optimized
- as needed
- if necessary

For blocking ambiguity state:
- competing interpretations
- downstream difference
- exact missing decision

## 7. Contradiction Audit

Question: Which statements cannot all be true simultaneously?

Examples:
- two systems own the same canonical entity
- incompatible state transitions
- conflicting API behavior
- conflicting retention rules
- incompatible authentication assumptions
- conflicting repository boundaries
- mutually exclusive product rules

Do not hide a contradiction with an explanatory paragraph. Resolve authority.

## 8. Boundary / Ownership Audit

Question: Does every material responsibility have one defensible owner?

Audit:
- capability
- domain
- service
- repository
- database
- API
- event
- worker/job
- external integration

Find:
- overlap
- orphan responsibility
- shared mutable ownership
- hidden cross-repo coupling
- duplicate domain logic
- global docs defining local internals
- local docs redefining global invariants

## 9. Implementation-Readiness Audit

Question: Can an engineer implement each major capability without inventing a material decision?

Require enough clarity around:
- purpose
- inputs / outputs
- state / transitions
- invariants
- ownership
- dependencies
- data
- permissions
- failure behavior
- retry/idempotency when applicable
- integration boundaries
- acceptance criteria

Do not demand irrelevant implementation detail.

## 10. Blind Reader Audit

Question: Can an experienced engineer with no historical context reconstruct the intended system from canonical docs alone?

Reconstruct:
- product
- capabilities
- flows
- domains
- architecture
- repo boundaries
- source-of-truth
- integrations
- invariants
- failures

Any necessary guess is evidence of a documentation gap or ambiguity.

## 11. Adversarial / Red Team Audit

Question: How can literal compliance with the spec still produce a bad system?

Attack:
- undocumented assumptions
- retries and duplicate delivery
- partial success
- timeouts
- concurrent state changes
- out-of-order events
- authorization boundaries
- ownership conflicts
- financial/data consistency
- reconciliation
- provider behavior changes
- hidden coupling
- failure recovery
- contradictory state transitions
- implementation dead ends
- invalid environmental assumptions
- impossible operational behavior

## 12. Blue Team Audit

Question: Does existing documentation contain an explicit control for each valid Red path?

Controls may include:
- invariant
- validation
- authorization
- ownership boundary
- idempotency
- retry contract
- state machine
- reconciliation
- timeout rule
- recovery rule
- explicit rejection behavior
- acceptance criterion / test

Classify:
- already controlled
- partially controlled
- uncontrolled
- cannot determine

Do not invent controls during audit.

## 13. Cross-Layer Audit

Question: Does each major feature connect cleanly through every documentation layer?

Trace vertically:
Business Need
→ Product Requirement
→ User Journey
→ Domain Rule
→ Architecture
→ Data / Contract
→ Repository Ownership
→ Implementation Expectation
→ Acceptance Criterion

Identify broken edges.

## 14. Reverse Trace Audit

Question: Does each implementation-facing construct have sufficient upstream justification?

Trace:
Repository / Service / Component / Integration / Schema / Job / Policy
→ Architecture reason
→ Requirement
→ Capability
→ Business / Product Need

Candidates lacking justification may represent:
- accidental complexity
- obsolete architecture
- premature abstraction
- historical residue
- dead documentation
- unjustified infrastructure

Do not remove automatically; establish evidence first.
