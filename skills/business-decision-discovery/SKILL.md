---
name: business-decision-discovery
description: Use when discovering, extracting, modeling, or documenting operational business decisions from requirements, rules, policies, workflows, code, specs, tickets, data, or stakeholder notes. Produces decision catalogs, decision tables, input data, outcomes, rules used, gaps, conflicts, and validation scenarios.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Business Decision Discovery

Discover operational business decisions from messy source material and model
how requirements, rules, and data produce business outcomes. Use this skill
when the user needs to find the decisions hidden inside requirements, rules,
policies, workflows, code, specs, tickets, data, or stakeholder notes.

Do not use this for broad strategy decisions or generic decision coaching. The
output should make business logic visible: decision question, input data,
outcomes, supporting rules, gaps, conflicts, and validation scenarios.

## Core Principle

Requirements, rules, and decisions are different layers:

- **Requirement:** what the business needs
- **Rule:** what policy or constraint applies
- **Decision:** what outcome must be chosen from rules and data
- **Decision table:** how input combinations map to outcomes
- **Test scenario:** how the decision is verified

Use this model:

```text
Requirement
  -> Decision
  -> Rules + Data
  -> Outcome
```

Example:

```text
Requirement:
Route customer requests to the right handling path.

Decision:
Determine request handling route.

Data:
Request type, customer tier, account status, urgency, required documents.

Rules:
- If required documents are missing, request more information.
- If the account is suspended, route to account review.
- If urgency is high, escalate to priority handling.

Outcome:
Self-service, standard handling, priority handling, account review, or request
more information.
```

## Grounding

Base the discovery on lightweight decision modeling practice:

- Model decisions as business questions that produce outcomes.
- Treat rules as ingredients used by decisions, not as the final artifact.
- Identify input data explicitly before writing decision logic.
- Use decision tables when several input conditions map to different outcomes.
- Link decisions back to requirements or business needs where evidence exists.
- Keep the model understandable to business stakeholders; do not require DMN
  XML, FEEL, or formal notation unless the user asks.

## Decision Types

Look for decisions where the business chooses an outcome:

- **Approval:** approve, reject, hold, or escalate
- **Routing:** send to a team, queue, workflow, channel, or reviewer
- **Eligibility:** eligible, ineligible, conditionally eligible, exception
- **Classification:** assign category, risk band, segment, tier, or status
- **Commercial terms:** choose plan, tier, rate, adjustment, or entitlement
- **Prioritization:** rank, schedule, expedite, defer, or deprioritize
- **Calculation:** compute score, amount, date, allocation, or entitlement
- **Assignment:** assign owner, approver, responsibility, territory, or account
- **Notification:** decide who is informed, when, and through which channel
- **Permission:** permit, block, require review, or require override

## Workflow

### 1. Scope

Identify:

- domain, product area, workflow, or process being analyzed
- source material available
- intended use: implementation, QA, workflow automation, audit, migration,
  stakeholder validation, documentation, or handoff
- whether requirements or rules have already been extracted

If the user has not provided source material, ask for it. If the user points to
a repo, folder, document, ticket set, transcript, spreadsheet, or workflow,
inspect it directly.

### 2. Find Candidate Decisions

Search source material for places where an outcome is chosen. Common signals:

- approve, reject, block, permit, route, escalate, review, assign, classify
- eligible, required, optional, allowed, prohibited, exception, override
- thresholds, risk levels, status checks, dates, jurisdictions, roles, tiers
- workflow branches, state transitions, validation outcomes, error outcomes
- calculations that determine a business result

Name each decision as a clear business question or outcome selection:

- "Select customer request handling route"
- "Is the user eligible for self-service access?"
- "Calculate service priority score"
- "Select onboarding review path"

Avoid naming a decision as a rule. "Suspended accounts require account review"
is a rule. "Determine request handling route" is the decision.

### 3. Identify Outcomes

For each decision, capture the possible outcomes:

- normal outcomes
- exception outcomes
- rejection or block outcomes
- manual review or escalation outcomes
- default outcome when no specific rule matches

If the default or precedence is unclear, record it as a gap instead of guessing.

### 4. Identify Input Data

Capture the facts needed to make the decision:

- quantities, dates, statuses, categories, roles, regions, products, channels
- customer, account, order, case, request, asset, user, or partner attributes
- risk scores, historical behavior, budgets, limits, entitlements
- validation results, external checks, source-of-truth systems

For each input, note source or confidence when known. If the rule mentions a
condition but the data source is missing, record a gap.

### 5. Link Supporting Rules

Group rules under the decision they support. Preserve existing rule IDs when
available. If rules are not already numbered, create local IDs such as
`BR-001`, `BR-002`, and mark them as local.

For each rule, capture:

- rule statement
- source evidence
- input conditions
- produced outcome or effect
- exceptions or overrides
- confidence: high, medium, or low

If one rule supports multiple decisions, list it under each decision and note
the dependency.

### 6. Model Decision Logic

Choose the clearest representation:

- **Decision table:** best when input combinations map to outcomes
- **Ordered rule list:** best when precedence matters
- **Formula:** best for calculations
- **State transition table:** best for workflow status changes
- **Pseudocode:** best when stakeholders need a compact logic summary

Prefer decision tables for approval, routing, eligibility, classification, and
permission decisions.

When building a table:

- include all known inputs that change the outcome
- include one row per meaningful condition set
- make rule precedence explicit when rows overlap
- include the default case if known
- mark unknown, missing, or contradictory cases instead of filling them in

### 7. Find Gaps And Conflicts

Check for:

- missing input data or source systems
- missing outcomes or default behavior
- unclear rule precedence
- overlapping rules that produce different outcomes
- contradictory thresholds, dates, statuses, or role permissions
- unhandled edge cases
- rules that describe policy but not the resulting decision outcome
- outcomes that appear in workflow or UI copy but lack supporting rules

Do not smooth over contradictions. Preserve them for stakeholder validation.

### 8. Generate Validation Scenarios

Create concrete examples that can become QA tests or stakeholder review cases.
Include:

- normal cases
- boundary cases, especially threshold values
- exception cases
- conflict or precedence cases
- default cases
- missing or invalid input cases

Each scenario should include input data, expected outcome, and rules tested.

## Output Format

Default to this format:

```markdown
# Business Decision Discovery: <domain>

## Scope
<what was reviewed, intended use, and exclusions>

## Decision Catalog
| ID | Decision | Requirement / Need | Inputs | Outcomes | Rules Used | Confidence |
|---|---|---|---|---|---|---|
| DEC-001 | <decision question> | <REQ/source/need> | <input data> | <outcomes> | <rule IDs> | <high/medium/low> |

## Decision Details

### DEC-001: <decision question>

**Purpose:** <business need this decision supports>

**Inputs:**
- <input name>: <meaning/source>

**Outcomes:**
- <outcome>: <meaning>

**Rules Used:**
- BR-001: <rule statement> (<source>, <confidence>)

**Decision Logic:**
| Condition | Outcome | Rules |
|---|---|---|
| <condition> | <outcome> | <rule IDs> |

**Gaps And Conflicts:**
- <gap, conflict, missing precedence, missing default, or missing source>

**Validation Scenarios:**
| Scenario | Input Data | Expected Outcome | Rules Tested |
|---|---|---|---|
| <case> | <data> | <outcome> | <rule IDs> |

## Cross-Decision Issues
| Issue | Affected Decisions | Why It Matters | Suggested Follow-Up |
|---|---|---|---|
```

When the source material contains many decisions, keep the decision catalog
complete and provide detailed logic only for decisions with enough evidence or
high importance.

## Quality Bar

A good discovery output is:

- layered: requirements, rules, decisions, data, and outcomes are separate
- decision-centered: rules are grouped around the decision they support
- input-explicit: required data is visible
- outcome-explicit: possible outcomes, defaults, and exceptions are visible
- traceable: decisions and rules cite source evidence where available
- testable: validation scenarios can become QA tests or stakeholder examples
- honest: gaps, conflicts, and ambiguous precedence are not guessed away
- lightweight: no strategic decision framework overhead unless requested

## Guardrails

The AI should:

- discover decisions from rules, requirements, workflows, data, and code
- name decisions as questions or outcome selections
- preserve existing requirement and rule IDs when available
- generate local IDs only when needed for readability
- use decision tables when they clarify the logic
- generate validation scenarios for each modeled decision

The AI should not produce a final strategic recommendation, create a full
requirements catalog, create a full rule catalog, bury rules inside prose,
invent missing precedence, invent missing data sources, or require formal DMN
notation unless the user asks for it.
