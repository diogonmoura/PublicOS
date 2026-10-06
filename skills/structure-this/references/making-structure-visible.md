# Making structure visible

## The rule

The pyramid must be visible on the page without being explained. That means
using, deliberately:

- Heading hierarchy — levels that mirror the levels of the pyramid.
- Indentation — sub-points visually subordinate to the points they support.
- Numbering — explicit sequence where the order is temporal or comparative.
- White space — separation between groups that are logically distinct.
- Explicit transitions between sections — a sentence that says how the next
  section relates to the one before it, not a blank line and a new heading.

Headings assert conclusions. They do not name topics. A heading is a pyramid
node in miniature — it has to say something, the same way any other node does
(see `synthesis-test.md`).

## How to test it

The headline-stack test: read only the headings of the document, top to
bottom, nothing else.

1. Do they form the complete argument on their own — could a reader who saw
   nothing but the headings reconstruct the governing thought and the
   reasoning under it?
2. If they read as a table of contents ("Background," "Analysis," "Next
   steps"), they are naming topics, not asserting conclusions. Any heading
   that fails this needs to be rewritten as a sentence.

## Failure modes

- **Headings that name topics.** "Findings," "Considerations," "Overview" —
  the same failure as an un-synthesised node (see `synthesis-test.md`).
- **Structure that exists only in the writer's head.** The grouping is sound
  but nothing on the page — no numbering, no indentation, no heading level —
  tells the reader where one group ends and the next begins.
- **Transitions left implicit.** A new section opens with no sentence
  connecting it to what came before, so the reader has to infer the
  relationship themselves.

### A note on decks

> This edition contains no chapter on on-screen presentations. What follows
> is chapter 6 applied to decks, not Minto quoted. The presentation material
> exists only in the North American lineage of the book.

With that caveat stated, the same rule extends to decks: one assertion per
headline; the headlines alone are the argument, readable start to finish with
the body hidden; the body of each slide is evidence for that slide's own
headline and nothing else — it does not smuggle in a second point.

### A note on email and Teams

The same rule compresses further here: the answer goes in the first line,
the SCQA introduction compresses to two sentences, and the supports render
as a short list, not paragraphs. The reader is scanning a message, not a
document — compression is what makes the structure visible at that length.
