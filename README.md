# Think

This repository contains local skills for structured thinking across reasoning,
decision work, business analysis, and project delivery control.

## How To Use These Skills

These skills are reusable instructions for AI assistants. A project manager or
business user does not need to run commands or edit the files directly. The same
skill can be used in several ways depending on the tools a company already has.

Common usage patterns:

| Context | How To Use The Skills |
|---|---|
| Company AI chat app | Add the relevant `SKILL.md` text to the assistant's system instructions, knowledge base, prompt library, or reusable template |
| ChatGPT or similar chat tools | Paste the relevant skill instructions into a custom GPT, project instructions, or the start of a chat before adding project material |
| Internal PMO or delivery templates | Convert the skill's output format into a standard briefing, risk review, or stakeholder-update template |
| Local agent tools such as Codex | Install the skill pack once so the agent can automatically choose and apply the right skill |
| Workshops and reviews | Use the skill's workflow as a facilitation checklist for turning messy notes into decisions, risks, actions, and updates |

The simplest non-technical workflow is:

1. Pick the skill that matches the job.
2. Give the AI assistant the skill instructions or use a preconfigured assistant
   that already has them.
3. Add the project notes, emails, meeting transcript, RAID log, plan, or status
   update.
4. Ask for the output you need.

Examples:

```text
Use project-situation-briefing to turn these project notes into a current-state briefing.
```

```text
Review this project plan for hidden delivery risks.
```

```text
Draft a customer-facing project update from these raw notes.
```

If you are not sure which skill to use, describe the problem in normal language.
The agent should choose the relevant skill from the skill descriptions.

## Installation For Admins

```bash
npx skills add fheinonen/think
```

## Skill Map

| Family | Skill | Use For |
|---|---|---|
| Core thinking | `think` | Turning a messy thought dump into a usable breakdown |
| Core thinking | `systemic-thinking` | Analyzing a complex problem with explicit structure |
| Core thinking | `model-building` | Turning a system or pattern into a conceptual model with parameters, levers, and tests |
| Decision work | `decision-system` | Stress-testing a decision frame and making a recommendation |
| Decision work | `engineering-judgment-coaching` | Improving the reasoning behind an engineering recommendation |
| Action coaching | `action-activation` | Converting stuckness into a low-stakes, reversible next action |
| Business analysis | `business-requirements-extraction` | Extracting traceable business, stakeholder, solution, transition, and constraint requirements |
| Business analysis | `business-rules-extraction` | Extracting auditable policies, constraints, calculations, validations, and exceptions |
| Business analysis | `business-decision-discovery` | Discovering operational decisions, inputs, outcomes, decision tables, and validation scenarios |
| Project management | `project-situation-briefing` | Turning messy project material into a current-state delivery briefing |
| Project management | `delivery-risk-review` | Finding hidden delivery risks, assumptions, dependencies, decisions, and control gaps |
| Project management | `stakeholder-update-composer` | Drafting audience-specific project updates, escalations, and decision requests |

## Core Thinking Model

The core thinking skills help move from raw thought to structured understanding:

| Thing | Question It Answers | Example |
|---|---|---|
| Thought breakdown | What are the threads inside this messy thought dump? | Database sync, rollback, cost, and ownership are separate concerns |
| Systemic analysis | What structure, unknowns, and models explain this problem? | The migration risk is not only technical; it is also ownership and timing |
| Conceptual model | What variables, feedback loops, constraints, and levers shape this system? | Ticket backlog grows when intake exceeds resolution and priority rules hide aging work |

## Business Analysis Model

The business-analysis skills form a simple layer model:

| Thing | Question It Answers | Example |
|---|---|---|
| Requirement | What does the business need? | Route customer requests correctly |
| Rule | What policy or constraint applies? | Suspended accounts require account review |
| Decision | What outcome must be chosen? | Should this request be self-served, handled normally, escalated, or reviewed? |
| Decision table | How is the outcome chosen? | If account is suspended, route to account review |
| Test scenario | How do we verify it? | Suspended account request routes to account review |

## Project Management Model

The project-management skills form a simple delivery-control model:

| Thing | Question It Answers | Example |
|---|---|---|
| Situation briefing | What is actually true about the project right now? | The migration is in build, test access is blocked, the sponsor decision is late, and two dependencies have no owner |
| Delivery risk review | What could break delivery, and what control is missing? | The cutover date depends on unvalidated test readiness and needs an owner, trigger, and contingency |
| Stakeholder update | What does this audience need to know or decide? | Steering group needs a decision on whether to hold scope, add capacity, or move the milestone |

The flow is usually: clarify the situation, review delivery risk, then
communicate the right facts, decisions, and asks to the right stakeholders.

## Common Prompts

### Core Thinking

- "I need to think through something"
- "Use systemic thinking to analyze this migration plan"
- "Break this problem into local notes and map the unknowns"
- "Model why our product activation is weak"
- "Turn this explanation into a control surface: variables, parameters, levers, risks, and small tests"

### Decision And Action

- "Help me decide whether to rebuild this dashboard"
- "Challenge the premise of this plan before we choose an option"
- "Coach me through this recommendation like a senior engineer mentoring another engineer"
- "Help me stop overthinking and pick the smallest real next step"
- "Turn this intention into a concrete action I can do today"

### Business Analysis

- "Extract the business requirements from these interview notes"
- "Separate requirements from designs, tasks, assumptions, and business rules"
- "Extract the business rules from this billing module"
- "Turn these policy notes into testable business rules"
- "Turn this rule catalog into decision tables and validation scenarios"

### Project Management

- "Turn these project notes into a current-state briefing"
- "Create a project truth snapshot from this email thread and RAID log"
- "Review this project plan for hidden delivery risks"
- "Turn these concerns into risks, assumptions, decisions, and next controls"
- "Draft a customer-facing project update from these raw notes"
- "Write an escalation note with impact, options, recommendation, and decision needed"

## HTML Artifacts

Several skills can turn their structured output into standalone HTML artifacts
when asked for a shareable or reviewable version. These files are intended for
stakeholder review, workshops, printing, or preserving a model outside the chat.

Ask for it directly:

```text
Create a standalone HTML artifact from this.
```

## License

MIT
