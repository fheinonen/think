---
name: business-requirements-extraction
description: Use when extracting, eliciting, auditing, or documenting business requirements from source material such as interviews, workshops, notes, tickets, specs, strategy docs, policies, workflows, data, customer feedback, or legacy systems. Produces a structured requirements catalog with goals, stakeholders, scope, acceptance criteria, traceability, priorities, risks, assumptions, and validation questions.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Business Requirements Extraction

Extract business requirements from messy source material and turn them into a
clear, traceable requirements catalog. Use this skill when the user asks to
discover, elicit, reverse-engineer, audit, document, validate, or prioritize
requirements from documents, conversations, product artifacts, code-adjacent
evidence, workflows, data, or stakeholder input.

Do not use this for generic summarization. The output should clarify what
change is needed, why it matters, who needs it, what outcomes it should produce,
and how the requirement can be validated.

## Core Principle

Separate needs, requirements, designs, and tasks. A requirement states a need,
goal, outcome, capability, constraint, or quality the change must satisfy. It is
not automatically a solution design, implementation task, or business rule.

## Grounding

Base the extraction on established business analysis and requirements
engineering practice:

- Start from change, need, value, stakeholder, solution, and context.
- Business requirements describe goals, objectives, and outcomes: why the
  change exists.
- Stakeholder requirements describe stakeholder needs that must be met to
  achieve the business requirements.
- Solution requirements describe capabilities and qualities the solution must
  have. Split them into functional and non-functional requirements.
- Transition requirements describe temporary capabilities or conditions needed
  to move from current state to future state.
- Requirements should be necessary, implementation-free unless constrained,
  unambiguous, consistent, complete enough for the decision at hand, singular,
  feasible, traceable, verifiable, bounded, and prioritized.
- User stories are conversation artifacts. Acceptance criteria define story
  boundaries and help verify and validate that the intended need is met.
- Trace every requirement upward to a business objective or stakeholder need
  and downward to acceptance criteria, tests, designs, backlog items, or open
  follow-up where available.

## Requirement Types

Classify each requirement as one primary type:

- **Business:** goals, objectives, outcomes, value, business problem, success
  measures, scope, or strategic constraints
- **Stakeholder:** needs of a stakeholder group, user role, customer segment,
  operational role, regulator, sponsor, support team, or partner
- **Solution - Functional:** behavior, information, workflow support, data
  capture, reporting, integration, automation, or user interaction
- **Solution - Non-functional:** performance, security, reliability, usability,
  accessibility, privacy, scalability, maintainability, compliance, auditability,
  or other quality conditions
- **Transition:** migration, data conversion, rollout, training, cutover,
  support readiness, business continuity, or temporary coexistence requirements
- **Constraint:** budget, date, regulation, contract, platform, policy, vendor,
  architecture, data residency, or organizational constraint

Tag requirements with domain labels such as onboarding, billing, reporting,
support, compliance, analytics, operations, integration, or admin.

## Workflow

### 1. Scope

Identify:

- product, business area, initiative, or workflow being analyzed
- source material available
- intended use: BRD, PRD, backlog, migration, procurement, QA, audit, discovery,
  stakeholder alignment, or handoff
- current state, future state, and known constraints

If source material is missing, ask for it. If the user points to a repo, folder,
document set, ticket set, transcript, spreadsheet, or workflow, inspect it
directly.

### 2. Source Inventory

Create a compact inventory of reviewed sources. Include documents, transcripts,
tickets, strategy notes, product docs, workflows, code paths, tests, analytics,
reports, data samples, policies, contracts, and stakeholder notes.

Classify evidence:

- **Authoritative:** approved strategy, policy, regulation, contract, BRD/PRD,
  signed-off decision, domain-owner confirmation
- **Stakeholder:** interviews, workshops, feedback, support tickets, sales notes,
  customer success notes, operational observations
- **Behavioral:** product behavior, code, tests, logs, analytics, reports,
  spreadsheets, data exports, existing process artifacts
- **Speculative:** proposals, ideas, assumptions, roadmap guesses, unresolved
  issue comments

### 3. Extract Candidate Requirements

For each candidate, capture:

- requirement statement in business-readable language
- source evidence
- stakeholder or owner
- business objective, need, or outcome it supports
- current-state problem or opportunity
- future-state capability or condition
- scope and boundaries
- priority or urgency, if available
- assumptions, risks, dependencies, and constraints
- acceptance criteria or validation method
- confidence: high, medium, or low
- status: explicit, inferred, contradicted, duplicate, or open question

Prefer atomic requirements. Split compound statements when each part can be
prioritized, tested, or delivered independently.

### 4. Normalize

Improve each requirement:

- make it singular and testable
- remove solution design unless the design is a real constraint
- replace vague terms with measurable criteria where evidence supports it
- define actors, events, data, thresholds, dates, jurisdictions, and conditions
- distinguish requirement from business rule, design decision, task, and idea
- connect user stories to the requirement they support
- write acceptance criteria in plain language or Given/When/Then form when
  useful

For agile output, check story candidates against INVEST: independent,
negotiable, valuable, estimable, small, and testable.

### 5. Analyze And Prioritize

Check the set, not just individual requirements:

- traceability to business objectives and stakeholder needs
- conflicts, overlaps, duplicates, and scope creep
- missing stakeholder groups, scenarios, data, integrations, operational flows,
  compliance obligations, and non-functional requirements
- feasibility, risk, dependencies, sequencing, and transition needs
- validation path: inspection, demonstration, test, analysis, stakeholder
  review, data query, or operational trial

Prioritize with the method that fits the context: MoSCoW, weighted scoring,
value/risk/effort, regulatory deadline, dependency order, or explicit
stakeholder ranking. Do not invent priority; label it unknown when missing.

## Output Format

Default to a requirements catalog:

```markdown
# Business Requirements: <domain or initiative>

## Scope
<what was reviewed, intended use, current state, future state, and exclusions>

## Source Inventory
| Source | Evidence Level | Notes |
|---|---|---|

## Stakeholders
| Stakeholder | Need / Interest | Role in Validation |
|---|---|---|

## Objectives And Success Measures
| ID | Objective / Outcome | Measure | Source | Confidence |
|---|---|---|---|---|

## Requirements Catalog
| ID | Type | Requirement | Rationale / Need | Priority | Source | Confidence | Validation |
|---|---|---|---|---|---|---|---|
| REQ-001 | <type> | <singular requirement> | <why it matters> | <priority/unknown> | <source> | <high/medium/low> | <acceptance/test/review> |

## Acceptance Criteria
| Requirement ID | Criteria |
|---|---|

## Traceability
| Requirement ID | Business Objective / Stakeholder Need | Downstream Artifact |
|---|---|---|

## Conflicts And Duplicates
| Topic | Issue | Sources | Recommended Resolution |
|---|---|---|---|

## Assumptions, Risks, And Dependencies
| Item | Type | Impact | Suggested Owner |
|---|---|---|---|

## Open Questions
| Question | Why It Matters | Suggested Owner |
|---|---|---|
```

Use a story map, journey map, context diagram, process model, or data model only
when it clarifies requirements that would otherwise be hard to understand.

## Quality Bar

A good extraction is:

- value-linked: every requirement has a reason to exist
- stakeholder-grounded: affected groups and validation owners are visible
- singular: each requirement can be assessed independently
- implementation-aware but not implementation-led
- verifiable: acceptance criteria or validation method is clear
- traceable: source and upstream/downstream links are recorded
- prioritized honestly: unknown priority stays unknown
- complete enough for the next decision, without pretending discovery is done

## Common Mistakes

- confusing business requirements with solution design
- treating every stakeholder wish as a requirement
- omitting non-functional, transition, data, integration, and operational needs
- documenting user stories without the underlying business objective
- inventing acceptance criteria not supported by evidence
- losing source traceability
- merging multiple requirements into one broad statement
- forcing priority when the source material does not support it
- treating requirements as final when they still need stakeholder validation

## Online References

These sources ground the method. Use them for principles, not as rigid ceremony:

- IIBA, *Global Business Analysis Core Standard*
  https://www.iiba.org/globalassets/standards-and-resources/core-standard/iiba-core-standard.pdf
- IIBA, *The Business Analysis Standard*
  https://www.iiba.org/knowledgehub/the-business-analysis-standard/
- IIBA, *Verify Requirements*
  https://www.iiba.org/knowledgehub/business-analysis-body-of-knowledge-babok-guide/7-requirements-analysis-and-design-definition/7-2-verify-requirements/
- ISO/IEC/IEEE 29148 overview, *Requirements Engineering*
  https://www.cwnp.com/req-eng/
- Agile Alliance and IIBA, *Agile Extension to the BABOK Guide*
  https://www.agilealliance.org/wp-content/uploads/2017/08/AgileExtension_V2-Member-Copy.pdf
- Agile Alliance, *INVEST*
  https://agilealliance.org/glossary/invest/
