# Think

This repository contains local skills for structured reasoning and coaching:

- `think` for turning a messy thought dump into a usable breakdown
- `decision-system` for challenging a decision premise, stabilizing the frame,
  making a recommendation, and optionally producing a decision memo
- `systemic-thinking` for analyzing a complex problem with explicit structure
- `engineering-judgment-coaching` for helping an engineer strengthen their
  reasoning and recommendation quality through guided coaching
- `business-requirements-extraction` for extracting traceable business,
  stakeholder, solution, transition, and constraint requirements
- `business-rules-extraction` for extracting auditable business rules from
  code, specs, policies, workflows, tickets, data, or conversations
- `business-decision-discovery` for discovering operational business decisions,
  input data, outcomes, decision tables, and validation scenarios

They solve adjacent but different stages of the same general problem. `think`
is for getting your thoughts out and organized. `decision-system` is for
deciding what to do after challenging whether the stated premise is even the
right one. `systemic-thinking` is for disciplined analysis once the problem
needs a more formal model. `engineering-judgment-coaching` is for improving how
an engineer reasons through a recommendation, not just the quality of the
analysis itself. `business-requirements-extraction` is for turning messy
stakeholder and product evidence into traceable requirements.
`business-rules-extraction` is for turning operational or implementation
evidence into explicit, source-backed rules. `business-decision-discovery` is
for grouping requirements and rules around the business decisions they support:
the question being answered, the input data needed, the possible outcomes, the
decision logic, and the validation scenarios.

## Install

```bash
npx skills add fheinonen/think
```

## Which Skill To Use

### Requirements, Rules, And Decisions

| Thing | Question It Answers | Example |
|---|---|---|
| Requirement | What does the business need? | Route customer requests correctly |
| Rule | What policy or constraint applies? | Suspended accounts require account review |
| Decision | What outcome must be chosen? | Should this request be self-served, handled normally, escalated, or reviewed? |
| Decision table | How is the outcome chosen? | If account is suspended, route to account review |
| Test scenario | How do we verify it? | Suspended account request routes to account review |

### Use `think` when

- you have too many threads open at once
- you want to dump thoughts quickly without structuring them first
- you need the AI to identify threads, open questions, and action items
- you want to keep refining and save the session as markdown

### Use `systemic-thinking` when

- you want rigorous, explicitly structured analysis of the problem, models,
  uncertainties, synthesis, and next steps
- the problem has multiple interacting parts, actors, or constraints
- the boundaries are unclear or several interpretations are plausible
- you need assumptions, unknowns, and uncertainty separated explicitly

### Use `decision-system` when

- you need to make, defer, split, or reject a decision
- the stated premise may be wrong or too narrow
- you want the agent to challenge the goal, framing, timing, constraints, and
  assumptions before comparing options
- you need explicit decision criteria, tradeoffs, reversibility, confidence,
  and decision triggers
- you want a recommendation that can later be turned into a decision memo

### Use `engineering-judgment-coaching` when

- you want to mentor an engineer through a decision, investigation, or design
  judgment
- you want critique and revision, not just an answer
- you want to strengthen framing, tradeoff awareness, prioritization, and
  recommendation quality

### Use `business-rules-extraction` when

- you need to reverse-engineer business rules from code, specs, policies,
  tickets, workflows, spreadsheets, data, or stakeholder notes
- you want a source-backed catalog of eligibility, validation, calculation,
  workflow, authorization, compliance, data, notification, or decision rules
- you need to separate explicit rules from inferred behavior, contradictions,
  exceptions, and open validation questions
- you want rules that can drive implementation, QA, migration, audit, or
  stakeholder review

### Use `business-decision-discovery` when

- you need to discover the business decisions that requirements and rules
  support
- you want to group rules around decision questions such as approval route,
  eligibility, pricing, classification, routing, assignment, or calculation
- you need to identify input data, possible outcomes, default behavior, and
  exception paths
- you want decision tables or ordered logic that show how rules and data produce
  outcomes
- you want validation scenarios that can drive QA, workflow automation, or
  stakeholder review

### Use `business-requirements-extraction` when

- you need to extract business, stakeholder, solution, transition, or constraint
  requirements from interviews, workshops, tickets, specs, strategy docs,
  workflows, data, feedback, or legacy systems
- you want source-backed requirements with objectives, stakeholders, rationale,
  priority, acceptance criteria, traceability, risks, assumptions, and open
  questions
- you need to separate needs from designs, tasks, business rules, ideas, and
  unsupported stakeholder wishes
- you want requirements that can drive a BRD, PRD, backlog, procurement, QA,
  migration, audit, or stakeholder review

## Side-by-Side Workflow

### `think`

`think` helps you get messy thoughts out of your head and into a useful shape.

The workflow is simple:

1. Dump everything in one go.
2. The skill organizes it into a structured breakdown.
3. Add more thoughts, dig deeper on a thread, or reframe it.
4. Save when it looks right.

The output focuses on:

- a clear problem statement
- distinct threads
- open questions
- concrete action items

Sessions are stored as markdown files in `~/.thinking-sessions/`.

Example:

```text
/think

I need to migrate a client system next month. The database sync might be the
real bottleneck. We only have a 4 hour maintenance window. I am worried about
rollback if DNS cutover fails. Running both environments in parallel could get
expensive. I also do not know who owns the final go/no-go call.
```

### `systemic-thinking`

`systemic-thinking` is for deeper analysis when the problem needs explicit
reasoning structure.

The skill works in two modes:

1. Analyze now, if missing context would not materially change the analysis.
2. Clarify first, if missing context would change the plausible models,
   eliminations, or recommended next steps.

If your prompt already contains enough context, the skill analyzes it directly
instead of re-asking for the problem.

It then produces a structured analysis covering:

- problem restatement
- small local notes
- ontological, epistemic, and morphological analysis
- MECE structure and semiotic analysis
- eliminated options, plausible models, open questions, synthesis, and next
  steps

Use it when you want the agent to reason carefully rather than just organize a
brain dump.

Systemic-thinking sessions can also be saved, listed, continued, and resolved.
They are stored separately in `~/.thinking-sessions/systemic-thinking/`.

When continuing a saved session, the skill first lets you inspect the existing
analysis as-is, then revise it only if you add new context or request changes.

### `decision-system`

`decision-system` is for decisions where the premise itself may need to be
rethought before options are compared.

The workflow is:

1. Adversarial exploration: challenge the stated decision, goal, timing,
   constraints, owner, and assumptions.
2. Frame stabilization: define the actual decision, criteria, stakes,
   unknowns, reversibility, and what would make the decision good.
3. Option generation: create a visible option set, including non-obvious paths
   like doing nothing, deferring, experimenting, or changing the premise.
4. Evaluation: compare viable options against criteria, risks, reversibility,
   opportunity cost, uncertainty, and context fit.
5. Recommendation first: choose a path, reject alternatives, state risks,
   confidence, decision triggers, and the next action.
6. Decision memo second: convert the reasoning into a durable artifact only
   after the recommendation is clear.
7. Review later: evaluate the decision process separately from the outcome.

Use it when you want a decision system, not just a thinking aid. The skill can
recommend acting, delaying, gathering evidence, splitting the decision, changing
the objective, doing nothing, or rejecting the original premise.

Decision-system sessions can be saved, listed, continued, and reviewed. They
are stored separately in `~/.thinking-sessions/decision-system/`.

The method is anchored in established decision practices:

- Decision Quality: appropriate frame, creative alternatives, reliable
  information, clear values and tradeoffs, sound reasoning, and commitment to
  action
- Kepner-Tregoe Decision Analysis: must-have constraints, weighted wants,
  alternative comparison, and risk evaluation
- WRAP: widen options, reality-test assumptions, attain distance, and prepare
  to be wrong
- OODA and Cynefin: orient to context and adapt the decision style to clear,
  complicated, complex, chaotic, or confused situations
- RAPID and DACI: clarify decision ownership and stakeholder roles
- Premortem thinking: imagine failure before committing
- One-way/two-way door thinking: scale rigor to reversibility
- Decision journaling: record reasoning so decision quality can be reviewed
  separately from outcome quality

### `engineering-judgment-coaching`

`engineering-judgment-coaching` helps an engineer improve how they reason.

The workflow is:

1. State the situation, reasoning, and recommendation.
2. Get critique on the biggest reasoning gaps.
3. Revise the reasoning.
4. Defend a clearer recommendation.
5. End with one coaching takeaway for next time.

### `business-rules-extraction`

`business-rules-extraction` turns messy source material into a structured rule
catalog.

The workflow is:

1. Define the extraction scope and intended use.
2. Inventory reviewed sources such as code paths, specs, policies, tickets,
   tests, workflows, spreadsheets, data, or interviews.
3. Extract candidate rules with evidence, context, inputs, outputs, actors,
   exceptions, and confidence.
4. Normalize rules into atomic, testable business language.
5. Flag contradictions, inferred behavior, undocumented exceptions, and open
   validation questions.
6. Produce a catalog with definitions, rule IDs, decision logic, contradictions,
   open questions, and a validation plan.

Use it when the main risk is losing, misreading, or over-trusting domain logic
that lives across implementation details and human process.

### `business-decision-discovery`

`business-decision-discovery` turns requirements and rules into operational
decision models.

The workflow is:

1. Define the source material and intended use.
2. Find candidate decisions where the business chooses an outcome.
3. Name each decision as a business question or outcome selection.
4. Identify possible outcomes and required input data.
5. Link supporting rules to each decision.
6. Model the logic with a decision table, ordered rule list, formula, state
   transition table, or compact pseudocode.
7. Flag missing inputs, missing defaults, unclear precedence, overlapping rules,
   contradictions, and unhandled cases.
8. Generate validation scenarios for normal, boundary, exception, conflict, and
   default cases.

Use it when a rule catalog is useful but still does not show how the business
actually chooses an outcome.

Example:

```text
Requirement:
Route customer requests to the right handling path.

Rules:
- Requests with missing required documents need more information.
- Suspended accounts require account review.
- High-urgency requests require priority handling.

Decision:
Determine request handling route.

Inputs:
- request type
- account status
- urgency
- document completeness

Outcomes:
- self-service
- standard handling
- priority handling
- account review
- request more information
```

### `business-requirements-extraction`

`business-requirements-extraction` turns messy stakeholder, product, and
operational evidence into a structured requirements catalog.

The workflow is:

1. Define scope, intended use, current state, future state, and constraints.
2. Inventory source evidence such as interviews, workshops, tickets, specs,
   strategy docs, workflows, feedback, analytics, code-adjacent evidence, and
   legacy process artifacts.
3. Extract candidate requirements with stakeholder, source, objective,
   rationale, priority, assumptions, risks, dependencies, and confidence.
4. Normalize requirements so they are singular, testable, traceable, and not
   confused with design decisions or implementation tasks.
5. Add acceptance criteria or validation methods.
6. Flag conflicts, duplicates, missing requirement types, and open questions.

Use it when the main risk is building from unclear needs, unsupported
stakeholder requests, or requirements with weak traceability.

## Common Prompts

### `think`

- "I need to think through something"
- "Expand thread 2"
- "Give me a different framing"
- "Continue the migration session"
- "List my thinking sessions"

### `systemic-thinking`

- "Use systemic thinking to analyze this migration plan"
- "Break this problem into local notes and map the unknowns"
- "Analyze this using ontological, epistemic, and morphological lenses"
- "Compare the plausible models and eliminate weak ones"
- "Save this systemic-thinking session"
- "List my systemic-thinking sessions"
- "Continue the migration analysis session"
- "Open the migration analysis session and show me the current model"
- "Mark the migration analysis session as resolved"

### `decision-system`

- "Help me decide whether to rebuild this dashboard"
- "Challenge the premise of this plan before we choose an option"
- "Use the decision system on this hiring decision"
- "Should we do this now, defer it, or change the objective?"
- "Turn this into a decision memo after making the recommendation"
- "List my saved decisions"
- "Continue the dashboard decision"
- "Review the dashboard decision outcome"

### `engineering-judgment-coaching`

- "Coach me through this decision like a senior engineer mentoring another engineer"
- "Critique my reasoning and help me strengthen it before giving me the answer"
- "Push back on my reasoning and make me defend a recommendation"
- "Help me improve how I think through this, not just solve it for me"

### `business-rules-extraction`

- "Extract the business rules from this billing module"
- "Reverse-engineer the eligibility rules from these tickets and specs"
- "Audit this workflow and produce a rule catalog with contradictions"
- "Turn these policy notes into testable business rules"
- "Find the validation, authorization, and calculation rules in this codebase"

### `business-decision-discovery`

- "Discover the business decisions supported by these routing rules"
- "Turn this rule catalog into decision tables and validation scenarios"
- "Find the inputs, outcomes, and rules for each operational decision"
- "Model how these eligibility rules produce approve, review, or reject outcomes"
- "Group these business rules by the operational decisions they support"

### `business-requirements-extraction`

- "Extract the business requirements from these interview notes"
- "Turn this discovery transcript into a requirements catalog"
- "Audit these tickets for missing acceptance criteria and traceability"
- "Extract stakeholder, solution, and transition requirements from this migration plan"
- "Separate requirements from designs, tasks, assumptions, and business rules"

## License

MIT
