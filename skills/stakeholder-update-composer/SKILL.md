---
name: stakeholder-update-composer
description: Use when drafting, rewriting, or tailoring project stakeholder communications from raw delivery facts, notes, RAID logs, meeting outcomes, risks, decisions, blockers, or status updates. Produces audience-specific project updates, steering summaries, escalation notes, decision requests, customer-facing updates, internal updates, and executive briefings.
---

# Stakeholder Update Composer

Convert raw project facts into clear stakeholder communication. Use this skill
when the user needs a project update, steering note, escalation, decision
request, customer-facing summary, internal delivery update, or executive brief.

## Practice Basis

Ground communication in broadly used project communications and stakeholder
engagement practice:

- PMI communications guidance emphasizes timely and appropriate planning,
  creation, distribution, management, monitoring, and disposition of project
  information. Use this to choose the right message, audience, timing, and
  channel.
- PMI stakeholder guidance emphasizes identifying stakeholders, understanding
  expectations and impact, and engaging them in project decisions and execution.
  Use this to tailor the update around what the audience needs to know or do.
- PMI risk communication guidance emphasizes that not every risk belongs in
  every stakeholder update; communicate risks that are relevant, actionable,
  and proportionate to the audience.
- PRINCE2 principles emphasize defined roles, management by stages, management
  by exception, product focus, and continued business justification. Use these
  to make decision requests, stage status, exception conditions, deliverables,
  and business impact clear.
- APM stakeholder engagement practice treats communication and stakeholder
  analysis as part of risk management. Use this to surface stakeholder impacts,
  resistance, support, decisions, and communication gaps.

Do not hide bad news. Do not overstate certainty. Do not expose unnecessary
internal noise to external stakeholders.

## Source Anchors

Use these sources as the underlying practice references when interpreting the
workflow:

- PMI communications management article:
  `https://www.pmi.org/learning/library/one-solution-for-project-success-11130`
- PMI communications best practices article:
  `https://www.pmi.org/learning/library/managing-communications-effectively-efficiently-5916`
- PMI risk communication article:
  `https://www.pmi.org/learning/library/explaining-risk-project-stakeholders-2206`
- PMI stakeholder management strategies article:
  `https://www.pmi.org/learning/library/stakeholder-management-strategies-applying-risk-management-7479`
- PeopleCert PRINCE2 7 syllabus:
  `https://peoplecert.jp/doc/PRINCE2_Agile_FND_Syllabus_EN_v2_0.pdf`
- APM stakeholder engagement and risk principle:
  `https://www.apm.org.uk/resources/find-a-resource/stakeholder-engagement/key-principles/just-part-of-managing-risk/`

## Workflow

### 1. Identify Audience And Purpose

Determine:

- audience: customer, sponsor, steering group, delivery team, vendor, executive,
  internal management, or mixed
- purpose: routine status, decision request, escalation, expectation reset,
  progress summary, milestone readiness, recovery update, or handover
- communication channel: email, Slack or Teams message, steering note, meeting
  pre-read, brief, or talking points
- desired tone: neutral, concise, formal, diplomatic, urgent, or executive
- whether the update should be external-safe or internal-only
- stakeholder decision authority, influence, and information need where known

If the audience is unclear, choose a conservative business-readable update and
state the assumption.

### 2. Extract Message Ingredients

From the raw material, identify:

- current status and confidence
- progress since last update
- completed work and evidence
- upcoming milestones
- risks, issues, blockers, and dependencies
- decisions needed and decision owner
- actions, owners, and dates
- changes to timeline, scope, cost, quality, or expectations
- support or input requested from the audience
- exception conditions, tolerance breaches, or stage-gate decisions
- business impact or benefits impact

Do not include every detail. Select what changes stakeholder understanding or
requires action.

### 3. Choose The Communication Shape

Use the shape that fits the purpose:

- **Routine status:** summary, progress, next milestones, risks/issues,
  decisions/actions.
- **Steering summary:** delivery confidence, material changes, decisions needed,
  top risks, asks, and exception conditions.
- **Escalation:** issue, impact, evidence, options, recommendation, decision or
  support needed, deadline.
- **Decision request:** decision question, context, options, tradeoffs,
  recommendation, deadline, impact if delayed.
- **Expectation reset:** prior expectation, current evidence, impact, revised
  plan, controls, ask.
- **Internal update:** operational detail, blockers, owners, follow-up actions,
  escalation path.
- **Customer-facing update:** outcome-focused progress, impact, next steps,
  dependencies, decisions needed, no unnecessary internal fault detail.
- **Stage or milestone update:** deliverables, acceptance status, confidence,
  open controls, decision to proceed, and conditions.

### 4. Draft And Tighten

Write with:

- clear subject or title when useful
- first paragraph that states the point
- short sections or bullets
- explicit asks and dates
- named owners where appropriate
- measured language for risk and uncertainty
- no unexplained acronyms unless the source audience clearly uses them

If the source facts are incomplete, include a short "open items" or "confirm"
section rather than pretending completeness.

## Output Format

Default to the requested communication artifact. If no format is specified,
produce:

```markdown
Subject: <clear project update subject>

Hi <audience>,

<short point-first opening>

## Current Status
<where things stand and confidence>

## Progress Since Last Update
<material completed work>

## Risks, Issues, And Dependencies
<only items relevant to this audience>

## Decisions Or Input Needed
<decision / ask, owner, needed by, impact if delayed>

## Next Steps
<actions, owners, dates>
```

For executive or steering updates, use a briefing format instead of an email:

```markdown
# Stakeholder Update: <project>

## Headline
<one-sentence point>

## Delivery Confidence
<green / amber / red if provided, or plain-language confidence if not>

## Material Changes
<what changed since last update>

## Decisions / Asks
| Ask | Owner | Needed By | Impact If Delayed |
|---|---|---|---|

## Top Risks And Controls
| Risk / Issue | Impact | Control | Owner |
|---|---|---|---|

## Next Milestones
| Milestone | Date | Confidence | Notes |
|---|---|---|---|
```

## Quality Bar

Before finalizing, check:

- Does the first paragraph say why the stakeholder is receiving this?
- Are facts and judgments separated?
- Are risks, issues, decisions, and actions not mixed together?
- Is the ask unmistakable, with owner and date where available?
- Is the level of detail appropriate for the audience?
- Are risks communicated only when relevant, timely, and actionable for this
  stakeholder?
- Could this be sent without embarrassing the PM or creating avoidable
  confusion?
