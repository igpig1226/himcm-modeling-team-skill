# Audit And Review

Read this when the user asks to review, audit, check, or 审核/检查 an existing
HiMCM deliverable instead of building a new one. The job is to find content,
model, and compliance problems in a finished paper and report them. Fixing is
a separate, later decision.

An audit is not a rewrite, a proofread, or a second modeling round. If the user
wants fixes after the report, that is a new instruction and follows the normal
revision loop.

## Mode Rules

1. **Read-only.** Nobody in audit mode edits anything inside the audited
   project: not the LaTeX sources, not the CSVs, not the figures, not the PDF.
   Do not run scripts that write into the project (`core.py`, `render.py`, a
   build that overwrites the paper). If a build must be checked, copy the
   project to a scratch directory or direct the output elsewhere, and record
   that a scratch build was made.
2. **Evidence for every finding.** Each finding names `file:line` (or a rule
   URL), quotes the exact text/equation/value, gives the evidence (CSV row,
   code line, recomputation, rule clause), and states the smallest change that
   would resolve it. A finding without evidence is an opinion and stays out.
3. **No silent fixes.** If an auditor changes a project file, that item is
   void as an audit result. The lead records it as an edit made during a
   read-only run, re-verifies which version is now on disk, and reports the
   side effect (including any page-count or numbering change) to the user.
4. **Report, do not judge the fix.** List problems; the user decides what to
   change. Do not rewrite prose, rename things, or adjust numbers during the
   audit.
5. **Reproducibility.** A "no defect found" conclusion about a number is only
   reportable after someone reproduces it from the frozen packet with a stated
   command or arithmetic, not because an agent asserted it.
6. **Verify sub-agent compliance.** Before accepting any reply as an audit
   result, confirm it carries the assigned TASK-ID, stays inside the assigned
   scope, uses the required output shape, and respected read-only. An off-brief
   reply is not an audit result: re-dispatch with a tighter brief (or run that
   role inline). Never merge a stray "status update" or a self-directed edit
   into the audit report.
7. **Lead-verified minimum.** The lead personally re-checks the page limit,
   headers, anonymity, AI disclosure placement, and at least the headline
   numbers before issuing the consolidated report.

## Audit Roles

| Role | Audit scope | Required output |
|---|---|---|
| Lead | Rules, page/format, anonymity, AI disclosure, task-to-section map, consolidation | Compliance ledger plus the single consolidated problem list |
| Modeler A | Equations vs code, units, indices, symbol definitions, objective, constraints, infeasible-case wording | Equation-by-equation divergences with `file:line` |
| Modeler B | Independent recomputation of headline, baseline, frontier, sensitivity, and worked-example values; inferential overreach | Recomputation table plus an overclaim list |
| Writer A | Method, data, notation, and assumption prose: traceability, definitions, assumption failure effects, citations, task coverage | Traceability and definition defects |
| Writer B | Results, validation, limitations, recommendations, Summary Sheet, letter, poster, figures, tables | Coverage, clarity, and accessibility defects |

Cross-review is mandatory, because each role is blind to its own section:
writer A reads the results and validation claims against the method; writer B
reads the method against the results; both modelers check figures, captions,
and the poster against the frozen packet. The lead resolves disagreements and
records which role found each item.

## Severity

- **BLOCKER** — the deliverable is wrong or ineligible: a rules violation that
  disqualifies (page count, anonymity, missing AI disclosure), a number that
  contradicts the frozen packet, or an unsupported claim that changes the
  recommendation.
- **MAJOR** — a prompt task is unanswered or answered only by assertion; a
  model assumption that changes the conclusion is undisclosed; a stated result
  cannot be reproduced from the packet; a figure or table contradicts its
  caption or the text.
- **MINOR** — unclear notation, an unused symbol, a missing citation, wording
  that invites a wrong reading, a table or figure never referenced in prose,
  or a presentation defect that does not change the answer.

## Stages

1. **Freeze the artifact.** List the sources and the built PDF with timestamps
   or hashes. State which numbers are frozen and where (result packet version,
   CSV paths). An audit of a document that is still changing is not valid.
2. **Recall the contract.** Re-read the problem statement and the internal
   contracts (`problem-contract.md`, `model-contract.md`, `evidence-ledger.md`,
   `ai-use-ledger.md`). Build the task-to-section-to-claim map before judging
   coverage; a judge scores the prompt, not the paper's own framing.
3. **Run the five roles.** Dispatch in waves when concurrency is limited;
   the roles are logical, not necessarily simultaneous. Keep every role
   read-only and demand the output shape below.
4. **Lead compliance audit.** Rules ledger with `source | date | requirement |
   where checked | result`: page count and the counted/uncounted split, first
   sheet, header control number and page number on every page, anonymity in the
   visible text and the PDF metadata, file size and naming, AI disclosure
   placement, inline AI citation, bibliography entry, and whether the AI report
   reproduces the prompts and outputs the current policy expects.
5. **Independently reproduce** every headline number and the extremal
   scenario/period named in the text, plus any value used in the Summary Sheet
   or the letter.
6. **Consolidate.** Deduplicate findings from all roles, keep the strongest
   evidence for each, assign severity, and group them as model/content,
   compliance, and language. Do not fix anything.
7. **Report.** Order by severity, give a count per prompt task, list what was
   checked and found sound, and state plainly that nothing was modified. If
   something was modified anyway, say exactly what and what it affected.

## Output Shape

```text
AUDIT | <artifact and version> | <date> | read-only
Coverage: <which of the required tasks are answered, and how>

FINDINGS
B-1 | BLOCKER | <file:line> | <quoted text> | <evidence> | <minimum change>
M-1 | MAJOR   | ...
m-1 | MINOR   | ...

CHECKED AND SOUND
<list>

NOT MODIFIED: <confirmation, or the exact list of unintended edits and their effect>
```

## Common Defects This Mode Catches

- A number in the Summary Sheet or letter that drifted from the result packet
  after a revision.
- A comparison that claims to change placement while one resource class is
  forced to the same allocation by its caps.
- A "sensitivity" row presented as a like-for-like loss when it changed the
  objective, the feasible set, or the weighting scale.
- Notation introduced and then never used by any equation.
- An audit described as "independent" when it was performed by the same agent
  family and reviewed by no human.
- An AI disclosure that summarizes interactions where the current policy
  expects the prompts and outputs, or that names a model version nothing in the
  session can confirm.
- Prompt tasks answered only in the letter, or only by assertion, with no
  model or result behind them.
