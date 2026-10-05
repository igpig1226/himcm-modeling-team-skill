# Writing Briefs

Paste-ready briefs for the writing stage. Fill in `<TASK-ID>`, the section file
paths, the frozen `M#`/`R#`, and the page budget the lead set from the current
rules. Keep each writer on its own section files; only the lead edits
`main.tex`, shared macros and the bibliography.

Every writing brief carries the same content rules, because those rules are what
the paper is scored on:

- answer the assigned prompt tasks explicitly, in the body;
- make a claim first, then the number, then the mechanism, then the decision
  consequence;
- spend the qualification budget once, not in every paragraph;
- never invent a value, an equation or a source; ask the lead instead.

## Common Preamble

```text
TASK | <TASK-ID> | <writer> | START | P# M# R#
Approved model and frozen packet: <paths>. Your prose may not outrun them.
You own <your section files>; the lead owns main.tex, shared macros and the
bibliography. Do not edit files you do not own. If you need a number, equation
or definition that is not in the packet, send REVIEW to the lead — do not
invent, estimate or silently round one.

Content standard (read references/writing-and-visuals.md first):
- Cover your assigned tasks explicitly; a task answered only by assertion, only
  by a table, or only in the letter is not answered.
- Open paragraphs with the claim, not with a disclaimer.
- Spend the qualification budget: full disclaimer where the reader first meets
  the assumptions and in the limitations; a short local qualifier elsewhere.
  Count your qualifier occurrences before handoff and cut the repeats.
- Every symbol must be used by an equation or a table column; define with units
  at first use.
- Cite external facts at the point of use.
- No paragraph that only restates a table or repeats a caption.

Handoff note, at the end of your reply: the tasks you answered; every number and
its source; your qualifier count and what you cut; symbols introduced and where
used; citations added and facts still uncited; unresolved questions.
```

## Writer A — Framing, Data, Notation, Model

```text
Scope: problem framing; data and assumptions; notation; model and computation;
appendices describing implementation.
Must produce: the exact questions; what is observed vs assumed with provenance;
the assumption list where each assumption says why it is needed and what happens
to a conclusion if it fails; the notation table; every equation with its
conditions; the algorithm and interfaces a reader needs to reproduce the result.
Watch for: a symbols list that includes something no equation uses (remove or
use it); a number without provenance; an assumption whose failure effect is only
asserted; an external fact — a named place, facility or event — with no citation
or no "planning label" disclaimer; a section that spends pages on background
that no later decision uses.
Budget: framing ~5%, data/assumptions/notation ~20%, model/computation ~20% of
the solution pages. Keep equations the results never touch out of the paper.
```

## Writer B — Results, Validation, Limitations, Recommendations, Transfer

```text
Scope: results and application; validation and sensitivity; limitations and
recommendations; the cross-continent transfer plan.
Must produce: a direct answer to each assigned task; baseline and scenario
values with their conditions; what each check can and cannot establish; for
every major assumption, which conclusion it would change; an actionable
sequence; the transfer plan's unchanged structure, parameters to replace, data
required and expected directional shift.
Watch for: table-reading prose; a "sensitivity" row presented as a like-for-like
loss when the objective, feasible set or weighting scale changed; calling an
internal recomputation "validation" or "independent"; a limitation that says
data are limited without naming the conclusion it bounds; a transfer plan that
asserts facts about the other sites instead of stating what must be measured.
Budget: results ~25%, validation/sensitivity ~12%, limitations/recommendations
~13%, transfer ~5% of the solution pages.
```

## Summary Sheet

```text
Scope: one page, drafted last, after the body's numbers are frozen.
Must produce, standing alone: the decision context; what the model is and what
"protected" means in it; the concrete headline numbers with their conditions;
the check that was run; the recommendation. A reader who sees only this page
must be able to state the result and the caveat.
Watch for: forward references to the body; an undefined term; a claim that does
not appear in the body; a headline number that no longer matches the packet.
Run modeler A over the method wording and modeler B over the numbers before the
lead finalizes.
```

## Letter To The Sponsor

```text
Scope: the non-technical letter, when the prompt asks for one.
Must produce: the recommendation in the first two sentences; the main tradeoff;
what the reader should do next; one sentence bounding what the scores mean, in
plain language. Any number that appears carries a gloss in the same sentence —
what it measures, what higher means, what it does not mean. Prefer relative
comparisons computed from the frozen packet over bare decimals.
Watch for: acronyms, equations, undefined metric names; a term used differently
from the body; a claim the body never establishes; more than one disclaimer
sentence; a graphic page whose caption needs a modeling background to read.
Length: respect the prompt's limit; when a graphic page is allowed it carries
its own plain-language caption.
```

## Lead Integration

Not a brief to dispatch. After both writers deliver, the lead checks: one voice
and one vocabulary; no disclaimer duplicated across sections; no number
restated without its conditions; the task map fully covered (including the
literal "and" in strengths *and* limitations, unchanged *and* changed); the page
budget met; the Summary Sheet and letter consistent with the body; every
`REVIEW` item resolved by the responsible modeler with a version attached.
Then run the light final review — rigor on claim strength, logic on whether the
recommendations follow — and only then show the draft to the user.
