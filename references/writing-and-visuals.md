# Writing, LaTeX, And Visual Review

Read when the user has accepted the modeling checkpoint and asked to begin
writing. The manuscript is in English; discuss progress and decisions with the
user in the user's language unless asked otherwise. Writers receive the same
approved `M#` and frozen `R#`. Their prose cannot outrun the evidence packet.

Dispatch briefs for each writing role are in [writing-briefs.md](writing-briefs.md).

## Section Responsibilities

| Section | Required argument | Owner |
|---|---|---|
| Problem framing and introduction | Decision context, exact questions, meaningful background, contribution and scope | Writer A |
| Data, assumptions, notation | Source coverage, cleaning, units, justified assumptions and their effects | Writer A |
| Model and computation | Why this abstraction, equations/constraints, parameter estimation, algorithm, outputs and interfaces | Writer A |
| Results and application | Direct answers to prompt tasks, baseline and scenario values, interpretation and decision meaning | Writer B |
| Validation and sensitivity | What was checked, range/uncertainty, threshold at which conclusions change | Writer B with modeler B |
| Limitations and recommendations | Which assumptions affect the decision; qualified and actionable conclusions | Writer B |
| Summary Sheet | Self-contained objective, core method, actual numerical results, check and recommendation | Writer B drafts last; lead finalizes |
| Letter/memo | Only when the prompt requests one; plain language for the named audience | Writer B |

The paper's order follows the prompt and logic, not the agent roles. The lead
maintains a task-to-section-to-claim map. A section with no prompt purpose or
evidence needs a reason to remain. A single primary model may be refined; do not
present disconnected scoring systems as one solution.

## Content Standard

Good content answers the prompt, and every paragraph earns its place. These
rules govern the writing, not the formatting.

### Task coverage is a contract, not an aspiration

1. Split the prompt's required tasks explicitly. Before drafting, the lead
   writes the task-to-section-to-claim map; each writer knows which tasks their
   sections own.
2. Every required task gets an explicit answer in the body: a paragraph that
   states the answer, the number or figure that supports it, and what it means
   for the decision. A task answered only in the letter, only in a table, or
   only by assertion is not answered.
3. Read the task wording literally. If it asks for "strengths **and**
   limitations", both halves get written text — a limitations section alone
   fails the task even when the limitations are excellent. Same for "which
   components remain unchanged **and** which would change", or "what data
   **and** how the metrics would shift".
4. When a task cannot be fully answered with the available evidence, say so in
   one sentence, name what is missing, and answer as far as the evidence
   allows. Do not silently drop the task.

### Every paragraph makes a claim

Open with the claim or the finding, then the number, then the mechanism, then
what it changes for the decision. This is a shape, not a rigid template: a
paragraph that only hedges, only describes a table, or only restates the method
is rewritten or deleted.

Never open a paragraph with a disclaimer. Disclaimers belong where the reader
first meets the assumption (data section, provenance table, limitations), not
at the head of every finding.

### The evidence ladder

definition or assumption → model → result → recommendation. A recommendation
may not skip the result step, and a conclusion may not be stronger than the
result that supports it. Use `simulate`, `estimate`, `predict`, `optimize` and
`validate` accurately. Reserve `optimal`, `significant`, `robust`, `accurate`
and `independent` for claims actually supported by proof, a comparison, a check
or an external reviewer.

Numbers require subject, scenario/time, units, sensible precision, and a
`C-#`/packet source. A dimensionless index is reported with its range and its
meaning; it is never relabeled as a percentage of a real-world outcome.

## Qualification Budget

Repeated disclaimers are the most common way a strong paper reads as
AI-generated, and they also hide the real argument. Spend the qualification
budget deliberately.

1. State the conditional nature of the inputs **once** where the reader first
   meets them (data/provenance) and **once** where the conclusions are bounded
   (limitations). Those two spots carry the full statement.
2. Everywhere else, qualify locally and briefly — "under the assumed scenario",
   "at the 140-person cap" — instead of repeating the full disclaimer. A
   qualifier that adds no new condition is deleted, not rephrased.
3. Before handoff, count the occurrences of the paper's qualifier vocabulary
   (for example `illustrative`, `assumed`, `not a measured`, `is not a claim`)
   and cut the repeats. A qualifier appearing more than a handful of times in
   the whole paper is a defect, not diligence.
4. Do not negate the same thing twice in different places. If the section text
   already says a score is not an outcome rate, the caption does not repeat it.
5. Two "X, not Y" constructions in one paragraph is a rewrite signal. Vary the
   sentence form or fold the negation into a positive statement.
6. The non-technical letter gets **one** sentence bounding what the scores mean,
   and that sentence also says what they *are*.

A short test: delete every qualifier and ask what a reader would now believe
that is false. Keep exactly those qualifiers; delete the rest.

## Definition And Notation Discipline

1. Every symbol must appear in an equation, a constraint, or a table column. A
   symbol that exists only in a definitions list is either used by the model or
   removed from the paper.
2. Define each symbol at first use with its unit; never redefine it later with
   a different meaning. If two concepts need the same letter, rename one.
3. Keep a lead-owned vocabulary list and use the same term everywhere — in
   equations, prose, tables, captions, the Summary Sheet and the letter. Two
   names for one quantity reads as two quantities.
4. A parameter that is described but never enters the model is stated as
   context, with a sentence saying the model does not use it, rather than
   carrying equation-style notation.

## Citation Discipline

1. Cite at the point of use, not only in a provenance table. A reader must be
   able to see where a fact came from without hunting.
2. Any named place, facility, event or external figure introduced in the prose
   carries a citation, or is explicitly labeled a planning label rather than a
   fact about the site.
3. Do not let a source that was read for context appear to be the basis of a
   modeled parameter. If a source is listed but not used, say so in its entry or
   drop it; an uncited bibliography entry invites the question of why it is
   there.
4. Verify the original source, not a search snippet, and never invent a
   reference. If the supplied material has unmapped citation markers, treat them
   as context and say so rather than fabricating a mapping.

## Anti-Template Rules

These are the observed failure modes of machine-assisted drafting. Each is
checked before handoff.

- Do not repeat a caption's disclaimer in the body or vice versa.
- Do not open consecutive paragraphs with the same frame ("This is not…",
  "The model does not…", "It remains conditional…").
- Do not restate a table row by row in prose; interpret what it shows and what
  it changes.
- Do not write "we did not model X" more than the once needed to bound a claim.
- Do not close a paragraph with a disclaimer as a reflex; close with the
  consequence.
- Do not pad a section to fill pages. A short section that answers its task
  beats a long one that repeats it.

## Section Contracts

Each section states what it must contain, what it must not contain, and roughly
what share of the solution pages it should take. The lead sets the page budget
from the current rules before drafting.

| Section | Must contain | Must not contain | Rough share |
|---|---|---|---|
| Framing | Decision context, the exact questions, why the abstraction is the right one, scope | Literature review for its own sake, unverified background | ~5% |
| Data, assumptions, notation | What is observed vs assumed, provenance, unit conventions, assumptions with their failure effect | Numbers without provenance; a definitions dump of unused symbols | ~20% |
| Model and computation | The mechanism, every equation with its conditions, the algorithm, the interfaces a reader would need to reproduce it | A method list; equations the results never use | ~20% |
| Results | Direct answers to the prompt's tasks, baseline and scenario values, mechanism, decision meaning | Table-reading prose; a new model introduced here | ~25% |
| Validation and sensitivity | What was checked, what each check can and cannot establish, the threshold at which the conclusion changes | Calling internal reconstruction "validation"; like-for-like claims across different scales | ~12% |
| Limitations and recommendations | Which assumption would change which conclusion; an actionable sequence | "Data are limited" without a consequence | ~13% |
| Transfer plan | Unchanged structure, parameters to replace, data required, expected directional shift | Invented local numbers or unsourced site claims | ~5% |
| Summary Sheet | Objective, method, real numbers, check, recommendation, standing alone | Forward references, undefined terms, claims absent from the body | 1 page |
| Letter | Recommendation first, plain-language tradeoff, one bounding sentence | Jargon, equations, undefined metric names, bare decimals without meaning | ≤2 pages |

## The Non-Technical Letter

The letter is read by decision-makers, not modelers. It is not a summary of the
paper; it is a recommendation with the reasoning a non-specialist can act on.

1. Recommendation in the first two sentences, with the main tradeoff.
2. No acronyms, no equations, no undefined metric names. If a score must appear,
   it appears with a plain-language gloss in the same sentence: what the number
   measures, what a higher number would mean, and what it does not mean.
3. Give relative comparisons rather than bare decimals where possible — how much
   better one option is than another, computed from the frozen packet.
4. The letter may not assert anything the body does not establish, and may not
   introduce a term the body defines differently.
5. If the prompt allows a graphic page, the graphic carries a plain-language
   caption of its own and follows the same qualification budget.

## Figures And Tables In The Manuscript

Use a diagram for mechanisms/interfaces, a plot for structure or trend, and a
table for exact comparable values. Different forms may appear across the paper,
but color has consistent meaning. Refer to every figure/table in prose; state
the reader's question before it and interpret its key pattern after it.
Captions give metric, scenario, units or source context, and the conclusion,
without becoming another results section or repeating the section's disclaimer.
Do not paste chart screenshots or duplicate the same data as both full table and
full chart without a reason. Titles and axis labels baked into a figure file are
part of the paper's language: keep their wording consistent with the text when a
figure is regenerated.

Writer B may request a revised plot via `REVIEW`, naming the missing comparison
or unreadable feature. A modeler changes the script and regenerates the plot;
the writer must not manually change values. The lead checks plots at final
printed size, grayscale distinction, legible axes and legends, and that all
results agree with the frozen packet.

## LaTeX Ownership And Build

Use a 12 pt `article` baseline unless current official rules require another
format. The lead owns `paper/main.tex`, shared commands and
`paper/references.bib`; writer A and writer B own different files under
`paper/sections/`. Use `\input{sections/method}` and `\input{sections/results}`
from the root, consistent `\label`/`\ref`/`\cite`, and vector-PDF figures via
`\includegraphics`. Keep tables native to LaTeX with readable units. Do not
shrink margins, captions, references, or figure labels to hide overflow. A table
of contents, references, and appendices count toward a HiMCM page limit when
current rules say they do.

For a multi-file project compile locally from `paper/`, for example
`xelatex main.tex`, `bibtex main`, then `xelatex main.tex` twice. Skip BibTeX
when unused; adapt to available tools. Inspect logs for undefined
references/overfull boxes. Render the completed PDF and inspect all pages for
cut-off text, blank/overlapping content, figure legibility, page count, required
first sheet, page headers with the control number and page number, anonymity in
visible text and metadata, and the placement of the AI use report. Check the
current rules before finalizing; if preparing an actual submission, check its
required filename and size too.

## Writing Review Gates

### Writer self-check before handoff

Submit the section with a short note listing:

1. the prompt tasks this section answers, one line each;
2. every number used, with its `C-#` or packet source;
3. the qualifier count in the section, and what was cut;
4. any symbol the section introduces, and where it is used;
5. any citation added, and any external fact still uncited;
6. anything the writer could not establish and wants the lead or a modeler to
   resolve.

### Lead integration check

After both writers deliver: one consistent voice, one vocabulary, no duplicated
disclaimers across sections, no number restated without its conditions, the
task map fully covered, the page budget met, and the Summary Sheet consistent
with the body.

### Final review round

The lead may then run the light review described in the main skill: the rigor
auditor on claim strength, and the logic auditor on whether the recommendations
follow from the results. A substantive numerical revision reopens the affected
prose, Summary Sheet, figures and AI records together.

## Cross-Review And User Loop

Writer A reviews whether the results follow the stated model; writer B reviews
whether the methods explain the results sufficiently. Both modelers then check
technical accuracy, units, numeric conditions, figures, and captions. The lead
edits for one consistent voice and resolves open `REVIEW` items. Present a
reviewable PDF and a short decision summary to the user. Ask what to change in
the model, result, visuals, language, or recommendation. Iterate; a substantive
numerical revision reopens affected prose, Summary Sheet, figures, and AI
records.
