# Writing, LaTeX, And Visual Review

Read when the user has accepted the modeling checkpoint and asked to begin writing. The manuscript is in English; discuss progress and decisions with the user in the user's language unless asked otherwise. Writers receive the same approved `M#` and frozen `R#`. Their prose cannot outrun the evidence packet.

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

The paper's order follows the prompt and logic, not the agent roles. The lead maintains a task-to-section-to-claim map. A section with no prompt purpose or evidence needs a reason to remain. A single primary model may be refined; do not present disconnected scoring systems as one solution.

## Paragraph And Claim Rules

Each important result paragraph should make a claim, give a traceable number/figure, explain the mechanism, and say what it changes for the prompt's decision. It need not follow a fixed four-sentence template. Numbers require subject, time/scenario, units, sensible precision, and `C-#` backing. Use `simulate`, `estimate`, `predict`, `optimize`, and `validate` accurately. Reserve `optimal`, `significant`, `robust`, and `accurate` for claims actually supported by proof, a comparison, or a check.

Introduce an equation by the real relationship it represents; define each new symbol and unit immediately after; explain important terms and the equation's conditions. Keep pseudocode, equations, and R/Octave implementation consistent. Assumptions explain why they are needed, where they apply, and what happens if they fail. Limitations must describe their effect on conclusions, not just say "data are limited."

Write the Summary Sheet after the body and numerical cross-check. It must stand alone and include concrete outputs, not only "we constructed a model." The lead asks modeler A to verify method wording and modeler B to verify numbers and conditions. If the prompt asks for a nontechnical letter, lead with the recommendation and tradeoff; omit unexplained acronyms and equations. Do not add a letter because another contest's problem used one.

## Language And Sources

Use short, direct English sentences when possible. Keep one point per paragraph; define acronyms on first use; use the same term and unit in equations, figures, captions, tables, summary, and letter. Cut formulaic transitions, empty praise, exaggerated novelty, and background unrelated to a modeling choice. Language polishing must not strengthen a technical claim. Every external fact, parameter, dataset, reused method, and outside figure/table needs an inline citation at its point of use and a real bibliography entry. Verify original sources, not just search snippets or AI-generated references.

## Figures And Tables In The Manuscript

Use a diagram for mechanisms/interfaces, a plot for structure or trend, and a table for exact comparable values. Different forms may appear across the paper, but color has consistent meaning. Refer to every figure/table in prose; state the reader's question before it and interpret its key pattern after it. Captions give metric, scenario, units or source context, and the conclusion, without becoming another results section. Do not paste chart screenshots or duplicate the same data as both full table and full chart without a reason.

Writer B may request a revised plot via `REVIEW`, naming the missing comparison or unreadable feature. A modeler changes the script and regenerates the plot; the writer must not manually change values. The lead checks plots at final printed size, grayscale distinction, legible axes and legends, and that all results agree with the frozen packet.

## LaTeX Ownership And Build

Use a 12 pt `article` baseline unless current official rules require another format. The lead owns `paper/main.tex`, shared commands and `paper/references.bib`; writer A and writer B own different files under `paper/sections/`. Use `\input{sections/method}` and `\input{sections/results}` from the root, consistent `\label`/`\ref`/`\cite`, and vector-PDF figures via `\includegraphics`. Keep tables native to LaTeX with readable units. Do not shrink margins, captions, references, or figure labels to hide overflow. A table of contents, references, and appendices count toward a HiMCM page limit when current rules say they do.

For a multi-file project compile locally from `paper/`, for example `xelatex main.tex`, `bibtex main`, then `xelatex main.tex` twice. Skip BibTeX when unused; adapt to available tools. Inspect logs for undefined references/overfull boxes. Render the completed PDF and inspect all pages for cut-off text, blank/overlapping content, figure legibility, page count, required first sheet, page headers with the control number and page number, anonymity in visible text and metadata, and the placement of the AI use report. Check the current rules before finalizing; if preparing an actual submission, check its required filename and size too.

## Cross-Review And User Loop

Writer A reviews whether the results follow the stated model; writer B reviews whether the methods explain the results sufficiently. Both modelers then check technical accuracy, units, numeric conditions, figures, and captions. The lead edits for one consistent voice and resolves open `REVIEW` items. Present a reviewable PDF and a short decision summary to the user. Ask what to change in the model, result, visuals, language, or recommendation. Iterate; a substantive numerical revision reopens affected prose, Summary Sheet, figures, and AI records.
