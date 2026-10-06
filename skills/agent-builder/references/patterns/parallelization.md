# Parallelization

## When to use

Sub-tasks are independent — they don't depend on each other's output — and can run simultaneously to save time or to produce multiple independent perspectives that are later merged.

Two variants:
- **Sectioning:** divide a large task into independent chunks (e.g. process 10 transcripts simultaneously)
- **Voting:** run the same task multiple times with different prompts/models and aggregate (e.g. 3 independent vulnerability reviews, take the union)

Use when:
- Sub-tasks share no state and produce no side effects on each other
- Latency matters and sub-tasks are slow enough that sequential feels painful
- You want independent perspectives to catch what a single pass would miss

## When NOT to use

- When sub-tasks need to coordinate or share intermediate state → use Orchestrator-workers
- When there's only one sub-task → no parallelization needed
- When the merge step requires significant judgment and you can't afford Opus × N calls

## Stage to start at

**Stage 1 (Manual).** Show the user the merged result before any external write. Especially important for voting variants — confirm that the merge logic (union, majority, etc.) is giving the right answer.

## Model tier

| Step | Model | Why |
|------|-------|-----|
| Worker (each parallel branch) | Haiku | Bulk work; cheap per call |
| Merge / aggregate | Sonnet or Opus | Depends on how much judgment the merge requires |

## Worked example

**Batch transcript processing:**
- 10 meeting transcripts arrived this week
- Haiku processes all 10 in parallel: extract action items from each
- Sonnet merges: deduplicates cross-meeting action items, groups by owner
- Opus reviews the merged list and flags ambiguous items
- The user approves before writing to the external system

## Judgment rules

_(Empty — fill in as corrections are made.)_
