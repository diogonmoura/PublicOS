---
name: agent-builder
description: Use when you want to design a new skill or agent — it interviews you about the use case and recommends which workflow/agent pattern to use, then produces a SKILL.md skeleton and a rationale doc.
---

# Agent Builder

A Socratic interview skill. You describe a use case; Claude drills with follow-up questions until it can recommend the right pattern from the Anthropic "Building Effective Agents" framework, mapped to a staged-trust model (Manual → Trusted → Agent).

## Before you start

Read these reference files (they are the knowledge base for this skill):

1. `skills/agent-builder/references/when-to-use-agents-vs-workflows.md`
2. `skills/agent-builder/references/stage-mapping.md`
3. All five files in `skills/agent-builder/references/patterns/`

Do not proceed until you have read all seven files.

## Interview procedure

Ask the user to describe the use case in plain language. Then ask Socratic follow-up questions — **one at a time** — until you can confidently answer all four of these:

1. **Decomposability:** Are the steps predictable in advance, or do they depend on what earlier steps return?
2. **Feedback loop:** Does the task need to retry, evaluate, or refine based on output quality?
3. **Human review tolerance:** Does the user need to review every output, spot-check, or just approve?
4. **Trigger and frequency:** How does this run — on a schedule, on demand, or triggered by an event?

Do not ask all four questions at once. Follow the thread of the user's answers.

## Recommendation

Once you have enough signal:

1. Name the pattern (or combination of patterns).
2. Quote the relevant principle from the Anthropic article (use the pattern card's "When to use" section).
3. Map to the stage model using `stage-mapping.md`: stage to start at, model tier per step, safety defaults.
4. Note any ambiguities or open questions.

## Output artifacts

### 1. Rationale doc

Save to: `docs/superpowers/specs/YYYY-MM-DD-<use-case-name>-agent-design.md`

Template:
```
# <Use Case Name> — Agent Design

## Use case
<What the user described>

## Pattern chosen
<Pattern name>

## Why this pattern
<Anthropic article principle, quoted or paraphrased from the pattern card>

## Stage mapping
- **Start at stage:** <Stage 1 / 2>
- **Model tiers:** <table from stage-mapping.md, customised for this use case>
- **Safety defaults:** <from stage-mapping.md>

## Open questions
<Any ambiguities that need resolving before implementation>
```

### 2. SKILL.md skeleton

Save to: `skills/<use-case-name>/SKILL.md`

Template:
```
---
name: <use-case-name>
description: Use when… <complete this>
---

# <Skill Name>

## Status
Stage 1 (Manual) — invoke and review every output before use.

## Model tiers

| Step | Model | Why |
|------|-------|-----|
| <step> | <Haiku/Sonnet/Opus> | <reason> |

## Safety defaults
- <safety rule from stage-mapping.md>
- Show the user the draft before writing to any external system.

## Inputs
- <what the skill needs to run>

## Procedure

<Stub — fill in the concrete steps>

## Judgment rules

_(Empty — fill in as corrections are made.)_
```

## After generating artifacts

Commit both files:

```bash
git add docs/superpowers/specs/<rationale-doc>.md skills/<use-case-name>/SKILL.md
git commit -m "feat: add <use-case-name> agent design + skill skeleton"
```

Tell the user: "Skeleton is at `skills/<use-case-name>/SKILL.md`. Fill in the Procedure section and run it manually (Stage 1) — promote after 3 clean runs with no corrections."

## Judgment rules

_(Empty — fill in as corrections are made.)_
