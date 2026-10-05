# Five-Agent Protocol

Read this before the first modeling dispatch and revisit it when writing starts. Use five logical roles: lead, modeler A, modeler B, writer A, writer B. Spawn or reactivate only when the stage requires that role. The lead retains ownership of shared contracts and final paper files.

## Role Contracts

| Role | Initial work | After the model decision | During writing |
|---|---|---|---|
| Lead | Parse prompt/rules, research, consult user | Choose route, resolve conflicts, freeze versions | Integrate, route questions, inspect final PDF, run review dialogue |
| Modeler A | Independent complete route | Core equations, computation, parameters, primary results | Answer method/formula/code questions; verify method prose |
| Modeler B | Independent complete route | Independent baseline or second compatible module, sensitivity and validation | Answer result/uncertainty questions; verify conclusions and figures |
| Writer A | May prepare requirement map and outline; no results prose | Wait for approved model contract | Problem analysis, assumptions, data, notation, method and algorithm sections |
| Writer B | May prepare a figure storyboard; no fabricated values | Wait for frozen result packet | Results, interpretation, limitations, recommendations, then Summary Sheet |

Both writers follow the content standard in
[writing-and-visuals.md](writing-and-visuals.md) — explicit task coverage,
claim-first paragraphs, a spent-once qualification budget, symbols that an
equation actually uses, and point-of-use citations — and are dispatched with
the matching brief in [writing-briefs.md](writing-briefs.md). Each writer
reports its task list, number sources, qualifier count, symbols and citations
before handoff; the lead then runs the integration check.

Audit mode adds two audit-only roles to this table: a **rigor auditor** (claim
strength against evidence: precision, uncertainty, units, like-for-like
comparisons, claim-strength words) and a **logic auditor** (inference structure
across section boundaries, contradictions, limitations that do not bound their
conclusion). They are not part of the build flow, but the lead may reactivate
both for the final review round before delivery. See
[audit-and-review.md](audit-and-review.md) and [audit-briefs.md](audit-briefs.md).

Do not dispatch writer A or B to draft substantive paper text until the user has approved the modeling checkpoint. Early outlines and figure plans may be prepared by the lead during preliminary analysis. If there are four concurrency slots including the lead, run at most three workers at once. During writing, keep both modelers' handles/context so they can be reactivated; suspend other workers as needed to answer a technical question promptly.

## Lead-Owned Contracts

- `problem-contract.md`: exact subquestions, outputs, data needs, deliverables, applicable rule URLs and access date, user decisions.
- `model-contract.md`: approved model version, variables and units, assumptions, equations, module interfaces, parameters and sources.
- `evidence-ledger.md`: claim ID to script/data/figure/source and allowed wording.
- `decision-log.md`: route and revision decisions, reason, new version, affected work and owner.
- `ai-use-ledger.md`: visible agent/tool calls and their purpose, outputs used or discarded, verification, manuscript location.

Keep these in the current problem's workspace, not inside the installed skill. Raw data are read-only. Modelers work in separate `work/model-a/` and `work/model-b/` directories; writers edit distinct `paper/sections/*.tex` files. Only the lead edits `paper/main.tex`, shared macros, bibliography, contracts, and final PDF.

## Message Format

Every message starts with `TYPE | TASK-ID | ROLE | STATUS | BASE-VERSIONS`. Supported types:

- `TASK`: objective, required inputs, file ownership, output path, acceptance criteria, due point.
- `HANDOFF`: result/claim IDs, evidence paths, run conditions, limitations, decisions requested, affected manuscript locations.
- `DECISION`: accepted/rejected change, reason, new version, owners to notify and rework.
- `REVIEW`: severity, exact claim/equation/figure/paragraph, evidence and concrete correction.

Use `DONE`, `NEEDS_DECISION`, or `BLOCKED` as the status. Use `P#` for problem contract versions, `M#` for model versions, `R#` for result packets, `C-#` for claims, `S-#` for sources, and `DEC-#` for lead decisions. A writer's technical question is a `REVIEW` addressed to the lead. The lead routes it to the appropriate modeler, obtains a versioned answer, records any decision, and returns that answer to both writers if it changes shared interpretation.

```text
HANDOFF | M2-07 | modeler B | NEEDS_DECISION | P2 M3 R1
Objective: Test how a 20% staff reduction changes room clearance.
Claim C-18: baseline <value>, reduced staff <value>; unit: fraction cleared by <time>.
Evidence: work/model-b/scenarios.R; results/staff.csv; figures/fig-04.pdf.
Conditions: layout <ID>; seed <integer>; parameter source S-04.
Limit: fatigue is not included.
Decision requested: add fatigue to M4 or state this limitation.
Affected text: results section 4.2; conclusion; Summary Sheet.
```

The lead must not paste rival proposals into one paper. Decide on one primary model, then admit another component only after checking state variables, units, assumptions, objectives, and data compatibility. If a frozen `M#` or `R#` changes, notify both writers and revisit every affected claim, figure, conclusion, and summary number.
