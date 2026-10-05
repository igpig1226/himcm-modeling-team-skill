# Audit Briefs

Paste-ready dispatch briefs for audit mode. Fill in `<TASK-ID>`, `<project>`,
`<version>` and the artifact paths. Keep each brief short: a long brief is more
likely to be answered off-scope than a short one.

## Dispatch Ladder

1. Dispatch one role per message, using that role's brief below.
2. Verify the reply before accepting it: first line must be
   `REVIEW | <TASK-ID> | <role> | DONE | <versions>`; the scope must match the
   brief; it must not have edited anything; each finding must carry `file:line`
   plus evidence. An off-brief status report, a question back, or a
   self-directed edit is **not** an audit result.
3. First miss: re-dispatch once with the brief cut to the single most important
   check and the line "Reply only in the required shape. Do not explore
   anything else."
4. Second miss: the lead runs that role inline and records `inline` for it in
   the report's `ROLES:` line. Never fold an off-brief reply into the report as
   if the role had performed the audit.

## Common Preamble

```text
AUDIT | <TASK-ID> | <role> | START | <version>
Read-only. Do not edit, create, or overwrite any file in <project>. Do not run
the project's scripts; if a number must be reproduced, copy what you need to a
scratch directory and compute there. Report findings only — fixing is a later,
separate decision.

Reply in exactly this shape, first line verbatim:
REVIEW | <TASK-ID> | <role> | DONE | <version>
then numbered findings: severity (BLOCKER/MAJOR/MINOR/INFO) + impact tag
(ELIGIBILITY/CONCLUSION/CREDIBILITY/PRESENTATION), file:line, quoted text,
why it is a problem, evidence, minimum change. Most severe first. Then a short
list of what you checked and found sound. If you cannot complete the task, reply
BLOCKED with the reason instead of substituting a different task.
```

## Modeler A — Formulation

```text
Scope: the equations, constraints and algorithm prose vs the model code.
Check: every equation and constraint against the code (variables, units,
indices, objective stages, linearizations, feasibility bounds); symbols defined
before use; notation that is defined but never used by any equation; any
sentence that states what the model proves more strongly than the formulation
supports.
Deliver: one finding per divergence, each with the code line that contradicts
the prose.
```

## Modeler B — Recomputation

```text
Scope: every number the paper states, against the frozen result packet.
Check: recompute headline, baseline, frontier, sensitivity and worked-example
values from the CSVs; confirm the comparison budgets are genuinely equal
(roster, assets, per-period totals); confirm infeasible/optimal labels match the
solver evidence; find claims that read as causal, predictive or measured when
the output is an index under assumed inputs.
Deliver: a recomputation table (paper value, packet value, match?) plus an
overclaim list. Report numbers you could not reproduce.
```

## Rigor Auditor — Claim Strength And Evidence Standard

```text
Scope: how strongly each claim is stated, not whether the arithmetic is right.
Check: every claim-strength word (optimal, robust, validated, significant,
accurate, feasible, independent, measured) against what the evidence can carry;
precision and significant figures versus the underlying uncertainty; units and
denominators stated with each number; comparisons that are not like-for-like
(different objective, feasible set, weighting scale or scenario set) presented
as losses or gains; uncertainty ranges where a point estimate is given; any
number quoted without its conditions; and whether this audit's own findings are
evidence-backed rather than opinion.
Deliver: findings that name the claim, the strength claimed, the strength the
evidence supports, and the exact rewording or qualification needed.
```

## Logic Auditor — Inference Structure

```text
Scope: whether conclusions follow from their premises, across section
boundaries.
Check: the task -> model -> result -> recommendation chain for each required
task; circular or self-justifying argument; unstated premises; a limitation that
does not actually bound the conclusion it is attached to; internal
contradictions between sections (a number, unit, scenario name or definition
that changed between method and results); a recommendation that needs a step
the paper never makes; the letter or summary asserting something the body never
establishes.
Deliver: findings as broken or missing inference steps, quoting both ends of
the chain, plus contradictions with both locations.
```

## Writer A — Method, Data, Notation

```text
Scope: framing, data, assumptions, notation, model and computation sections,
plus the appendices.
Check: task coverage in these sections; every non-prompt number traced to a
labelled assumption or a packet column; definitions and units before use;
indices used consistently; every assumption says why it is needed and what
happens to the conclusion if it fails; citations exist at the point of use and
the cited source can actually support the claim; tables/figures referenced in
prose; judge-visible gaps such as an unstated limitation or an ambiguity that
changes the answer.
Deliver: traceability and definition defects with the missing evidence named.
```

## Writer B — Results And Deliverables

```text
Scope: results, validation, limitations, recommendations, Summary Sheet,
letter, poster, figures and tables.
Check: does each required task get a direct answer; do the results follow the
method as written; is every table/figure referenced and interpreted; does each
caption match its content and units; is the non-technical letter actually
non-technical and does its recommendation follow from the results; does the
Summary Sheet stand alone with concrete numbers; are transfer/adaptation claims
about other sites stated as plans rather than sourced facts.
Deliver: coverage and clarity findings, each naming the reader who would be
misled.
```

## Lead — Compliance And Consolidation

Not dispatched. The lead runs this checklist directly:
page count and the counted/uncounted split; first sheet; header control number
and page number on every page; anonymity in text and PDF metadata; file size
and naming; AI disclosure placement, inline AI citation, bibliography entry and
whether the AI report reproduces what the current policy expects; version
consistency between paper, packet and ledgers; then independent reproduction of
the headline numbers; then dedupe, severity and impact tags, and the report.
