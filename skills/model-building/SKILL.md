---
name: model-building
description: Use when a user wants to understand an external or internal system well enough to identify variables, parameters, feedback loops, constraints, levers, experiments, and model weaknesses.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Model Building

Build explicit conceptual models that reveal what can be observed, changed, or
tested. The goal is not a complete map of reality. The goal is a useful control
surface: a representation clear enough to expose parameters, leverage points,
limits, risks, and experiments.

Use this for external systems such as products, businesses, markets,
organizations, workflows, codebases, and ecosystems. Also use it for internal
systems such as attention, motivation, habits, avoidance patterns, identity
pressure, decision behavior, and learning loops.

## When To Use

Use this skill when the user:

- wants to understand how a thing works so they can change it
- says their current mental model limits what they can see or modify
- wants parameters, levers, feedback loops, or intervention points
- needs to compare different conceptual models of the same system
- wants to test whether an explanation is useful or misleading
- is dealing with recurring behavior, system behavior, organizational dynamics,
  product dynamics, or complex personal patterns

Do not use this skill when:

- the user only wants a thought dump organized; use `think`
- the user mainly needs broad structured analysis; use `systemic-thinking`
- the user needs a decision recommendation; use `decision-system`
- the user needs low-stakes action pressure; use `action-activation`
- medical, legal, financial, safety, or mental-health stakes require expert
  guidance rather than informal modeling

## Core Principle

Do not stop at explanation.

Convert the explanation into a model with observable variables, modifiable
parameters, constraints, feedback loops, leverage points, intervention
hypotheses, and tests that would update the model.

## Operating Rules

- Start with the modeling purpose. A model for intervention is different from a
  model for explanation, prediction, communication, or self-reflection.
- Make boundaries explicit. Name what is inside, outside, and ambiguous.
- Treat the user's current mental model as evidence, not truth.
- Keep competing models alive until evidence rules them out.
- Label confidence. Separate known, assumed, inferred, speculative, unknown,
  and contested claims.
- Prefer small useful models over encyclopedic maps.
- Distinguish shallow parameter changes from deeper leverage points such as
  information flows, rules, goals, incentives, identity, and paradigms.
- For internal systems, avoid diagnosis. Model patterns, contexts, incentives,
  and feedback loops without assigning clinical labels.

## Session Flow

### 1. Establish Purpose

Clarify the modeling target and why the model is being built.

If the prompt already contains enough context, proceed. Otherwise ask only the
minimum needed:

- What system or pattern are we modeling?
- What do you want the model to help you understand or change?
- What observations make this system interesting or frustrating?
- What have you already tried, and what happened?

State the purpose in one sentence:

```text
We are modeling <system> in order to <understand/change/predict/test> <target>.
```

### 2. Elicit The Current Mental Model

Extract how the user currently believes the system works.

Capture:

- current explanation
- assumed causes
- expected effects
- implicit boundaries
- words or metaphors shaping the model
- interventions the current model makes seem obvious

Then state:

```text
Current model: <compact explanation>
This model makes these levers visible: <levers>
This model hides or compresses: <blind spots>
```

### 3. Build The Explicit Model

Map the system using only the detail needed for the purpose.

Include:

- **Boundary:** inside, outside, ambiguous edge cases
- **Entities:** actors, components, resources, artifacts, environments
- **States:** meaningful conditions the system can be in
- **Variables:** values that change and matter
- **Parameters:** variables whose values shape behavior
- **Constraints:** limits, rules, capacities, dependencies, norms, beliefs
- **Flows:** movement of attention, money, information, work, energy, trust,
  demand, risk, or other relevant quantities
- **Feedback loops:** reinforcing loops, balancing loops, delays, thresholds,
  and unintended consequences

Use compact diagrams when helpful:

```text
input -> process -> output -> feedback
```

or:

```text
ambiguity -> threat -> avoidance -> short-term relief
     ^                              |
     |                              v
  pressure <- reduced progress <- reinforcement
```

### 4. Identify Parameters And Levers

Separate what can vary from what can be changed.

Use this table:

```text
Parameter | Observable? | Directly changeable? | Lever | Expected effect | Risk
```

Classify changeability:

- **Fixed:** not changeable in the relevant timeframe
- **Direct:** can be changed by an action
- **Indirect:** can be influenced through another variable
- **Emergent:** changes only through system-level conditions
- **Unknown:** not enough evidence yet

Then distinguish leverage depth:

- **Numbers:** values, quantities, thresholds
- **Buffers:** slack, reserves, capacity
- **Flows:** who gets what information, when, and in what form
- **Rules:** permissions, constraints, incentives, decision rights
- **Goals:** what the system optimizes
- **Paradigms:** the frame that defines what the system is and what matters

Do not assume the best lever is a numeric parameter. Often the stronger lever
is a rule, feedback flow, goal, or paradigm.

### 5. Stress-Test The Model

Look for where the model may mislead.

Check:

- What important behavior does this model fail to explain?
- What has to be true for this model to work?
- Which causal links are assumed rather than observed?
- Where are delays, nonlinearities, or thresholds likely?
- What intervention could backfire?
- What alternative model would explain the same observations?
- What would falsify or weaken this model?

Produce at least one competing model when the stakes or uncertainty are
material.

### 6. Design Model Tests

Convert the model into low-risk learning loops.

Each test should include:

```text
Hypothesis:
Intervention or observation:
Expected result:
Alternative result:
What each result would update:
Risk and reversibility:
```

Prefer small tests that reveal sensitivity:

- change one parameter
- observe whether the expected behavior changes
- keep the action reversible when possible
- avoid high-stakes experiments when evidence is weak

### 7. Produce The Final Model

End with a concise model that the user can hold in their head.

Use this structure:

```markdown
## Model Purpose

## Current Mental Model

## System Boundary

## Components And Dynamics

## Parameters And Levers

## Feedback Loops

## Model Weaknesses

## Competing Models

## Intervention Hypotheses

## Model Tests

## Updated Working Model
```

The **Updated Working Model** should be short enough to reuse:

```text
This system appears to work like <model>. The most important variables are
<variables>. The strongest current levers are <levers>. The biggest uncertainty
is <uncertainty>. The next best test is <test>.
```

## Common Mistakes

- Confusing a description of parts with a model of dynamics
- Treating the first explanation as the model
- Listing variables without identifying which are controllable
- Optimizing shallow parameters while ignoring rules, goals, incentives, or
  information flows
- Creating a map too large to use
- Hiding uncertainty behind clean causal language
- Giving advice before identifying the model's leverage points
- Modeling internal systems with moral labels instead of variables and loops

## Invocation

Apply this skill when the user asks to model, conceptualize, understand how
something works, identify parameters, find levers, change a system, improve a
mental model, or test an explanation.

Default pattern:

1. State the modeling purpose.
2. Extract the current mental model.
3. Build a bounded system model.
4. Identify variables, parameters, constraints, and feedback loops.
5. Separate modifiable levers from fixed or indirect factors.
6. Stress-test the model and compare alternatives.
7. Propose small tests that would update the model.
8. End with a compact working model.
