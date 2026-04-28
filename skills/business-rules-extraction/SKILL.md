---
name: business-rules-extraction
description: Use when extracting, auditing, or documenting business rules from code, specs, tickets, policies, workflows, conversations, spreadsheets, or legacy systems. Produces a structured rule catalog with sources, confidence, ambiguities, ownership, and validation questions.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Business Rules Extraction

Extract business rules from messy source material and turn them into a durable,
auditable rule catalog. Use this skill when the user asks to find, document,
reverse-engineer, audit, migrate, or clarify domain rules from code,
documentation, operational processes, data, or stakeholder notes.

Do not use this for generic summarization. The output should preserve rules as
explicit decisions the business or system depends on.

## Core Principle

Separate facts from interpretations. Every extracted rule needs source evidence,
scope, confidence, and open questions. Do not silently convert weak inference
into certain policy.

## Grounding

Base the extraction on established business-rule practice:

- Treat rules as first-class requirements, not implementation by-products.
- Keep rules separate from processes, procedures, UI behavior, and enforcement
  mechanisms. A process can invoke or enforce a rule, but it is not the rule.
- Build rules on business vocabulary: terms define concepts, facts connect
  concepts, and rules constrain, derive, or guide facts.
- Express rules declaratively in business language. Prefer "An order must..."
  over procedural instructions like "Call this service, then update..."
- Make each rule atomic enough that it cannot be split without losing business
  meaning.
- Record whether each rule is a structural assertion, action assertion, or
  derivation before adding practical tags.
- Model complex decisions with a decision question, allowed outcomes, required
  input data, supporting knowledge, related decisions, and decision tables when
  useful.
- Validate rules with business stakeholders for correctness and against each
  other for consistency. No rule is assumed just because code behaves that way.
- Treat exceptions as rules too. Do not bury them in prose.

## Rule Types

First classify each rule by business-rule kind:

- **Structural assertion:** a term, definition, fact, or relationship the
  business relies on
- **Action assertion:** a constraint, permission, prohibition, obligation, or
  condition that governs behavior
- **Derivation:** a calculation, inference, classification, score, eligibility
  result, or other knowledge derived from facts

Then add one or more practical tags:

- **Eligibility:** who or what qualifies
- **Validation:** allowed, required, prohibited, or formatted values
- **Calculation:** formulas, thresholds, derived fields, fees, scores, taxes,
  dates, or allocations
- **Decision:** branching logic, approvals, routing, prioritization, overrides,
  or exception handling
- **Workflow:** state transitions, sequencing, handoffs, timing, SLAs, or
  required actions
- **Authorization:** roles, permissions, ownership, separation of duties, or
  access constraints
- **Compliance:** legal, policy, audit, retention, disclosure, or reporting
  requirements
- **Data:** definitions, lifecycle, source of truth, deduplication, mappings,
  or synchronization rules
- **Notification:** who is informed, when, through which channel, and with what
  content

## Workflow

### 1. Scope

Identify the extraction target:

- domain or product area
- source material available
- intended use: documentation, rewrite, migration, QA, compliance, onboarding,
  automation, or stakeholder alignment
- desired output format, if specified

If the user has not provided source material, ask for it. If the user points to
a repo, codebase, folder, document, or ticket set, inspect it directly.

### 2. Source Inventory

Create a compact inventory of reviewed sources. Include paths, documents,
tables, endpoints, modules, config files, tests, tickets, or interview notes.

Inventory sources by evidence level:

- **Authoritative:** policy, law, contract, signed-off spec, product decision,
  domain-owner confirmation
- **Behavioral:** production code, tests, data, logs, workflows, reports,
  spreadsheets, operational runbooks
- **Anecdotal:** conversation notes, examples, comments, issue discussions,
  legacy tribal knowledge

When working in code:

- search for conditionals, validations, constants, enums, state machines,
  permissions, feature flags, scheduled jobs, calculations, error messages,
  tests, migrations, schemas, and policy/config files
- prefer existing tests and fixtures as behavioral evidence
- include line references for rules when practical

When working from prose:

- separate explicit policy from examples, anecdotes, preferences, and proposed
  future behavior
- note conflicting statements without forcing resolution

### 3. Extract Candidate Rules

For each candidate, capture:

- canonical business vocabulary used by the rule
- the rule in plain business language
- evidence source
- trigger or context
- inputs and outputs
- actors, roles, or systems involved
- exceptions, overrides, and edge cases
- confidence: high, medium, or low
- whether the rule is explicit, inferred, or contradicted
- whether the observed behavior is current behavior, intended policy, or both

Prefer atomic rules. Split compound statements when each part can change
independently.

For decisions, capture:

- decision question
- allowed outcomes
- input data
- supporting knowledge or policies
- related upstream or downstream decisions
- output and business impact

### 4. Normalize

Make rules testable and unambiguous:

- define key terms before relying on them
- replace vague language with concrete thresholds where evidence supports it
- preserve original wording when it carries policy meaning
- identify default behavior when no condition matches
- separate current behavior from desired behavior
- distinguish "must", "should", "may", and "must not"
- separate the rule from how it is enforced
- turn exception prose into explicit exception rules

### 5. Validate And Gap Check

Before finalizing, check for:

- missing actors, states, dates, thresholds, currencies, jurisdictions, or time
  zones
- overlapping or contradictory rules
- rules encoded only in UI copy, tests, migrations, or operational habit
- undocumented exceptions and manual overrides
- implementation behavior that may not match intended policy
- downstream reports, billing, compliance, or customer-visible effects

Ask targeted questions only for gaps that could materially change the catalog.
When possible, propose examples that should pass, fail, and hit exceptions.

## Output Format

Default to a rule catalog:

```markdown
# Business Rules: <domain>

## Scope
<what was reviewed and what is out of scope>

## Source Inventory
| Source | Type | Notes |
|---|---|---|
| <path/doc/person> | <code/spec/interview/data/test> | <relevance> |

## Definitions
| Term | Meaning | Source | Confidence |
|---|---|---|---|

## Rule Catalog
| ID | Kind | Tags | Rule | Applies When | Exceptions | Source | Confidence |
|---|---|---|---|---|---|---|---|
| BR-001 | <structural/action/derivation> | <tags> | <plain-language rule> | <trigger/scope> | <exceptions> | <source> | <high/medium/low> |

## Decision Logic
<optional pseudocode, decision table, state transition table, or formula summary>

## Contradictions
| Topic | Conflict | Sources | Recommended Resolution |
|---|---|---|---|

## Open Questions
| Question | Why It Matters | Suggested Owner |
|---|---|---|

## Validation Plan
<tests, stakeholder checks, data queries, or examples that would confirm the rules>
```

Use decision tables for branching logic, state transition tables for workflows,
and formulas for calculations when those representations are clearer than prose.

## Quality Bar

A good extraction is:

- traceable: every rule points back to evidence
- atomic: one rule can change without rewriting unrelated rules
- testable: a person can tell whether an example complies
- bounded: scope and exclusions are explicit
- honest: inferred, contradicted, and low-confidence rules are labeled
- useful: the catalog can drive implementation, QA, migration, or stakeholder
  review
- business-readable: stakeholders can validate the wording without reading code
- stable: rules are separate from the process steps or technical mechanism that
  enforce them

## Common Mistakes

- summarizing behavior without extracting rules
- treating code behavior as intended business policy without saying so
- omitting exceptions because they are inconvenient
- merging validation, workflow, and authorization into one vague rule
- inventing missing thresholds or owners
- failing to include source references
- writing procedural instructions instead of declarative rules
- documenting exceptions as comments instead of rules

## Online References

These sources ground the method. Use them for principles, not as rigid ceremony:

- Business Rules Group, *Defining Business Rules - What Are They Really?*
  https://www.businessrulesgroup.org/first_paper/BRG-whatisBR_3ed.pdf
- Business Rules Group, *Business Rules Manifesto*
  https://www.businessrulesgroup.org/brmanifesto/BRManifesto.pdf
- Object Management Group, *Decision Model and Notation*
  https://www.omg.org/dmn/index.htm
- IIBA, *The Business Analysis Standard*
  https://www.iiba.org/knowledgehub/the-business-analysis-standard/
- IIBA, *BABOK Guide Techniques*
  https://www.iiba.org/knowledgehub/business-analysis-body-of-knowledge-babok-guide/techniques/
