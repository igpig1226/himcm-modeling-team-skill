# Modeling And Evidence

Read after the user accepts the preliminary analysis, before dispatching the two modelers. Use the current problem rather than borrowing a high-scoring paper's named algorithms. COMAP's judge commentary values a focused, justified model that the team can explain over a collection of advanced methods.

## Preliminary Research Packet

Before modeling, the lead gives the user a compact packet:

1. A row for every prompt requirement: intended output, evidence needed, expected paper location, unresolved choice.
2. Verified source candidates with URL/title/date, relevance, geographic and time coverage, missing fields, likely bias or uncertainty.
3. Two or three modeling directions at the level of mechanism and tradeoff, not a preselected pile of algorithms.
4. Questions that materially affect scope, target metric, data selection, or decision objective.

Do not dispatch modelers until the user responds to this packet and directs modeling to start. Revise the packet when the user changes scope.

## Independent Proposal Contract

Give both modelers the same `P#` problem contract and research packet. Each returns a short full-problem proposal with:

- Exact output for each prompt task and the decision metric.
- Real-world mechanism, state variables with units, time/spatial scale, equations or algorithm outline.
- Assumptions with justification and the direction in which each might bias results.
- Data and parameter plan, sources and fallbacks, computational effort.
- A simple baseline, verification/validation plan, uncertainty and sensitivity questions.
- A failure case and what the model cannot conclude.

The lead records `DEC-#` after comparing coverage, explanation, usable data, feasibility, and checks. One route becomes primary. Use a modeler's alternative as a baseline or compatible extension only when the mathematics permits. A second independent subproblem may have its own module, but its input/output contract must be written first.

## Result Packet

For each accepted result keep the model version, input data, script command, software version, random seed if relevant, output CSV, figure, claim ID, units, uncertainty, and allowed interpretation. Keep raw data unchanged and document cleaning. Column names encode units where useful, for example `clearance_minutes` and `completion_rate`; a separate field description defines missing values and confidence/uncertainty intervals.

Use R for data handling, statistics, and publication plots when practical; use Octave for matrix, optimization, ODE, or simulation work when appropriate. Do not require both languages merely because they are available. Exchange via documented CSV when both are used. Every figure must be regenerated from script and a frozen result table. No hand-edited plotted values or invented data.

Modeler A implements the core and primary outputs. Modeler B checks dimensions and boundary cases, independently compares to a simple baseline, and tests sensitivity/scenarios that could alter recommendations. Distinguish code verification, data/model validation, and sensitivity; a fit to the same data is not external validation. For stochastic models, report repetitions, seeds, distributions or intervals rather than one run. For optimizers, check feasibility and compare a baseline; call a solution global optimal only with appropriate proof or solver evidence. For weighted scores, explain normalization, weight origin, and rank stability.

## Figure Storyboard

Choose each display for one job. Common options include a model/state diagram, data coverage map, spatial density or route plot, time evolution with uncertainty band, baseline-versus-option comparison, sensitivity tornado/heatmap, observed-versus-predicted check, and Pareto frontier or rank stability. A table is better for exact parameter values or a compact decision comparison. There is no figure count target.

For every candidate figure record `prompt task -> claim ID -> plot form -> input CSV -> script -> axes/units -> colors -> caption point -> manuscript location`. Prefer vector PDF; use high-resolution PNG only when vector output is unsuitable. Use stable color meanings, colorblind-friendly categorical colors, sequential scales for magnitude, and diverging scales only around a meaningful midpoint. Add line types or direct labels so grayscale remains readable. Inspect labels at the figure's final page size. Do not use decoration or a model diagram that merely repeats the table of contents.

## Modeling Checkpoint With The User

The lead presents: selected model and why, alternatives rejected or retained as checks, assumptions and parameter sources, key quantitative outputs, principal visuals, validation/sensitivity findings, and unresolved risk. Ask for targeted feedback and update the model/result packets. Wait for an explicit instruction to begin writing. The user may request another modeling round; keep both modelers engaged until the model is accepted.
