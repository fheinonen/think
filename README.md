# Think

This repository contains two local skills for structured reasoning:

- `think` for turning a messy thought dump into a usable breakdown
- `systemic-thinking` for analyzing a complex problem with explicit structure

They solve different stages of the same general problem. `think` is for getting
your thoughts out and organized. `systemic-thinking` is for disciplined
analysis once the problem needs a more formal model.

## Install

```bash
npx skills add fheinonen/think
```

## Which Skill To Use

### Use `think` when

- you have too many threads open at once
- you want to dump thoughts quickly without structuring them first
- you need the AI to identify threads, open questions, and action items
- you want to keep refining and save the session as markdown

### Use `systemic-thinking` when

- you want rigorous, explicitly structured analysis of the problem, models,
  uncertainties, synthesis, and next steps
- the problem has multiple interacting parts, actors, or constraints
- the boundaries are unclear or several interpretations are plausible
- you need assumptions, unknowns, and uncertainty separated explicitly

## Side-by-Side Workflow

### `think`

`think` helps you get messy thoughts out of your head and into a useful shape.

The workflow is simple:

1. Dump everything in one go.
2. The skill organizes it into a structured breakdown.
3. Add more thoughts, dig deeper on a thread, or reframe it.
4. Save when it looks right.

The output focuses on:

- a clear problem statement
- distinct threads
- open questions
- concrete action items

Sessions are stored as markdown files in `~/.thinking-sessions/`.

Example:

```text
/think

I need to migrate a client system next month. The database sync might be the
real bottleneck. We only have a 4 hour maintenance window. I am worried about
rollback if DNS cutover fails. Running both environments in parallel could get
expensive. I also do not know who owns the final go/no-go call.
```

### `systemic-thinking`

`systemic-thinking` is for deeper analysis when the problem needs explicit
reasoning structure.

The skill works in two modes:

1. Analyze now, if missing context would not materially change the analysis.
2. Clarify first, if missing context would change the plausible models,
   eliminations, or recommended next steps.

It then produces a structured analysis covering:

- problem restatement
- small local notes
- ontological, epistemic, and morphological analysis
- MECE structure and semiotic analysis
- eliminated options, plausible models, open questions, synthesis, and next
  steps

Use it when you want the agent to reason carefully rather than just organize a
brain dump.

## Common Prompts

### `think`

- "I need to think through something"
- "Expand thread 2"
- "Give me a different framing"
- "Continue the migration session"
- "List my thinking sessions"

### `systemic-thinking`

- "Use systemic thinking to analyze this migration plan"
- "Break this problem into local notes and map the unknowns"
- "Analyze this using ontological, epistemic, and morphological lenses"
- "Compare the plausible models and eliminate weak ones"

## License

MIT
