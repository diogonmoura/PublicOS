# When to Use Agents vs. Workflows

## The core distinction (Anthropic article)

**Workflows** — LLMs and tools are orchestrated through predefined code paths. The structure is fixed; the LLM fills in the content at each step.

**Agents** — LLMs dynamically direct their own processes and tool usage. The structure is determined at runtime based on environmental feedback.

## The decision fork

Ask yourself: **do the steps need to be decided at runtime, or can they be known in advance?**

| Signal | Points toward |
|--------|--------------|
| Task decomposes into a fixed sequence of sub-tasks | Workflow |
| Sub-tasks are always the same, regardless of input | Workflow |
| One pass is enough (no retry/refine loop needed) | Workflow |
| Human reviews every output before it's used | Workflow |
| Which sub-tasks to run depends on what earlier steps return | Agent |
| The task requires a feedback loop (check output, decide next step) | Agent |
| Error recovery requires judgment (not just retry) | Agent |
| The task is open-ended and the "done" condition is uncertain | Agent |

## Anthropic's guidance

> "When to use agentic systems: Agents are better for open-ended problems where it's difficult or impossible to predict the required number of steps, and where you can't hard-code a fixed path."

> "Workflows are better for well-defined, predictable tasks where you need consistency and reliability."

## Default rule

**Start with a workflow. Graduate to an agent only when a workflow provably can't handle the task.** Agents are harder to debug, harder to trust, and harder to correct. The extra power is only worth it when the task genuinely requires it.

## Judgment rules

_(Empty — fill in as corrections are made.)_
