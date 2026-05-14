---
name: person-skill-distillation
description: Use when the user wants to distill a person's expertise, taste, judgment, workflow, decision rules, or tacit know-how from interviews, writing, work artifacts, examples, observations, or transcripts into a reusable skill profile, training guide, prompt, rubric, or AI skill file.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Person Skill Distillation

Distill a person's skill into explicit, reusable operating knowledge. The goal
is not biography or personality profiling. The goal is to capture what the
person repeatedly notices, decides, does, avoids, checks, and improves so
someone else or an AI agent can perform closer to their standard.

Use cognitive task analysis as the backbone: reveal the hidden perception,
judgment, decisions, strategies, and mental representations behind expert
performance, then convert them into transfer material.

## Use For

Use this skill when the user wants to:

- extract someone's expertise from interviews, notes, recordings, writing, or
  work samples
- understand how a person gets unusually good results
- codify a founder, operator, designer, engineer, salesperson, researcher,
  teacher, coach, or domain expert's judgment
- turn tacit taste into principles, rubrics, examples, prompts, or training
  material
- create a reusable AI `SKILL.md` based on how a person works

Do not use this for medical, psychological, legal, employment, or surveillance
judgments about a person. Do not infer sensitive traits, diagnoses, motives, or
private facts. Label all inferences and keep them tied to evidence.

## Core Principle

Distill from evidence, not aura.

Every useful claim should connect to at least one concrete source: an example,
artifact, quote, decision, correction, repeated behavior, or observed contrast
between the person and a less skilled baseline.

## Method Backbone

Use these practices as defaults:

- **Cognitive Task Analysis:** focus on the cognitive demands of the work, not
  just visible steps. Extract cues, goals, tradeoffs, uncertainty, strategies,
  and knowledge that shape performance.
- **Critical Decision Method:** anchor interviews in a real incident where the
  person made a consequential judgment. Reconstruct the timeline, cues,
  options considered, information used, uncertainty, and what would have changed
  the decision.
- **Knowledge Audit:** ask for expertise indicators: anomalies noticed,
  difficult discriminations, workarounds, opportunities, common traps, leverage
  points, and situations where novices get misled.
- **Think-aloud and artifact review:** have the person walk through real work
  while explaining what they inspect, ignore, compare, question, and revise.
- **Contrast cases:** compare excellent, average, poor, edge-case, and failed
  examples. Tacit standards become clearer at the boundaries.
- **Cognitive apprenticeship:** make expert cognition transferable through
  modeling, coaching, scaffolding, articulation, reflection, and exploration.
- **Deliberate practice:** convert the distillation into drills with clear
  subskills, immediate feedback, repetition, and increasing difficulty.

## Inputs

Ask for the smallest missing input needed to proceed. Useful inputs include:

- the target person and domain of skill
- what the distilled skill should be used for
- interviews, transcripts, notes, essays, emails, code, designs, decisions,
  sales calls, reviews, teaching sessions, or shipped work
- examples of excellent, average, and poor work in the person's domain
- moments where the person corrected someone else's work
- known constraints, audience, standards, and success criteria

If the user has no artifacts yet, run an interview instead of blocking.

## Workflow

### 1. Frame The Distillation

Define:

- **Person:** whose skill is being distilled
- **Performance surface:** the specific arena, not a broad title
- **Purpose:** why the distillation matters
- **Output:** profile, rubric, training plan, prompt, checklist, or `SKILL.md`
- **Evidence:** what sources are available
- **Skill transfer target:** human training, AI behavior, hiring/evaluation,
  documentation, succession, or self-improvement
- **Boundary:** what should not be inferred or copied

If the domain is too broad, narrow it to a concrete performance surface:

```text
Too broad: "Steve's product sense"
Better: "How Steve evaluates early B2B SaaS feature ideas before build"
```

### 2. Sample The Evidence

Use at least two evidence types when possible:

- **Incidents:** real moments with stakes, uncertainty, or correction
- **Artifacts:** work outputs, drafts, reviews, decisions, tools, templates
- **Contrasts:** excellent vs average vs poor examples
- **Observation:** live walkthrough, shadowing, think-aloud, or screen review
- **Commentary:** interviews, notes, essays, talks, recorded explanations

Avoid relying only on the person's self-description. Experts often automate
important distinctions and may omit the cues they actually use.

### 3. Build An Evidence Table

Extract compact evidence before interpreting it. Keep claims source-linked.

```text
Source | Situation | Cue noticed | Goal/tradeoff | Action/decision | Result | Skill signal | Confidence
```

Prefer recurring signals over isolated anecdotes. Mark weak signals as
`tentative`.

### 4. Reconstruct Critical Incidents

For consequential moments, run a short Critical Decision Method pass:

```text
Timeline: What happened, in order?
Cues: What did they notice first, and what changed their interpretation?
Goals: What were they optimizing and protecting?
Options: What did they consider, reject, or never consider?
Uncertainty: What was missing, ambiguous, risky, or time-sensitive?
Decision point: What made the chosen move preferable?
Counterfactuals: What would have changed the decision?
Novice contrast: What would a competent novice likely miss?
```

Extract decision requirements, not just the final decision.

### 5. Run A Knowledge Audit

Probe for expertise that rarely appears in ordinary process descriptions:

- **Cues and patterns:** What small signal changes the interpretation?
- **Anomalies:** What feels wrong before there is proof?
- **Edge cases:** Where do normal rules fail?
- **Tradeoffs:** What must be sacrificed to preserve what matters more?
- **Workarounds:** What do they do when the standard process breaks?
- **Leverage:** Which intervention changes the most with the least force?
- **Traps:** What looks correct to novices but creates later damage?
- **Calibration:** How do they know when confidence is too high or too low?
- **Recovery:** How do they detect and correct mistakes?

### 6. Identify The Skill Stack

Break the person's skill into layers:

- **Perception:** what they notice that others miss
- **Classification:** how they categorize situations
- **Standards:** what "good" and "bad" mean to them
- **Decision rules:** how they choose under uncertainty
- **Mental representations:** the internal model, map, schema, or chunking
  system they use to simplify complexity
- **Sequence:** the order they do things in
- **Tools and artifacts:** templates, questions, diagrams, scripts, checks
- **Taste:** preferences that produce better work, stated as criteria
- **Failure modes:** what they avoid, catch, or correct early
- **Feedback loops:** how they learn and improve the work

Separate:

- observed behavior
- stated belief
- inferred heuristic
- speculative interpretation

### 7. Contrast Against A Baseline

Explain what the person does differently from a competent average practitioner.

Use this format:

```text
Average move: <common behavior>
Person's move: <distinct behavior>
Why it matters: <effect on outcome>
Evidence: <source>
```

This is often where tacit skill becomes visible.

### 8. Distill Operating Principles

Turn patterns into principles that are specific enough to change behavior.

Bad principle:

```text
Care about quality.
```

Good principle:

```text
Before improving a solution, challenge whether the user's stated request is the
real job. If the request is a proposed solution, restate the underlying decision
or need first.
```

For each principle, include:

- when to apply it
- what to do
- what to avoid
- a concrete example
- confidence: high, medium, or low

### 9. Convert To Transfer Material

Choose the output that matches the user's goal.

#### Skill Profile

```markdown
# <Person> Skill Profile: <Domain>

## Distilled Capability
<one-paragraph summary>

## Evidence Base
<sources and confidence>

## Skill Stack
<perception, classification, standards, decisions, sequence, tools, taste,
failure modes, feedback loops>

## Critical Incidents
<key moments and decision requirements extracted from them>

## Operating Principles
<specific reusable principles>

## Rubric
<criteria for evaluating work in this person's style>

## Examples
<excellent/average/poor examples or reconstructed examples>

## Practice
<exercises to develop the skill>

## Limits
<where this distillation is weak, context-bound, or speculative>
```

#### AI Skill Draft

When the user wants a reusable AI skill, produce a concise `SKILL.md` with:

- frontmatter `name` and `description`
- when to use and when not to use
- core principle
- required inputs
- workflow
- output formats
- verification or quality checks

Do not write a fan profile. Encode behaviors an agent can perform.

#### Training Or Practice Plan

When the user wants skill transfer to a person, create:

```markdown
## Subskills
<small trainable components>

## Demonstrations
<expert examples with commentary>

## Drills
<repeated practice tasks with increasing difficulty>

## Feedback
<what good feedback looks like and when it should arrive>

## Rubric
<observable criteria for improvement>

## Fading Support
<how scaffolding is removed as competence increases>
```

#### Interview Guide

If evidence is thin, produce questions designed to reveal tacit skill:

- "Show me a recent piece of work you think is excellent. What makes it good?"
- "What would a novice miss here?"
- "Where would you intervene first, and why?"
- "What do you check before you trust the result?"
- "What are common fixes that look right but make things worse?"
- "Walk me through the last time you changed your mind."
- "What examples define the edges of good, acceptable, and unacceptable?"
- "Tell me about a time the standard process failed. What did you do instead?"
- "What early signal tells you this will become expensive later?"
- "What would make you reverse your recommendation?"

### 10. Verify The Distillation

Before finalizing, check:

- Is each major claim grounded in evidence?
- Are inferences labeled?
- Can the output change someone else's behavior?
- Does it include cues, decisions, standards, feedback, and failure modes rather
  than only abstract values?
- Does it preserve the person's standards without mimicking their identity?
- Are sensitive, private, diagnostic, or unsupported claims excluded?
- Are the limits of the evidence explicit?
- Has the skill been tested against at least one realistic example, contrast
  case, or simulation?

If the output is a `SKILL.md`, mentally simulate a new agent using it on a
realistic task. Tighten vague instructions until the agent would know what to
do.

## Default Output

If the user does not specify a format, return:

1. a compact skill profile
2. 5-10 operating principles
3. a rubric for recognizing the skill in action
4. the evidence gaps that would improve the distillation
