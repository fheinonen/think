# Business Decision Discovery Design

## Purpose

Add a lightweight `business-decision-discovery` skill that discovers the
business decisions hidden inside requirements, rules, policies, workflows,
specs, code, tickets, or stakeholder notes.

This skill is the missing middle layer between:

- `business-requirements-extraction`: what the business needs
- `business-rules-extraction`: what policies or constraints apply
- `business-decision-discovery`: what question is answered, using which data
  and rules, to produce which outcome

The skill should not become a general strategic decision-making framework. Its
job is to model operational business decisions clearly enough that they can
drive implementation, QA, workflow automation, and stakeholder validation.

## Mental Model

Use this simple relationship:

```text
Requirement
  -> Decision
  -> Rules + Data
  -> Outcome
```

Example:

```text
Requirement:
Prevent unauthorized invoice payments.

Decision:
Determine invoice approval route.

Data:
Invoice amount, supplier risk, tax ID status, budget status.

Rules:
- If invoice > EUR 5,000, manager approval is required.
- If supplier is high-risk, finance review is required.
- If tax ID is missing, invoice cannot proceed.

Outcome:
Auto-approve, manager approval, finance review, or reject.
```

## Scope

In scope:

- Create `skills/business-decision-discovery/SKILL.md`.
- Update `README.md` to explain the requirements/rules/decisions distinction.
- Keep the skill concise and practical.
- Ground the skill in well-known decision modeling practice, especially
  Decision Model and Notation (DMN), decision tables, and business rule
  analysis.
- Produce decision catalogs, decision tables, gaps, conflicts, and test
  scenarios.

Out of scope:

- Do not create a heavyweight pre-decision strategy or executive decision
  framework.
- Do not recommend which business option to choose.
- Do not duplicate `decision-system`.
- Do not duplicate requirements or rule extraction beyond the minimum needed to
  link decisions to requirements and rules.
- Do not create scripts, assets, or reference files unless implementation shows
  a clear need.

## Grounding

Use established decision modeling ideas as lightweight scaffolding:

- Decision Model and Notation (DMN): represent operational business decisions,
  required input data, supporting rules or knowledge, and decision logic.
- Decision tables: map input conditions to outcomes using rows of rules.
- Business rule analysis: keep rules separate from processes, UI behavior, and
  implementation mechanisms.
- Requirements traceability: link decisions back to the requirement or business
  need they support.

The skill should not require formal DMN XML, FEEL expressions, or full decision
requirements diagrams. Use plain Markdown tables unless the user asks for a
formal notation.

## Workflow

The skill should run this flow:

1. **Scope the source material.** Identify the business domain, source material,
   and intended use. If no source material is provided, ask for it.
2. **Find candidate decisions.** Look for places where the business chooses an
   outcome: approve/reject, route/escalate, price/discount, eligible/ineligible,
   classify, prioritize, calculate, assign, notify, block, or permit.
3. **Name each decision as a question.** Prefer clear phrases such as
   "Determine invoice approval route" or "Is the customer eligible for renewal
   discount?"
4. **Identify possible outcomes.** Capture the finite outcomes the decision can
   produce, including default and exception outcomes.
5. **Identify required input data.** Capture the facts needed to make the
   decision: amount, status, risk score, customer type, date, jurisdiction,
   account state, product type, history, or other data.
6. **Link supporting rules.** Group extracted or inferred business rules under
   the decisions they support. Preserve rule IDs when available. Create local
   temporary IDs when source rules are not already numbered.
7. **Build decision logic.** Use a decision table, ordered rule list, or compact
   pseudocode. Prefer decision tables when combinations of inputs produce
   different outcomes.
8. **Find gaps and conflicts.** Identify missing inputs, missing outcomes,
   overlapping rules, contradictory rules, unclear precedence, ambiguous
   thresholds, and unhandled cases.
9. **Generate validation scenarios.** Produce concrete test cases for normal,
   boundary, exception, conflict, and default cases.

## Output Format

Default to this compact artifact:

```markdown
# Business Decision Discovery: <domain>

## Scope
<source material reviewed and intended use>

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
- BR-001: <rule>

**Decision Logic:**
| Condition | Outcome | Rules |
|---|---|---|
| <condition> | <outcome> | <rule IDs> |

**Gaps And Conflicts:**
- <gap, conflict, missing precedence, missing default, missing source>

**Validation Scenarios:**
| Scenario | Input Data | Expected Outcome | Rules Tested |
|---|---|---|---|
| <case> | <data> | <outcome> | <rule IDs> |

## Cross-Decision Issues
| Issue | Affected Decisions | Why It Matters | Suggested Follow-Up |
|---|---|---|---|
```

When the source material contains many decisions, keep the catalog complete and
provide detailed logic only for the decisions with enough evidence or highest
importance.

## Quality Bar

A good output:

- separates requirements, rules, decisions, data, and outcomes
- names decisions as business questions or outcome selections
- groups rules around the decision they support
- makes required input data explicit
- includes default and exception outcomes when discoverable
- uses decision tables when they make logic easier to inspect
- preserves source evidence and confidence
- identifies unhandled cases, conflicts, and ambiguous precedence
- generates validation scenarios that can become QA tests or stakeholder review
  examples
- stays lightweight and avoids strategic decision framework overhead

## README Update

Update the README with a short explanation:

```text
Requirement = what the business needs.
Rule = what policy or constraint applies.
Decision = what outcome must be chosen from rules and data.
Decision table = how input combinations map to outcomes.
Test scenario = how to verify the decision.
```

Also add `business-decision-discovery` to the skill list and side-by-side
workflow section.

## Implementation Notes

Follow the style of existing skills in this repository. A single `SKILL.md`
file should be enough. The frontmatter description must trigger on terms like
discover business decisions, decision tables, decision logic, input data,
outcomes, group rules by decision, operational decision, approval route,
eligibility decision, routing decision, pricing decision, and validation
scenarios.
