# Business Decision Discovery Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a lightweight `business-decision-discovery` skill that groups requirements and rules into operational business decisions, input data, outcomes, decision logic, gaps, and validation scenarios.

**Architecture:** Follow the existing repo pattern: one skill directory containing a single `SKILL.md`, plus README positioning. Keep the skill distinct from requirements extraction, rules extraction, and strategic decision support.

**Tech Stack:** Markdown skills, repository README, shell validation with `rg`, `sed`, and git diff.

---

### Task 1: Create The Skill

**Files:**
- Create: `skills/business-decision-discovery/SKILL.md`

- [x] **Step 1: Create the skill directory**

Run: `mkdir -p skills/business-decision-discovery`

- [x] **Step 2: Add `SKILL.md` with complete instructions**

Create `skills/business-decision-discovery/SKILL.md` with frontmatter:

```yaml
---
name: business-decision-discovery
description: Use when discovering, extracting, modeling, or documenting operational business decisions from requirements, rules, policies, workflows, code, specs, tickets, data, or stakeholder notes. Produces decision catalogs, decision tables, input data, outcomes, rules used, gaps, conflicts, and validation scenarios.
metadata:
  author: Felix Heinonen
  version: "0.1.0"
---
```

Body sections to include:

- Purpose: missing middle layer between requirements and rules.
- Core principle: decisions answer a business question by applying data and rules to produce outcomes.
- Mental model: `Requirement -> Decision -> Rules + Data -> Outcome`.
- Decision types: approval, routing, eligibility, classification, pricing, prioritization, calculation, assignment, notification, blocking/permitting.
- Workflow: scope, candidate decisions, outcomes, inputs, rules, logic, gaps/conflicts, validation scenarios.
- Output format: decision catalog, decision details, decision logic table, gaps/conflicts, validation scenarios, cross-decision issues.
- Quality bar: lightweight, traceable, explicit inputs/outcomes, rule grouping, testable scenarios.
- Guardrails: no strategic recommendation, no full requirements catalog, no full rule catalog, no formal DMN unless requested.

- [x] **Step 3: Inspect the skill for frontmatter and structure**

Run: `sed -n '1,260p' skills/business-decision-discovery/SKILL.md`

Expected: frontmatter is valid YAML; body includes workflow and output format.

### Task 2: Update README Positioning

**Files:**
- Modify: `README.md`

- [x] **Step 1: Add the skill to the top list**

Add:

```markdown
- `business-decision-discovery` for discovering operational decisions from
  requirements, rules, data, outcomes, and validation scenarios
```

- [x] **Step 2: Add the layer distinction**

Add a short section near "Which Skill To Use":

```markdown
## Requirements, Rules, And Decisions

| Thing | Question It Answers | Example |
|---|---|---|
| Requirement | What does the business need? | Prevent unauthorized payments |
| Rule | What policy or constraint applies? | Invoices over EUR 5,000 need approval |
| Decision | What outcome must be chosen? | Should this invoice be approved, reviewed, or rejected? |
| Decision table | How is the outcome chosen? | If amount > EUR 5,000, route to manager |
| Test scenario | How do we verify it? | Invoice EUR 5,001 routes to manager |
```

- [x] **Step 3: Add "Use business-decision-discovery when"**

Add bullets that mention discovering decisions, grouping rules by decision, identifying input data and outcomes, building decision tables, and generating validation scenarios.

- [x] **Step 4: Add side-by-side workflow copy**

Add a compact explanation that it takes extracted requirements/rules and creates decision models such as invoice approval route.

### Task 3: Validate The Skill

**Files:**
- Read: `skills/business-decision-discovery/SKILL.md`
- Read: `README.md`

- [x] **Step 1: Check for unwanted heavyweight framing**

Run:

```bash
rg -n "Cynefin|WRAP|Kepner|executive|strategy framework|recommendation first|decision-system handoff" skills/business-decision-discovery README.md
```

Expected: no matches except harmless README mentions of `decision-system`.

- [x] **Step 2: Check for required decision modeling vocabulary**

Run:

```bash
rg -n "Decision Catalog|Decision Logic|Validation Scenarios|Inputs|Outcomes|Rules Used|Requirement -> Decision -> Rules \\+ Data -> Outcome" skills/business-decision-discovery/SKILL.md
```

Expected: matches for all required sections or phrases.

- [x] **Step 3: Check git diff**

Run: `git diff -- README.md skills/business-decision-discovery/SKILL.md`

Expected: diff contains only the new skill and README positioning.

### Task 4: Commit Implementation

**Files:**
- Add: `skills/business-decision-discovery/SKILL.md`
- Modify: `README.md`

- [x] **Step 1: Stage only intended files**

Run:

```bash
git add skills/business-decision-discovery/SKILL.md README.md docs/superpowers/plans/2026-04-28-business-decision-discovery.md
```

- [x] **Step 2: Commit**

Run:

```bash
git commit -m "feat: add business decision discovery skill"
```

- [x] **Step 3: Confirm remaining worktree state**

Run: `git status --short`

Expected: only pre-existing unrelated changes remain, especially `skills/business-requirements-extraction/SKILL.md` if still modified.
