---
name: business-process-extraction
description: Use when extracting, mapping, auditing, or documenting business processes and workflows from interviews, observation notes, SOPs, tickets, emails, code, system behavior, or stakeholder descriptions. Produces a process catalog with triggers, steps, actors, handoffs, inputs, outputs, systems, exceptions, pain points, gaps, and validation walkthroughs.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Business Process Extraction

Extract business processes from messy source material and turn them into a
clear, validated process map. Use this skill when the user asks to discover,
document, reverse-engineer, audit, or clarify how work actually flows: who does
what, in what order, triggered by what, using which systems, producing which
outcomes.

Do not use this for generic summarization, and do not use it to extract the
policies or decision logic inside the process. Rules belong to
`business-rules-extraction` and decision logic belongs to
`business-decision-discovery`; a process step can invoke a rule or decision,
but the process is the flow of work around them.

## Core Principle

Separate the observed process from the official process. What people actually
do, what the SOP says, and what the system enforces are three different things
that rarely match. Capture each with its own evidence and confidence; do not
silently merge them into one tidy flow, and do not document the happy path as
if it were the whole process.

## Grounding

Base the extraction on established process analysis practice:

- Define each process by trigger and outcome before listing steps. A process
  starts with an event and ends with a result a customer or stakeholder cares
  about; activity lists without boundaries are not processes.
- Keep the process separate from the rules and decisions it invokes. "Route the
  request" is a step; how routing is chosen is a decision; "suspended accounts
  require review" is a rule.
- Model actors and handoffs explicitly. Most delay, rework, and lost work lives
  at handoffs and wait states, not inside steps.
- Use SIPOC thinking to bound each process: suppliers, inputs, process,
  outputs, customers.
- Treat exception paths, variants, and rework loops as part of the process, not
  as footnotes. The exception path is often the expensive one.
- Distinguish as-is from to-be. Extract the current state faithfully; propose a
  future state only when the user asks for one.
- Keep notation lightweight and business-readable. Use step tables, text
  swimlanes, and state tables; do not require BPMN diagrams unless the user
  asks.

## Process Elements

For each process, look for these elements:

- **Trigger:** the event, request, schedule, threshold, or state change that
  starts the process
- **Outcome:** the result that ends the process, including failure outcomes
- **Steps:** the units of work, in order, with the actor who performs each
- **Actors:** roles, teams, customers, partners, or systems that do the work
- **Handoffs:** transfers of work between actors, with the channel used
- **Inputs and outputs:** documents, data, approvals, goods, or messages each
  step consumes and produces
- **Systems:** applications, queues, spreadsheets, inboxes, or paper involved
- **Rules and decisions invoked:** policies applied or outcomes chosen at a
  step, referenced by ID when a catalog exists
- **Wait states:** places where work sits pending a person, system, or event
- **Variants:** alternate paths by segment, channel, region, product, or volume
- **Exceptions and rework:** error paths, escalations, manual workarounds, and
  loops back to earlier steps
- **Timing:** durations, deadlines, SLAs, batch schedules, and cutoffs when
  evidence exists

## Workflow

### 1. Scope

Identify:

- domain, department, value stream, or named process being analyzed
- process boundaries: the triggering event and the ending outcome
- source material available
- intended use: documentation, onboarding, automation, system replacement,
  improvement, audit, compliance, outsourcing, or stakeholder alignment
- whether the user wants as-is only, or as-is plus to-be

If source material is missing, ask for it. If the user points to a repo,
folder, document set, ticket set, transcript, SOP, or system, inspect it
directly.

### 2. Source Inventory

Create a compact inventory of reviewed sources. Include SOPs, runbooks,
transcripts, observation notes, tickets, emails, screenshots, code paths,
workflow configurations, queue definitions, and reports.

Classify evidence:

- **Official:** SOPs, policies, training material, signed-off process docs,
  workflow definitions, contracts
- **Behavioral:** tickets, logs, emails, code, system states, queue data,
  timestamps, reports showing what actually happens
- **Anecdotal:** interviews, observation notes, hallway descriptions, tribal
  knowledge, issue comments

When official and behavioral evidence disagree, record both versions instead
of choosing one.

### 3. Identify Processes And Boundaries

List candidate processes before detailing any of them. Common signals in
source material:

- trigger language: "when a customer...", "every Monday", "once approved",
  "if the balance exceeds..."
- sequence language: "then", "after", "before", "once", "next", "meanwhile"
- handoff language: "sends to", "assigned to", "escalates to", "waits for"
- exception language: "unless", "if that fails", "in rare cases", "workaround"
- queues, statuses, inboxes, and folders that hold work in progress

Name each process as trigger-to-outcome, such as "Customer refund request to
refund issued or declined". If a process is large, split it into subprocesses
that each have their own trigger and outcome.

### 4. Extract Steps

For each process, capture per step:

- step number and short action name, starting with a verb
- actor performing it
- inputs consumed and outputs produced
- system, tool, or channel used
- rules or decisions invoked, with IDs when available
- handoff target and wait state, if the step ends with one
- known exceptions, errors, and rework loops
- timing or SLA, when evidence exists
- confidence: high, medium, or low
- whether the step is official, observed, or both

Trace at least one concrete instance end-to-end when the evidence allows it;
real cases expose steps and waits that descriptions omit.

### 5. Map Variants And Exceptions

For each process, separate:

- the main path: the most common route from trigger to outcome
- variants: legitimate alternate paths and what selects them
- exception paths: error handling, escalation, manual override, rework
- abandonment: where work is dropped, cancelled, or lost, and what happens then

Do not collapse variants into the main path. If the selection logic between
paths is complex, name it as a decision and refer it to
`business-decision-discovery`.

### 6. Find Gaps And Pain Points

Check for:

- steps with no clear actor or owner
- handoffs with no notification, queue, or tracking
- wait states with no trigger to resume work
- undocumented manual workarounds and shadow processes such as personal
  spreadsheets and side channels
- official steps nobody performs, and performed steps no document mentions
- rework loops and their causes
- single points of failure: one person, one inbox, one spreadsheet
- missing measures: no one knows volume, duration, or error rate

Record pain points as observations with evidence, not as redesign proposals.

### 7. Validate

Create walkthrough scenarios that stakeholders can confirm or correct: a
concrete case traced step by step from trigger to outcome, including at least
one exception case. Ask targeted questions only for gaps that could materially
change the map.

## Output Format

Default to a process catalog:

```markdown
# Business Processes: <domain>

## Scope
<boundaries, intended use, as-is/to-be, and exclusions>

## Source Inventory
| Source | Evidence Level | Notes |
|---|---|---|

## Process Inventory
| ID | Process | Trigger | Outcome | Actors | Confidence |
|---|---|---|---|---|---|
| PROC-001 | <trigger-to-outcome name> | <event> | <result> | <roles> | <high/medium/low> |

## Process Details

### PROC-001: <process name>

**Trigger:** <event that starts it>
**Outcome:** <results that end it, including failure outcomes>
**Suppliers / Inputs:** <who provides what to start>
**Customers / Outputs:** <who receives what at the end>

**Main Path:**
| # | Step | Actor | Inputs | Outputs | System | Rules / Decisions | Confidence |
|---|---|---|---|---|---|---|---|

**Handoffs And Wait States:**
| From | To | Channel | Resumed By | Known Delay |
|---|---|---|---|---|

**Variants:**
| Variant | Selected When | Differs How |
|---|---|---|

**Exceptions And Rework:**
| Case | Path | Evidence |
|---|---|---|

**Official Vs Observed:**
| Topic | Official Version | Observed Version | Sources |
|---|---|---|---|

**Pain Points:**
| Observation | Evidence | Impact |
|---|---|---|

## Cross-Process Issues
| Issue | Affected Processes | Why It Matters | Suggested Follow-Up |
|---|---|---|---|

## Open Questions
| Question | Why It Matters | Suggested Owner |
|---|---|---|

## Validation Walkthroughs
| Scenario | Path Traced | Expected Outcome | Confirms |
|---|---|---|---|
```

Omit empty sections. When the source material contains many processes, keep
the process inventory complete and provide step detail only for processes with
enough evidence or high importance. Use a text swimlane or state transition
table instead of a step table when those are clearer.

## Shareable HTML Artifact

If the user asks for a shareable, reviewable, exportable, or HTML artifact,
create a single self-contained `.html` file. If no path is provided, use
`./artifacts/YYYY-MM-DD-<slug>-business-processes.html`.

The HTML artifact should:

- present an executive summary, scope, source inventory, process inventory,
  process details, cross-process issues, open questions, and validation
  walkthroughs
- make steps, actors, handoffs, systems, and exception paths visually
  scannable, with swimlane-style grouping by actor when useful
- visually distinguish main path, variants, exceptions, wait states, official
  versus observed behavior, pain points, and confidence
- preserve all process IDs, step numbers, source references, rule and decision
  IDs, confidence labels, gaps, and open questions from the Markdown output
- include a generated date, scope, intended use, and exclusions
- be print-friendly and readable when shared as a standalone file
- use inline CSS only, no external assets, no remote fonts, and no JavaScript
  unless the user explicitly asks for interactivity
- escape source text and user-provided content before inserting it into HTML

Do not use the HTML artifact to make the observed process look official, hide
exception paths and workarounds, or present an unvalidated map as confirmed.

## Quality Bar

A good extraction is:

- bounded: every process has an explicit trigger and outcome
- actor-explicit: every step has an owner, or the missing owner is flagged
- handoff-aware: transfers, channels, and wait states are visible
- exception-complete: variants, errors, rework, and abandonment are mapped
- layered: rules and decisions are referenced, not re-extracted
- honest: official and observed versions are kept separate with evidence
- traceable: steps cite sources, and confidence is labeled
- validatable: a stakeholder can walk a real case through the map and say
  where it is wrong

## Common Mistakes

- documenting the happy path and calling it the process
- merging the official SOP and observed behavior into one flow
- writing steps with no actor, or "the system" as actor for human work
- hiding wait states inside steps instead of mapping them
- embedding rule and decision logic in step descriptions
- treating workarounds and shadow processes as out of scope
- proposing process improvements when the user asked for the current state
- drawing a diagram first and forcing the evidence to fit it
- losing source traceability for contested steps

## Online References

These sources ground the method. Use them for principles, not as rigid
ceremony:

- IIBA, *BABOK Guide Techniques* (process modelling, process analysis)
  https://www.iiba.org/knowledgehub/business-analysis-body-of-knowledge-babok-guide/techniques/
- IIBA, *The Business Analysis Standard*
  https://www.iiba.org/knowledgehub/the-business-analysis-standard/
- Object Management Group, *Business Process Model and Notation*
  https://www.omg.org/bpmn/
- ASQ, *SIPOC Diagram*
  https://asq.org/quality-resources/sipoc
- ASQ, *Value Stream Mapping*
  https://asq.org/quality-resources/lean/value-stream-mapping
