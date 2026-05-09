---
name: project-situation-briefing
description: Use when turning messy project information into a clear current-state project briefing, including objectives, scope, status, stakeholders, owners, dependencies, decisions, risks, blockers, assumptions, open questions, and next actions. Useful for project kickoffs, handovers, status resets, recovery work, steering preparation, and reconstructing project truth from notes, emails, tickets, meeting minutes, plans, or stakeholder updates.
---

# Project Situation Briefing

Turn scattered project material into a concise delivery truth snapshot. Use this
skill when the user needs to understand where a project actually stands before
planning, reporting, escalating, recovering, or handing over work.

## Practice Basis

Ground the briefing in broadly used project management practice, not one
company's reporting habits:

- PMI's PMBOK Guide frames current project management around principles and
  performance domains such as stakeholders, planning, project work, delivery,
  measurement, and uncertainty. Use the briefing to connect project facts to
  value, outcomes, stakeholders, delivery work, and uncertainty.
- PRINCE2 principles emphasize continued business justification, defined roles
  and responsibilities, management by stages, management by exception, product
  focus, and tailoring. Use these as checks for whether the project has a clear
  why, accountable roles, stage or milestone controls, tolerances, deliverables,
  and a fit-for-context management approach.
- APM project controls treat scope, time, cost, risk, and change as core
  control dimensions. Use those dimensions to expose whether the project is
  controlled enough for the user's purpose.
- RAID practice gives a simple control layer for risks, assumptions, issues,
  and dependencies. Use RAID categories to make uncertainty and blockers
  operational rather than vague.
- Stakeholder engagement practice treats stakeholder identification, analysis,
  communication, and involvement as active project work. Use the briefing to
  make stakeholder interests, influence, decisions, and information needs
  visible.

Do not invent certainty. If a date, owner, decision, dependency, risk, or scope
boundary is missing or inconsistent, mark it as unknown, conflicting, or inferred.

## Source Anchors

Use these sources as the underlying practice references when interpreting the
workflow:

- PMI PMBOK Guide overview:
  `https://www.pmi.org/pmbok-guide-standards/foundational/pmbok`
- PMI project performance domains summary:
  `https://www.pmi.org/-/media/pmi/documents/public/pdf/pmbok-standards/pmbok-project-performance-domains.pdf`
- PeopleCert PRINCE2 7 syllabus:
  `https://peoplecert.jp/doc/PRINCE2_Agile_FND_Syllabus_EN_v2_0.pdf`
- APM project controls overview:
  `https://www.apm.org.uk/resources/what-is-project-management/what-is-project-controls/`
- APM stakeholder engagement and risk principle:
  `https://www.apm.org.uk/resources/find-a-resource/stakeholder-engagement/key-principles/just-part-of-managing-risk/`

## Workflow

### 1. Establish The Briefing Context

Identify:

- project name or working label
- intended use: kickoff, handover, status reset, steering preparation, recovery,
  delivery planning, escalation, or stakeholder alignment
- source material reviewed
- reporting date or "as of" date
- audience: PM only, delivery team, sponsor, customer, steering group, or mixed

If the source material is thin, still produce a briefing and make the gaps
visible.

### 2. Extract The Delivery Shape

Capture the basic project frame:

- objective and business outcome
- in-scope and out-of-scope work
- major deliverables or workstreams
- current phase or status
- target milestones and known deadlines
- success criteria or acceptance conditions
- control dimensions: scope, schedule, cost, quality, risk, change, benefits,
  and stakeholder readiness
- constraints such as budget, capacity, compliance, business readiness, vendor
  availability, procurement, change windows, or contractual commitments

Separate facts from interpretations. Use "evidence says", "appears", or
"unknown" when confidence differs.

### 3. Build The Control View

Extract and normalize:

- stakeholders and their roles
- owners for deliverables, decisions, approvals, risks, and actions
- dependencies and prerequisites
- decisions made, pending, or missing
- open questions
- risks, assumptions, issues, and blockers
- benefits or business justification signals
- stage or milestone tolerances where available
- recent changes since the last known baseline
- next actions with owner and date where available

Flag common control weaknesses:

- action without owner
- owner without authority
- due date without dependency readiness
- dependency without accountable party
- decision needed but no decision owner
- risk stated as a concern but not controlled
- milestone that depends on an unresolved assumption
- exception or tolerance breach without escalation path
- deliverable without acceptance criteria
- status label that conflicts with evidence

### 4. Synthesize The Situation

Create a short narrative that answers:

- What is the project trying to achieve?
- Where does it stand now?
- What is on track?
- What is blocked, at risk, or ambiguous?
- What decisions or actions would most improve delivery confidence?

Keep the synthesis neutral and operational. Avoid blame, exaggerated confidence,
or generic project-management filler.

## Output Format

Default to this structure:

```markdown
# Project Situation Briefing: <project>

## As-Of Context
<date, sources, audience, intended use>

## Executive Snapshot
<5-8 bullets on objective, current state, health, and most important controls>

## Project Frame
| Area | Current Understanding | Evidence / Confidence |
|---|---|---|

## Stakeholders And Ownership
| Stakeholder / Role | Interest Or Responsibility | Owner / Accountable? | Notes |
|---|---|---|---|

## Workstreams And Milestones
| Workstream / Deliverable | Status | Owner | Target / Date | Dependency | Confidence |
|---|---|---|---|---|---|

## RAID And Blockers
| Type | Item | Impact | Owner | Control / Next Step | Confidence |
|---|---|---|---|---|---|

## Decisions And Open Questions
| Item | Needed From | By When | Impact If Delayed | Status |
|---|---|---|---|---|

## Immediate Next Actions
| Action | Owner | Due | Purpose | Source / Confidence |
|---|---|---|---|---|
```

For a quick answer, compress the output into: snapshot, risks/blockers,
decisions, next actions, and gaps.

## Quality Bar

Before finalizing, check:

- Are facts, assumptions, and gaps separated?
- Are dates, owners, and dependencies explicit where known?
- Are vague statements converted into delivery-relevant controls?
- Are scope, time, cost, risk, change, quality, benefits, and stakeholder
  impacts covered enough for the user's purpose?
- Are all recommendations traceable to source material or clearly labeled as
  inferred?
- Would another PM understand what to do next without reading the original
  source pile?
