# Worked example — synthetic

A fictional `audit`-mode run showing the expected `structure-this` output shape,
including the low-stakes tier behaviour on Gate 4. Entirely invented — no real
person, company, tool, or project. Synthetic so that no real work content ends up in this repo.

**Reader**: Priya (named colleague). **Artifact**: email → **low stakes**.
**Posture**: neutral.

## Before — a low-stakes email that fails Gates 1, 4 and 5

> Subject: Ticketing migration update
>
> Hi Priya,
>
> Ops has logged tickets in Ticketframe since March. The vendor is retiring its
> on-prem tier in November, and Glidewing has been our approved replacement since
> Q2.
>
> There are three issues with the current approach: a spreadsheet export
> nobody owns, tickets older than 90 days that aren't migrating cleanly, and
> an onboarding guide that assumes admin access most of the team lacks.
>
> Also worth flagging:
> - The support queue backlog is at 340 tickets.
> - Glidewing's mobile app just left beta.
> - Two engineers are out next week for training.
>
> The vendor confirmed Ticketframe exports stop working after October 15. If
> exports stop working, anything not migrated by then is lost. So we should
> move the migration date up to October 1.
>
> Tom

## Diagnosis

Artifact is an email → **low stakes**. Gate 4 flags rather than blocks; every
other failing gate below blocks or flags per its own row in the gates table.

1. **Gate 1 — blocks.** No question is written down anywhere in the draft. The
   reader has to infer one from the closing paragraph ("so we should move the
   migration date up to October 1"), and the draft never states what question
   that answers. Until a question is written — one sentence, ending in a
   question mark, that Priya would recognise as hers — nothing downstream can
   be checked against it. (This also makes **Gate 2** unevaluable: there is no
   written Question to read the Answer back against.)

2. **Gate 3 — blocks.** The three-bullet group —
   *"The support queue backlog is at 340 tickets," "Glidewing's mobile app just left
   beta," "Two engineers are out next week for training"* — has no discernible
   order. It isn't temporal (the three items don't happen in sequence), isn't
   structural (they aren't parts of one named whole — a backlog count, a
   product-readiness fact, and a staffing fact are three different kinds of
   thing), and isn't comparative (nothing ranks them by importance). Per
   `orders-and-mece.md`, a group that fits none of the three orders is wrong
   thinking, not a formatting problem — it needs to be re-derived from
   whatever question it's meant to support, not just reordered.

3. **Gate 5 — flags.** The closing paragraph is a textbook deductive chain at
   the top of the pyramid: *"The vendor confirmed Ticketframe exports stop
   working after October 15* [X is the case] *. If exports stop working,
   anything not migrated by then is lost* [X implies Y] *. So we should move
   the migration date up to October 1"* [therefore Z]. Per
   `deduction-vs-induction.md`, this is exactly the failure mode to avoid at
   the top level — a reader who loses the thread at step two gets nothing from
   step three, and the top of the pyramid is where a reader decides whether to
   keep reading at all.

4. **Gate 4 — flags (low stakes; would block on a high-stakes artifact).**
   *"There are three issues with the current approach:"* fails the synthesis
   test in `synthesis-test.md` — it announces that a category exists (three
   issues) without saying what they add up to. Covering the three items and
   reading the parent line alone, a reader learns only that problems exist,
   not what they mean for the migration. This is a flag, not a block, because
   the artifact is a low-stakes email — proposed rewrite:
   *"The current plan will lose tickets at cutover unless three gaps close
   first: the spreadsheet export needs an owner, the 90-day migration script
   needs a fix, and the team needs admin access before onboarding."*

## After — the same email, restructured

> Subject: Move the Glidewing migration to October 1
>
> Hi Priya,
>
> Ticketframe's exports stop working after October 15, and the plan we're on
> now won't have the team migrated by then. So let's move the cutover from
> November to October 1.
>
> Closing three gaps this week gets us to a clean cutover:
> - Assign an owner to the spreadsheet export so it stops breaking silently.
> - Fix the migration script so tickets older than 90 days move correctly.
> - Get the team admin access before onboarding, since Glidewing's guide assumes
>   they already have it.
>
> None of this is blocked by the support backlog, the mobile app's beta
> status, or next week's training — but the October 15 export deadline is
> real, so I'd like to lock the new date this week.
>
> Tom
