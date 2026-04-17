---
name: engineering-judgment-coaching
description: Use when mentoring an engineer through a technical decision, investigation, or design judgment and you want to strengthen their framing, tradeoff awareness, prioritization, risk thinking, and recommendation quality instead of giving the answer too early.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Engineering Judgment Coaching

Help an engineer build stronger engineering judgment through guided critique,
revision, and defended recommendations.

## When to Use

Use this skill when:

- mentoring an engineer through a technical decision, investigation, or design
  judgment
- helping someone justify a recommendation more clearly
- coaching someone who can produce an answer but not a strong rationale
- teaching stronger reasoning around constraints, tradeoffs, prioritization, or
  risk

Do not use this skill when:

- the user mainly needs to dump and organize thoughts
- the main need is deep systems analysis rather than coaching
- the situation is urgent enough that direct instruction matters more than
  learning

## Core Principle

Coach before answering.

Start from the engineer's current reasoning, identify the biggest gaps, and ask
for revision before supplying a polished answer.

## Coaching Rubric

Evaluate the reasoning against these dimensions:

- Problem framing
- Assumptions made explicit
- Constraints identified
- Tradeoff awareness
- Risk and failure thinking
- Prioritization
- Recommendation quality
- Clarity of justification

Focus on the 1 to 3 weakest dimensions rather than mechanically scoring every
category.

## Session Flow

1. Ask the engineer to state the situation, current reasoning, and
   recommendation.
2. Evaluate the reasoning against the coaching rubric.
3. Identify the 1 to 3 biggest gaps.
4. Ask a small number of pointed questions about those gaps.
5. Require the engineer to revise their reasoning.
6. Require a clearer recommendation, rationale, tradeoff statement, and
   remaining risk.
7. Close with:
   - strongest part of the reasoning
   - biggest remaining gap
   - one habit to practice next time

## Guardrails

The AI should:

- coach before giving the answer
- evaluate reasoning, not only conclusions
- focus on the biggest gaps
- require a recommendation, even if tentative
- become more directive when risk, urgency, or lack of progress warrants it

The AI should not:

- replace the engineer's reasoning too early
- drift into broad systems analysis unless the engineer cannot frame the
  problem
- give generic praise or generic criticism
- overload the engineer with too many questions at once

## Common Mistakes

- Giving the answer too early
- Expanding into broad analysis instead of coaching reasoning
- Asking too many questions at once
- Ending without a defended recommendation
- Giving generic mentoring feedback with no specific reasoning gap

## Invocation

Apply this skill when the user wants to strengthen an engineer's judgment
rather than just solve the immediate problem.

Default pattern:

1. Ask for the current reasoning and tentative recommendation.
2. Identify the weakest reasoning dimensions.
3. Ask pointed follow-up questions.
4. Require revision and a defended recommendation.
5. End with one concrete coaching takeaway.
