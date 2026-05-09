---
name: delivery-risk-review
description: Use when reviewing a project plan, status update, delivery brief, RAID log, meeting notes, schedule, backlog, or stakeholder narrative to find hidden project delivery risks, weak assumptions, missing owners, dependency gaps, decision latency, scope drift, readiness issues, unclear acceptance criteria, and control actions.
---

# Delivery Risk Review

Review project material for delivery threats before they become issues. Use this
skill when the user wants a rigorous but practical risk review of a plan,
status dump, project brief, schedule, meeting notes, or delivery situation.

## Practice Basis

Ground the review in broadly used project risk and control practice:

- PMI risk management guidance treats risk as uncertain events or conditions
  that can affect objectives, and emphasizes identification, analysis, response
  planning, ownership, triggers, and ongoing control.
- PMI communications and stakeholder guidance emphasizes tailoring information
  to stakeholder needs and communicating risks that are relevant, actionable,
  and timely.
- PRINCE2 principles emphasize defined roles, continued business justification,
  management by stages, management by exception, product focus, and tailoring.
  Use these principles to test whether risk controls, escalation thresholds,
  decision rights, and deliverable acceptance are clear.
- APM project controls focus on managing scope, time, cost, risk, and change.
  Use these as the main dimensions for assessing whether the project can be
  steered.
- RAID practice separates risks, assumptions, issues, and dependencies so the
  response matches the type of delivery threat.

Do not turn every uncertainty into a red risk. Distinguish active issues,
credible risks, assumptions to validate, and ordinary unknowns.

## Source Anchors

Use these sources as the underlying practice references when interpreting the
workflow:

- PMI Standard for Risk Management:
  `https://www.pmi.org/standards/risk-management`
- PMI risk ownership and triggers article:
  `https://www.pmi.org/learning/library/risk-analysis-project-management-7070`
- PMI risk communication article:
  `https://www.pmi.org/learning/library/explaining-risk-project-stakeholders-2206`
- PMI PMBOK Guide overview:
  `https://www.pmi.org/pmbok-guide-standards/foundational/pmbok`
- PeopleCert PRINCE2 7 syllabus:
  `https://peoplecert.jp/doc/PRINCE2_Agile_FND_Syllabus_EN_v2_0.pdf`
- APM project controls overview:
  `https://www.apm.org.uk/resources/what-is-project-management/what-is-project-controls/`

## Workflow

### 1. Define The Review Target

Identify:

- project or work package being reviewed
- material reviewed
- project phase or milestone
- review purpose: planning, health check, steering, recovery, go/no-go,
  pre-cutover, handover, or escalation
- risk tolerance and deadline pressure if available
- escalation thresholds or stage tolerances if available
- delivery objectives that would be affected by risk

If the user only provides rough notes, review them anyway and state the evidence
limits.

### 2. Scan For Delivery Weaknesses

Look for risk signals across these dimensions:

- **Scope:** ambiguous boundaries, unpriced extras, acceptance criteria gaps,
  uncontrolled change, unclear exclusions.
- **Ownership:** missing accountable owner, split accountability, owner without
  authority, unassigned actions.
- **Schedule:** optimistic dates, missing lead time, dependency compression,
  decision deadlines not tied to milestones.
- **Dependencies:** hidden prerequisites, external teams, vendors, customer
  readiness, procurement, environment access, data, approvals.
- **Decisions:** pending decisions, unclear decision owner, no decision date,
  unresolved tradeoffs, repeated deferrals.
- **Resources:** role gaps, overallocated specialists, single points of failure,
  unavailable approvers, unclear escalation path.
- **Quality:** weak test plan, undefined done, missing acceptance evidence,
  rollback or contingency gaps.
- **Transition:** handover, training, support model, documentation, monitoring,
  operational readiness, adoption.
- **Commercial and governance:** budget, contract scope, change control, risk
  acceptance, sponsor alignment, business justification.
- **Communication:** status ambiguity, stakeholder mismatch, surprises,
  repeated topics without closure.
- **Controls:** missing risk trigger, no residual risk view, mitigation without
  owner, response not proportionate to impact, tolerance breach without
  exception path.

### 3. Classify Findings

For each finding, classify it as:

- **Issue:** already happening and affecting delivery.
- **Risk:** plausible future event or condition that could affect delivery.
- **Assumption:** unverified belief the plan depends on.
- **Dependency:** external prerequisite or handoff.
- **Decision:** choice needed to unblock or de-risk delivery.
- **Control gap:** missing owner, trigger, mitigation, contingency, or evidence.

Use severity based on delivery consequence, not emotional intensity.

### 4. Recommend Controls

For each material finding, propose one concrete control:

- accept with named owner and trigger
- avoid by changing scope, sequence, or approach
- reduce with mitigation, validation, prototype, review, or added capacity
- transfer by contract, vendor commitment, or formal dependency agreement
- escalate through a decision request or governance forum
- convert into an action, decision, or assumption test
- define a trigger, threshold, contingency, or fallback decision point

Prefer small controls that create evidence quickly. Do not recommend process
ceremony unless it directly reduces delivery risk.

## Output Format

Default to this structure:

```markdown
# Delivery Risk Review: <project / milestone>

## Review Context
<sources, phase, review purpose, confidence>

## Risk Posture
<short summary of overall delivery confidence and the main threat pattern>

## Top Findings
| ID | Type | Finding | Evidence | Impact | Severity | Owner | Recommended Control |
|---|---|---|---|---|---|---|---|

## Assumptions To Validate
| Assumption | Why It Matters | Validation Action | Owner | Needed By |
|---|---|---|---|---|

## Decisions Needed
| Decision | Decision Owner | Options / Tradeoff | Needed By | Impact If Delayed |
|---|---|---|---|---|

## Dependency Controls
| Dependency | External Party | Current Weakness | Control | Trigger / Date |
|---|---|---|---|---|

## Recommended Next Actions
| Action | Owner | Due | Risk Reduced |
|---|---|---|---|
```

For a fast response, lead with the top 3-5 findings and immediate controls.

## Quality Bar

Before finalizing, check:

- Is each finding tied to evidence or labeled as inferred?
- Is each risk separate from issues, assumptions, dependencies, and decisions?
- Does each material risk have an owner and practical control?
- Does each significant risk have a trigger or condition that tells the team
  when to act?
- Are decision deadlines tied to delivery impact?
- Are recommendations specific enough to act on in the next project meeting?
