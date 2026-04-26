---
name: decision-system
description: Use when making, reframing, or stress-testing a decision where the premise, criteria, options, recommendation, and review logic all need to be explicit.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Decision System

Help the user make better decisions by challenging the premise before comparing
options, then turning the recommendation into a durable memo when useful. Use
for personal, product, engineering, business, strategy, and organizational
decisions with meaningful tradeoffs, uncertainty, or opportunity cost.

Do not use this when the user mainly needs a thought dump (`think`), broad
systems modeling before any decision is possible (`systemic-thinking`), coaching
an engineer's reasoning process (`engineering-judgment-coaching`), or a trivial
low-cost choice where structure adds friction.

## Core

Challenge the decision before solving it. Do not assume the stated decision is
the real decision. First test the premise, objective, timing, owner,
constraints, and success criteria. The user should experience better questions,
clearer criteria, stronger options, and a defensible recommendation.

## Modes

Determine the mode from the user's request before starting. If unclear, default
to **New Decision**.

### New Decision

The user wants to make, rethink, or stress-test a decision.

Run the flow below. If the request already has enough context, proceed directly.
If missing context would materially change the frame, ask only the minimum
necessary clarifying questions.

#### 1. Adversarial Exploration

Attack the premise before comparing options. Use WRAP-style widening and
reality-testing:

- What decision is actually being made?
- Is the stated decision a problem statement or a proposed solution?
- Why now, who owns it, and what happens if no decision is made?
- What goal is being optimized, and is that goal right?
- Which constraints are real, assumed, inherited, or self-imposed?
- What would make this decision irrelevant?
- What alternative framing would a skeptical competent person propose?

#### 2. Frame Stabilization

Define the stable frame. Use Decision Quality for frame, values, information,
tradeoffs, reasoning, and commitment:

- **Decision:** actual choice to be made
- **Owner/Roles:** owner and implementer by default; for multi-stakeholder
  decisions, use DACI/RAPID-style roles: recommender, decider, contributors,
  approvers, implementers, and informed parties
- **Timing/Stakes:** why now, later, or not yet; what is gained, lost, risked,
  or delayed
- **Criteria:** Kepner-Tregoe-style must-have constraints and weighted wants
- **Assumptions/Unknowns:** relied-on claims, missing facts, and what would
  invalidate key assumptions
- **Reversibility:** one-way/two-way-door assessment: one-way door, two-way
  door, or mixed
- **Context type:** Cynefin/OODA-style orientation: clear, complicated,
  complex, chaotic, or confused

Use context type to choose the decision style:

- **Clear:** decide quickly using known rules or obvious constraints
- **Complicated:** analyze, compare, and seek expert input where needed
- **Complex:** prefer probes, experiments, reversible steps, and learning loops
- **Chaotic:** stop normal flow; recommend the minimum stabilizing action first
- **Confused:** stop normal flow; recommend decomposition or discovery first

Continue only when the frame is coherent enough to compare alternatives without
pretending to know more than is known.

#### 3. Options

Generate a visible option set after criteria are clear. Include the obvious
option plus plausible non-obvious paths: do nothing, defer/gather evidence,
take a reversible first step, split the decision, relax a constraint, run an
experiment, change the objective, or stop doing the underlying thing.

Eliminate options that fail must-have constraints. Keep viable options distinct
enough that the recommendation is not just the original premise restated.

#### 4. Evaluation

Compare viable options against musts, wants, risks, mitigations, reversibility,
opportunity cost, uncertainty, and context fit. Use Decision Quality to check
information quality, values, tradeoffs, and reasoning. If a missing fact could
change the choice, recommend targeted discovery instead of forcing a decision.

#### 5. Recommendation

Make the recommendation before writing the memo. Include:

- chosen path and rationale
- serious rejected alternatives and why
- risks and mitigations
- confidence: low, medium, or high, with reason
- decision triggers: evidence or events that would change the decision
- next action

Before finalizing, run a premortem: imagine the recommendation failed badly,
name likely causes, and decide whether any cause changes the recommendation,
requires mitigation, or becomes a decision trigger.

#### 6. Memo

If the user asks for a memo or durable capture, use this format:

```markdown
# Decision: <short title>

## Decision
<one clear sentence>

## Original Premise
<starting frame>

## Premise Challenge
<what changed or survived>

## Context Type
<clear, complicated, complex, chaotic, or confused; include effect on decision style>

## Criteria
<must-have constraints and weighted wants>

## Roles
<owner, decider, contributors, implementers, and people to inform>

## Assumptions And Unknowns
<claims relied on, missing facts, and invalidation conditions>

## Options Considered
<compact comparison of viable options>

## Evaluation
<comparison against criteria, risks, reversibility, opportunity cost, uncertainty, and context fit>

## Rejected Alternatives
<serious contenders rejected and why>

## Recommendation
<chosen path and why>

## Risks And Mitigations
<major risks, failure modes, and mitigations>

## Premortem
<why this might fail and whether that changes the recommendation>

## Confidence
<low, medium, or high, plus why>

## Reversibility
<one-way door, two-way door, or mixed>

## What Would Change This Decision
<decision triggers>

## Next Action
<first concrete step>

## Review Date
<YYYY-MM-DD or not needed>
```

#### 7. Save

If the user asks to save, finalize, journal, or record the decision:

1. Ensure `~/.thinking-sessions/decision-system/` exists.
2. Generate title, 3-5 word lowercase hyphenated slug, 2-5 lowercase
   hyphenated tags, and review date as ISO `YYYY-MM-DD` or `null`.
3. Write to `~/.thinking-sessions/decision-system/YYYY-MM-DD-<slug>.md`;
   append `-2`, `-3`, etc. to avoid collisions.
4. Use frontmatter:

```markdown
---
title: "<title>"
created: <current ISO 8601 timestamp>
updated: <current ISO 8601 timestamp>
status: active
tags: [<generated tags>]
review: <YYYY-MM-DD or null>
---
```

Tell the user: "Decision saved to
`~/.thinking-sessions/decision-system/<filename>`."

### List Decisions

List `.md` files in `~/.thinking-sessions/decision-system/` whose frontmatter
has `title` and `status`. Sort newest first, max 20:

```text
YYYY-MM-DD  [status]  title
```

If none exist, say: "No saved decisions yet. Start one by asking for the
decision system."

### Continue Decision

Find the decision by partial slug match. If one match, load it; if multiple,
ask the user to pick; if none, say no match and suggest `list decisions`.

Then:

1. Summarize the existing decision, confidence, and decision triggers.
2. Ask what changed: new evidence, changed criteria, changed context, or
   reframing.
3. Re-run only affected sections.
4. On save, overwrite the file and update `updated`.

### Review Decision

Find the saved decision using the same matching logic. Review process quality
separately from outcome using Decision Journal discipline:

- outcome
- assumptions right/wrong
- decision triggers fired
- whether reasoning was sound given what was known
- outcome quality: good, bad, mixed, or unknown
- what should change next time

If complete, set `status: reviewed`, add `reviewed: <current ISO 8601
timestamp>`, update `updated`, and save.

## Guardrails

The AI should:

- challenge the premise before evaluating options
- separate original premise from stabilized decision
- distinguish constraints from assumptions and musts from wants
- identify owner/roles, uncertainty, reversibility, and opportunity cost
- scale rigor to stakes and reversibility
- evaluate viable options before recommending
- run a premortem before finalizing
- recommend discovery rather than pretend to decide when evidence is missing
- end with a recommendation or a clear reason no decision should be made

The AI should not accept the first framing too quickly, compare options before
criteria are explicit, write a memo before recommendation, hide weak evidence
behind confidence, judge decision quality only by outcome, or force closure
when learning is the correct next step.

## Invocation

Apply this skill to the user's decision: adversarial exploration, frame
stabilization, options, evaluation, recommendation, then memo/save/review when
requested.
