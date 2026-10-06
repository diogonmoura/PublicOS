# Orchestrator-Workers

## When to use

A central LLM (the orchestrator) dynamically decides which sub-tasks to dispatch and to whom, based on what earlier steps return. The set of sub-tasks isn't known in advance.

Use when:
- The task is complex enough that the right sub-tasks depend on the input
- Sub-tasks are heterogeneous — different workers do different things
- Error recovery requires judgment ("this worker failed, try a different approach")
- The task is the closest thing to "agentic" without being fully open-ended

## When NOT to use

- When the steps are always the same → use Prompt chaining
- When you just need to fan out the same task across many inputs → use Parallelization
- When the task is truly open-ended with an unknown "done" condition → consider a full Autonomous agent

## DiogoOS stage to start at

**Stage 1 (Manual).** Show Diogo the orchestrator's plan before dispatching workers. Show each worker's output before passing it back to the orchestrator. This is the pattern most likely to produce surprising behavior — review everything early.

## Model tier

| Step | Model | Why |
|------|-------|-----|
| Orchestrator (plan + judge) | Opus | Makes judgment calls about what to do next |
| Workers (execute sub-tasks) | Haiku or Sonnet | Mechanical execution; escalate only if the sub-task requires taste |

## Worked example

**Cross-repo coding change:**
- Opus orchestrator receives: "add rate limiting to all API endpoints"
- Orchestrator identifies which files need changes (dynamic — depends on the codebase)
- Dispatches Sonnet workers, one per file, to make the changes
- Orchestrator reviews each diff, flags inconsistencies, requests revisions
- Diogo approves the final set of diffs

## Judgment rules

_(Empty — fill in as corrections are made.)_
