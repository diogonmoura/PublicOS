# Prompt Chaining

## When to use

The task decomposes into a fixed, ordered sequence of sub-tasks where each step's output feeds the next. The sequence is predictable before you start. Examples: extract → summarise → format; draft → translate → review.

Use when:
- Steps are always the same regardless of input content
- Each step is independently verifiable (you can check the output of step 2 before feeding it to step 3)
- One pass through the chain is enough

## When NOT to use

- When the number or type of steps depends on what earlier steps return → use Orchestrator-workers
- When you need to retry or refine based on quality evaluation → use Evaluator-optimizer
- When steps are independent and can run simultaneously → use Parallelization

## DiogoOS stage to start at

**Stage 1 (Manual).** Show each intermediate output to Diogo before passing it to the next step. Once the chain runs cleanly 3 times with no corrections, promote to Stage 2.

## Model tier

| Step | Model | Why |
|------|-------|-----|
| Mechanical extraction / formatting | Haiku | No judgment needed |
| Drafting / summarising | Sonnet | Quality matters but not Opus-level |
| Final judgment / write to Notion | Opus | Taste layer; this is what Diogo would do |

## Worked example

**Meeting transcript → meeting note pipeline:**
1. Haiku: extract raw action items and attendees from transcript
2. Sonnet: draft the meeting note in Notion format
3. Opus: review the note, infer owners, flag ambiguous items
4. (Human) Diogo approves before writing to Notion

## Judgment rules

_(Empty — fill in as corrections are made.)_
