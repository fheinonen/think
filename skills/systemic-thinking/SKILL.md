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

Default output is inline in the current response. Only persist the analysis if
the user explicitly asks to save it or another workflow requires persistence.

## When To Use

- Problems with many interacting variables, constraints, or stakeholders
- Situations where multiple interpretations seem plausible
- Cases where assumptions, unknowns, and dependencies need to be separated
- Analysis tasks that need a structured synthesis rather than a quick answer

## Modes

Determine the mode from the user's prompt before starting.

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

### Section Map

Use this mapping so the method and the output structure stay aligned.

- A. Problem restatement: concise framing of the user's stated problem and
   goals.
- B. Small local notes: output from steps 1 and 2.
- C. Ontological map: output from step 3 using the ontological lens.
- D. Epistemic map: output from step 3 using the epistemic lens.
- E. Morphological possibilities: output from step 3 using the morphological
   lens.
- F. MECE structure: output from step 4.
- G. Semiotic analysis: output from step 5.
- H. Eliminated options and why: output from step 6.
- I. Remaining plausible models: options left after step 6.
- J. Conflicts, uncertainties, and open questions: output from steps 7, 8,
   and 9.
- K. Consolidated synthesis: output from step 10.
- L. Recommended next steps: actionable follow-up from step 10.

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

### Output Format

Produce the analysis using these sections:

A. Problem restatement

B. Small local notes

C. Ontological map

D. Epistemic map

E. Morphological possibilities

F. MECE structure

G. Semiotic analysis

H. Eliminated options and why

I. Remaining plausible models

J. Conflicts, uncertainties, and open questions

K. Consolidated synthesis

L. Recommended next steps

## Invocation

Apply this skill to the user's stated problem and any additional goals or
constraints they provide.

- Choose Analyze Now or Clarify First before beginning.
- Keep alternative interpretations separate until evidence supports one over
   the others.
