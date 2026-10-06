# Routing

## When to use

The input can belong to one of several distinct categories, each handled differently. A classifier picks the route; a handler executes it. The routes are known in advance.

Use when:
- Inputs are heterogeneous but each type has a clear, consistent handling procedure
- The classification decision is cheap (a short prompt is enough)
- Each route is independent — handlers don't need to coordinate

## When NOT to use

- When the "route" depends on the output of processing, not just the input → use Orchestrator-workers
- When all inputs need the same handling, just with different parameters → just parameterise a single prompt
- When routes aren't mutually exclusive → use Parallelization instead

## Stage to start at

**Stage 1 (Manual).** Log which route was taken on every run. The user checks that the classifier is making the right call. Promote to Stage 2 once routing decisions are consistently correct across 3+ real runs.

## Model tier

| Step | Model | Why |
|------|-------|-----|
| Classification | Haiku | Binary/categorical decision on short input |
| Handler (mechanical) | Haiku | If the route is a formatting or extraction task |
| Handler (judgment) | Sonnet or Opus | If the route involves drafting or quality decisions |

## Worked example

**Inbox triage skill:**
- Haiku classifies each item: meeting transcript / action item / FYI / noise
- "Meeting transcript" → triggers harvest-teams-transcripts + meeting-to-tasks
- "Action item" → writes directly to a task tracker
- "FYI" → archives to an inbox folder
- "Noise" → discards

## Judgment rules

_(Empty — fill in as corrections are made.)_
