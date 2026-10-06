---
name: structure-this
description: Use when Diogo has something to write — an email, a Teams message, a deck, or a Confluence page — or a draft that isn't landing, and wants it structured answer-first.
---

# Structure This

Applies Barbara Minto's Pyramid Principle (Financial Times / Prentice Hall edition,
10 chapters in 2 parts) to what Diogo actually writes.

The value of this skill is not "put the answer first" — Diogo already knows that. The
value is chapters 7–9, which are the hard ones. So this skill is built as **gates that
block**, not as a formatting pass.

## Status

Stage 1 (Manual) — 0/3 clean runs. Show Diogo every output; never write to an external
system.

## Before you start

Read all eight reference cards. Do not proceed until you have read every one:

1. `skills/structure-this/references/three-rules.md`
2. `skills/structure-this/references/orders-and-mece.md`
3. `skills/structure-this/references/synthesis-test.md`
4. `skills/structure-this/references/deduction-vs-induction.md`
5. `skills/structure-this/references/scqa.md`
6. `skills/structure-this/references/problem-definition.md`
7. `skills/structure-this/references/making-structure-visible.md`
8. `skills/structure-this/references/limits.md`

## Model tiers

| Step | Model | Why |
|------|-------|-----|
| Extract from a pasted draft — enumerate headings, enumerate claims, strip prose | `haiku` | Purely mechanical; keeps a long document out of Opus context |
| Interview, all five gates, synthesis, rewrite | `opus` | The taste layer; CONVENTIONS reserves the final write for Opus |

Skip the Haiku pass on inputs under roughly 500 words — dispatching a subagent to
enumerate the claims in a six-line email costs more than it saves.

## Safety defaults

- Never send, post, or write to Confluence, Notion, or Outlook. Output goes to chat and
  `work/pyramids/` only.
- Fail loudly. If audit mode cannot infer the question from a draft, say so — do not
  invent a question that makes the draft look coherent.
- Never write prose before the pyramid is approved.

## Inputs

One of: a draft to fix, raw material plus a known answer, or a problem with no answer yet.

## Procedure

### 1. Pick the mode

Ask which mode. Propose one if it is obvious — a pasted draft suggests `audit` — but
confirm before proceeding.

| Mode | Diogo has | He leaves with |
|------|-----------|----------------|
| `audit` | A draft | Diagnosis → the correct pyramid → rewrite |
| `author` | Raw material, and he knows his answer | Pyramid → finished prose |
| `structure` | A problem, and no answer yet | A well-formed question → pyramid. No prose. |

### 2. Interview — one question per message, never batched

**Stage 0 — Framing (all modes)**

1. Who is the reader? Must be a named person or a genuinely homogeneous group. If the
   answer is "the team" or "stakeholders", reject it and ask again — an unnamed reader
   has no single question, and without one question there is no pyramid.
2. What artifact? Sets the stakes tier: email or Teams → **low**; deck, Confluence page,
   or decision doc → **high**.
3. What is the reader's posture — receptive, neutral, or resistant?

**Stage A — Problem definition (`structure` mode only)**

Read `problem-definition.md` and walk the five steps, one question per message:
starting point and context, disturbing event, current undesired result, desired result.
Then draft the question from those four and have Diogo confirm it.

**Stage B — SCQA (`author` and `structure`)**

Read `scqa.md`. Establish Situation, Complication, Question — one at a time. In
`author` mode, also establish the Answer now: Diogo knows it.

In `structure` mode, do not ask for the Answer — he has none yet. It is derived later,
as the governing thought the pyramid produces in step 3, then checked by Gate 2.

In `audit` mode, do not ask: **infer** all four (Situation, Complication, Question,
Answer) from the draft and show your reading for correction. If you cannot infer the
Question, that is the top finding of the audit, not a failure of this skill.

### 3. Build the pyramid, then run the gates

Three gates block. Two flag.

| # | Gate | Card | Behaviour |
|---|------|------|-----------|
| 1 | The question is written down — one sentence, ends in a question mark, and the reader would recognise it as theirs | `scqa.md` | **Blocks** |
| 2 | The governing thought answers *that* question. Read them back to back; if the answer answers a different question, one of the two is wrong | `scqa.md` | **Blocks** |
| 3 | Every grouping declares its order — temporal, structural, or comparative. If none fits, the grouping is wrong and the thinking must change, not the formatting | `orders-and-mece.md` | **Blocks** |
| 4 | The synthesis test — every node says something | `synthesis-test.md` | **Blocks** on high stakes; **flags** on low |
| 5 | Induction on top, deduction below | `deduction-vs-induction.md` | **Flags** |

When a gate blocks, say which gate and why, and work the problem with Diogo. Do not
route around it.

On Gate 2 in `structure` mode: there is no Answer at Stage B to test, so Gate 2 is
deferred, not skipped. Once the pyramid yields a governing thought, run Gate 2 against
it exactly as in the other modes — read the Question and the derived Answer back to
back, and if the answer answers a different question, one of the two is wrong.

On Gate 3: MECE is asserted and checked, not belaboured. Do not run a full MECE proof
on a three-bullet email.

Record every gate result in the state file's gate log.

### 4. Choose the introduction order

Posture changes the opening only. The pyramid is identical either way.

- **Receptive or neutral** → S-C-Q-A. Answer up front.
- **Resistant** → lead with the Complication, hold the Answer until after the argument
  line. Say which version you produced and why. See `limits.md`.

### 5. Produce the output

Write in the language of the input. Render into the artifact's native form — see
`making-structure-visible.md` for headings, decks, and email/Teams compression.

- **`audit`** → three sections in order: **Diagnosis** (findings named against specific
  gates, most severe first), **the pyramid the draft should have**, **the rewrite**.
  The diagnosis must answer all four of these:
  - What question does this document answer? Is it written anywhere, or only implied?
  - Does each heading assert a conclusion, or only name a topic?
  - What order is each grouping in — temporal, structural, or comparative?
  - Strip out every number and chart. Does the argument still stand?
- **`author`** → show the pyramid and get approval **first**, then write the prose.
- **`structure`** → question and pyramid, then stop. Decline to write prose; offer to
  hand the pyramid to `author` mode.

### 6. Write the state file

Write `work/pyramids/YYYY-MM-DD-<slug>.md` using
`references/state-file-template.md`. `work/` is gitignored.

## Judgment rules

_(Empty — fill in as Diogo makes corrections. A correction that recurs is a rule that
belongs here.)_
