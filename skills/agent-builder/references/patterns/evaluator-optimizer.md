# Evaluator-Optimizer

## When to use

One LLM generates a response; a second LLM evaluates it and provides feedback; the generator revises. This loop repeats until the evaluator is satisfied or a cap is hit.

Use when:
- Quality has a clear rubric (the evaluator can judge against explicit criteria)
- A single pass reliably underperforms but iteration reliably improves quality
- The task is creative or analytical enough that "good enough" requires multiple attempts

## When NOT to use

- When you don't have a clear rubric — an evaluator without criteria is just noise
- When the first pass is already good enough — iteration adds cost and latency for no gain
- When the "evaluation" is just a human gut check → keep it Manual and have the user review directly

## Stage to start at

**Stage 1 (Manual).** Show the user each iteration (generator output + evaluator feedback) so they can see whether the loop is actually improving quality. Cap iterations at 3 until the pattern is trusted. Promote to Stage 2 only after confirming the evaluator's rubric is reliable.

## Model tier

| Step | Model | Why |
|------|-------|-----|
| Generator | Sonnet | Produces the draft; Haiku often underperforms here |
| Evaluator | Opus | Makes quality judgments; this is the taste layer |

## Iteration cap

Always set a hard cap (e.g. max 3 iterations). Without a cap, a poorly-specified rubric can loop forever. If the cap is hit without convergence, surface the last iteration to the user rather than silently stopping.

## Worked example

**Meeting note quality loop:**
- Sonnet generates the meeting note from transcript
- Opus evaluates against rubric: are all action items captured? Are owners inferred correctly? Is the summary accurate?
- If rubric not met, Opus provides specific feedback; Sonnet revises
- Loop repeats up to 3 times
- The user reviews and approves the final note before the external write

## Judgment rules

_(Empty — fill in as corrections are made.)_
