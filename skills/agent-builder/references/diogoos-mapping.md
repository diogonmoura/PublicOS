# DiogoOS Pattern Mapping

Quick reference: which pattern maps to which DiogoOS stage, model tier, and safety defaults.

## Pattern → DiogoOS mapping

| Pattern | Start at stage | Orchestration model | Worker model | Safety default |
|---------|---------------|---------------------|--------------|----------------|
| Prompt chaining | Stage 1 (Manual) | Sonnet (coordinates steps) | Haiku (mechanical steps) | Show each step's output before writing |
| Routing | Stage 1 (Manual) | Haiku (classifies) | Sonnet/Haiku (handles) | Log the route taken; show before acting |
| Parallelization | Stage 1 (Manual) | Sonnet (fans out, merges) | Haiku (parallel workers) | Show merged result before writing |
| Orchestrator-workers | Stage 1 (Manual) | Opus (plans, judges) | Haiku/Sonnet (executes) | Show plan before execution; show each worker output |
| Evaluator-optimizer | Stage 1 (Manual) | Opus (evaluates) | Sonnet (generates) | Show each iteration; cap at N iterations |
| Autonomous agent | Stage 1 (Manual) | Opus (all judgment) | Haiku (tool calls) | Human approves every external write; hard iteration cap |

## Stage definitions (from CONVENTIONS.md)

- **Stage 1 (Manual):** Diogo invokes and reviews every output before it's used.
- **Stage 2 (Trusted):** After ≥3 clean real runs with no corrections. Diogo spot-checks.
- **Stage 3 (Agent):** Runs on schedule/trigger; Diogo approves output, doesn't produce it.

## Safety defaults by stage

- Stage 1: Never write to Notion or any external system without showing Diogo the draft first.
- Stage 2: Write, but log what was written and notify Diogo.
- Stage 3: Write + notify; Diogo approves the run, not each output.

## Harvester rule (always applies)

Skills that race against deletion (e.g. fetching a transcript before it's purged) must persist raw input to `inbox/` first, then process — never lose the source.
