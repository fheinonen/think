---
name: systemic-thinking
description: Use when analyzing complex problems with interacting parts, unclear boundaries, incomplete information, or multiple plausible interpretations that require structured decomposition before synthesis.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---

# Systemic Thinking

Use a rigorous systemic-thinking method to analyze a problem without jumping too
quickly to a global explanation.

Sessions are saved as portable markdown files in
`~/.thinking-sessions/systemic-thinking/`.

## Modes

Determine the mode from the user's request before starting. If unclear, default
to **New Session**.

### New Session

The user wants to analyze a new problem.

**Step 1 - Capture the problem.**
If the user's request already contains enough problem/context and goals or
constraints to begin, use that directly.

Otherwise, ask the user for the problem/context and any goals or constraints.

Collect the user's full response before analyzing. Do not interrupt with
partial analysis.

If the response is empty or too short to identify a real problem, ask again.

**Step 2 - Decide the analysis mode.**
Choose **Analyze Now** or **Clarify First** using the decision rules below.

**Step 3 - Produce the analysis.**
Generate the full A-L analysis using the same A-L headings and section content
defined in Save Format below, even when the analysis is only being shown
inline and not saved.

**Step 4 - Generate metadata.**
From the problem and analysis, generate:
- **Title:** a short descriptive title for the session
- **Slug:** 3-5 words, lowercase, hyphenated
- **Tags:** 2-5 lowercase hyphenated tags from the domain, context, and topic

**Step 5 - Refine.**
After presenting the analysis, ask:

> Want to refine? You can:
> - Add more context
> - Ask me to revisit a section
> - Ask me to compare models differently
> - Say "save" to finalize

If the user adds context, revisit the analysis with the new information.

If the user says "save" or "done", proceed to the save step.

### List Sessions

The user wants to see saved systemic-thinking sessions.

List all `.md` files in `~/.thinking-sessions/systemic-thinking/`. For each
file, read the YAML frontmatter. Only include files that have both `title` and
`status` fields.

Sort by filename (newest first). Show max 20 entries.

Output format, one line per session:

```
YYYY-MM-DD  [status]  title
```

If the directory does not exist or is empty, say:
"No systemic-thinking sessions yet. Start one by asking for a systemic analysis."

### Continue Session

The user wants to continue an existing systemic-thinking session.

Find the session file matching the user's description. Search filenames in
`~/.thinking-sessions/systemic-thinking/` for a partial match on the slug.

- If exactly one file matches: load it.
- If multiple files match: list them and ask the user to pick.
- If no files match: say "No session found matching that. Run 'list sessions' to see available sessions."

Once loaded:
1. Read the saved analysis and present a concise summary of the existing model.
2. Ask whether the user wants to review it as-is, add new context, revise a
   section, or save or resolve it.
3. If the user adds new context or requests revisions, incorporate the new
   information and regenerate the A-L analysis.
4. If the user only wants to inspect the existing analysis, do not regenerate
   it yet.
5. Enter the refine step from New Session.
6. On save: overwrite the file and update the `updated` timestamp in frontmatter.

### Resolve Session

The user wants to mark a systemic-thinking session as done.

Find the session file using the same matching logic as Continue Session.

Once found:
1. If the session is already `status: resolved`, tell the user it is already resolved and take no action.
2. Update the frontmatter: set `status: resolved` and add `resolved: <current ISO 8601 timestamp>`.
3. Update the `updated` timestamp.
4. Save the file.
5. Tell the user: "Session '<title>' marked as resolved."

### Analyze Now

Use this mode when missing context would not materially change the analysis.

Proceed with the full A-L structure and make any assumptions explicit in the
epistemic map, open questions, and synthesis.

### Clarify First

Use this mode when missing context would materially change the plausible
models, eliminations, or recommended next steps.

Treat missing context as material when any of these are true:

- It could add or remove a major actor, boundary, constraint, or dependency.
- It could change which models remain plausible.
- It could reverse an elimination decision.
- It could change the recommended next steps in a substantive way.

Ask only the minimum necessary clarifying questions, then continue with the
full A-L structure.

### Save Format

On save, ensure the directory `~/.thinking-sessions/systemic-thinking/` exists.

Write the session file to:
`~/.thinking-sessions/systemic-thinking/YYYY-MM-DD-<slug>.md`

If a file with that name already exists, append `-2` (or `-3`, etc.) to the
slug to avoid collision.

The file format is:

```markdown
---
title: "<title>"
created: <current ISO 8601 timestamp>
updated: <current ISO 8601 timestamp>
status: active
tags: [systems, analysis, planning]
---

## Problem Context

<user's problem statement, goals, and constraints>

## Analysis

### A. Problem restatement
<concise framing of the user's stated problem and goals; final framing for the analysis>

### B. Small local notes
<local observations, entities, components, constraints, and relationships from method steps 1 and 2>

### C. Ontological map
<objects, processes, states, and system boundaries from method step 3 using the ontological lens>

### D. Epistemic map
<known, assumed, inferred, unknown, and uncertain points from method step 3 using the epistemic lens>

### E. Morphological possibilities
<possible configurations, structures, and solution shapes from method step 3 using the morphological lens>

### F. MECE structure
<mutually exclusive, collectively exhaustive organization from method step 4>

### G. Semiotic analysis
<semantics, syntactics, and pragmatics from method step 5>

### H. Eliminated options and why
<ruled-out options with reasons from method step 6>

### I. Remaining plausible models
<models still supported by the evidence after method step 6>

### J. Conflicts, uncertainties, and open questions
<contradictions, unresolved uncertainties, and next questions from method steps 7, 8, and 9>

### K. Consolidated synthesis
<integrated model built from the surviving evidence in method step 10>

### L. Recommended next steps
<actionable follow-up steps derived from method step 10>
```

Tell the user: "Session saved to `~/.thinking-sessions/systemic-thinking/<filename>`."

## Instructions

When this skill is invoked, analyze the user's problem with the following
method.

### Method

1. Break the problem into many small, local notes rather than jumping to a
   global theory.
2. Identify entities, components, actors, variables, constraints,
   dependencies, and relationships.
3. Apply these lenses:
   - Ontological clarity: What exists in this system? What are the relevant
     objects, processes, states, and boundaries?
   - Epistemic clarity: What is known, unknown, assumed, inferred, uncertain,
     or missing?
   - Morphological clarity: What possible configurations, structures,
     combinations, or solution shapes exist?
4. Organize the analysis using MECE principles:
   - Mutually Exclusive: categories should not overlap unnecessarily.
   - Collectively Exhaustive: categories should cover the relevant space.
5. Apply semiotic analysis:
   - Semantics: What do the key terms mean?
   - Syntactics: How do the parts relate structurally?
   - Pragmatics: What are the functional consequences in practice?
6. Use deductive elimination to rule out weak, contradictory, impossible, or
   less plausible options.
7. Avoid premature global explanations. Build upward from local observations.
8. Periodically summarize findings, check for contradictions, resolve
   conflicts, and consolidate into a clearer model.
9. If multiple interpretations are possible, keep them separate until evidence
   supports one over the others.
10. End with a structured synthesis.

### Epistemic Map Format

Structure the epistemic map with these labels when relevant:

- Known: directly stated facts or established constraints.
- Assumed: working assumptions used to proceed. For each one, state why it is
   being assumed and what kind of evidence would invalidate it.
- Inferred: conclusions derived from the known facts.
- Unknown: information that is missing but not yet answerable from the
   current context.
- Uncertain: points where evidence exists but remains ambiguous or contested.

Use section J for open questions that should be resolved next. Do not merge
open questions into the assumptions list.

## Invocation

Apply this skill to the user's stated problem and any additional goals or
constraints they provide.

Follow the session modes, analysis mode selection, and method defined above.
