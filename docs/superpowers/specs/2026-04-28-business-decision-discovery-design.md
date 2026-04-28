# Business Decision Discovery Design

## Purpose

Add a `business-decision-discovery` skill for pre-decision discovery. The skill
helps an agent clarify a vague, high-stakes, or multi-stakeholder business
decision before option evaluation begins. It should produce a structured
discovery brief, not a recommendation.

The skill sits before `decision-system` in the workflow. It discovers whether
there is a real decision to make, what business need and value are at stake,
which stakeholders matter, what evidence exists, what is still unknown, and
what discovery work is needed next.

## Scope

In scope:

- Create `skills/business-decision-discovery/SKILL.md`.
- Update `README.md` so users can distinguish this skill from
  `decision-system`, `business-requirements-extraction`, and
  `business-rules-extraction`.
- Ground the skill in established business decision and business analysis
  practices.
- Include a decision-readiness gate that classifies the situation as ready for
  decision, needing targeted discovery, needing reframing, or needing a split or
  deferral.

Out of scope:

- Do not create scripts, assets, or reference files unless implementation shows
  a clear need.
- Do not make the skill produce final recommendations by default.
- Do not change existing business extraction or decision-system behavior.
- Do not add agent UI metadata unless the repository pattern changes.

## Positioning

Use `business-decision-discovery` when the user needs to prepare a business
decision before deciding. Examples include market entry, pricing, vendor choice,
build/buy, operating model changes, major process changes, strategic
prioritization, or other business choices where the frame and evidence are not
yet stable.

Use `decision-system` when the decision frame is ready enough to compare
options and recommend a path.

Use `business-requirements-extraction` when the goal is a requirements catalog.
Use `business-rules-extraction` when the goal is a rule catalog.

## Grounding

The skill should use the following practices as internal scaffolding:

- IIBA/BACCM: analyze change, need, solution, stakeholder, value, and context.
- Decision Quality: check frame, alternatives, information, values and
  tradeoffs, reasoning readiness, and commitment to action.
- Cynefin/OODA: classify the context as clear, complicated, complex, chaotic, or
  confused and choose a matching discovery style.
- WRAP: widen the frame, reality-test assumptions, attain distance, and prepare
  to be wrong.
- Kepner-Tregoe-style separation of must-have constraints from weighted wants.
- Premortem and assumption testing: expose failure modes before committing to a
  decision process.

The skill should not require citations in ordinary use, but its instructions
should name the practices so future agents understand the provenance of the
workflow.

## Workflow

The skill should run this flow:

1. **Scope the decision candidate.** Identify whether the user has provided a
   decision, problem, proposed solution, research question, or conflict. If
   source material is missing and materially needed, ask for it.
2. **Map business context.** Capture change, need, stakeholder, value, solution
   candidates, and operating context. Separate current state from desired
   future state.
3. **Identify roles and stakeholders.** Capture owner, decider, contributors,
   approvers, implementers, affected stakeholders, blockers, and people to
   inform.
4. **Stabilize the frame.** Define the decision question, boundaries, timing,
   stakes, must-have constraints, wants, success measures, assumptions,
   unknowns, risks, dependencies, and reversibility.
5. **Inventory evidence.** Separate authoritative, stakeholder, behavioral, and
   speculative evidence. Record contradictions and missing evidence.
6. **Choose discovery style.** Use context type:
   - Clear: confirm facts and constraints quickly.
   - Complicated: analyze and bring in expertise.
   - Complex: run probes, interviews, experiments, and learning loops.
   - Chaotic: recommend stabilization before discovery.
   - Confused: decompose into smaller decision areas.
7. **Build discovery backlog.** List questions, evidence to collect,
   stakeholders to interview, analyses to run, experiments to perform, and
   validation criteria.
8. **Assess readiness.** Classify the decision as ready for `decision-system`,
   needing targeted discovery, needing reframing, or needing split/defer. Give a
   concise rationale and next action.

## Output Format

Default to a discovery brief:

```markdown
# Business Decision Discovery: <topic>

## Scope
<decision candidate, intended use, source material, exclusions>

## Source Inventory
| Source | Evidence Level | Notes |
|---|---|---|

## Business Context
| Concept | Finding | Confidence |
|---|---|---|
| Change | ... | ... |
| Need | ... | ... |
| Stakeholders | ... | ... |
| Value | ... | ... |
| Solution Candidates | ... | ... |
| Context | ... | ... |

## Stakeholders And Roles
| Stakeholder / Role | Interest | Influence | Needed From Them |
|---|---|---|---|

## Decision Frame
| Element | Finding |
|---|---|
| Decision Question | ... |
| Owner / Decider | ... |
| Timing / Stakes | ... |
| Must-Have Constraints | ... |
| Wants / Criteria | ... |
| Success Measures | ... |
| Assumptions | ... |
| Unknowns | ... |
| Risks | ... |
| Reversibility | ... |
| Context Type | ... |

## Option Space
<visible options or option families to investigate, without recommendation>

## Contradictions And Tensions
| Topic | Tension | Sources | Discovery Needed |
|---|---|---|---|

## Discovery Backlog
| Priority | Question / Activity | Method | Owner | Decision Impact |
|---|---|---|---|---|

## Readiness Assessment
<ready for decision-system / targeted discovery needed / reframe needed / split or defer>

## Handoff To Decision-System
<what frame, criteria, evidence, and options should carry forward>
```

## Quality Bar

A good output:

- does not recommend before the discovery frame is ready
- separates decision, problem, proposed solution, and research question
- makes stakeholders and decision ownership explicit
- links value to stakeholder and context
- distinguishes must-have constraints from wants
- separates evidence from assumptions and unknowns
- identifies contradictions instead of smoothing them over
- scales discovery style to context and uncertainty
- ends with a practical next discovery action or a handoff to `decision-system`

## Implementation Notes

Keep the skill concise and similar in style to the existing repository skills.
Use one `SKILL.md` file unless the body grows large enough to justify
references. Avoid changing the existing skills except for README positioning.
