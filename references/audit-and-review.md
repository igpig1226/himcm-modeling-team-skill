# Audit And Review

Read this when the user asks to review, audit, check, or 审核/检查 an existing
HiMCM deliverable instead of building a new one. The job is to find content,
model, compliance, rigor and logic problems in a finished paper and report
them. Fixing is a separate, later decision.

An audit is not a rewrite, a proofread, or a second modeling round. If the user
wants fixes after the report, that is a new instruction and follows the
handoff rules at the end of this file.

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
   reply is not an audit result. Follow the dispatch ladder in
   [audit-briefs.md](audit-briefs.md): a first miss is re-dispatched once with a
   tighter brief; a second miss is run inline by the lead and disclosed as
   `inline` in the report. Never merge a stray status update, a question back,
   or a self-directed edit into the audit report.
7. **Lead-verified minimum.** The lead personally re-checks the page limit,
   headers, anonymity, AI disclosure placement, and at least the headline
   numbers before issuing the consolidated report.
8. **Artifact integrity.** Record a hash manifest of the audited sources, the
   result packet, and the built PDF before the audit starts, and re-check it
   before the report is issued. Any file whose hash changed during the audit is
   an integrity finding: name the file, what changed, and which claim it
   affects. An audit performed against a packet that moved under it proves
   nothing.
9. **Name the version under audit.** The report states the exact revision
   audited (paper files, packet, ledgers) and when it was frozen. If the
   artifact is still being edited by someone else, either audit a declared
   snapshot or decline and say why — "the current head" is not a version.
10. **Do not audit against a document that is mid-edit.** If another worker is
    changing the paper or the packet, say so and offer to wait, to audit a
    snapshot, or to run only the version-consistency gate.

## Audit Roles

Seven logical roles. Waves are fine when concurrency is limited; the roles are
logical, not necessarily simultaneous. Copy the matching brief from
[audit-briefs.md](audit-briefs.md) for each dispatch.

| Role | Audit scope | Required output |
|---|---|---|
| Lead | Rules, page/format, anonymity, AI disclosure, version consistency, task-to-section map, consolidation | Compliance ledger plus the single consolidated problem list |
| Modeler A | Equations vs code, units, indices, symbol definitions, objective, constraints, infeasible-case wording | Equation-by-equation divergences with `file:line` |
| Modeler B | Independent recomputation of headline, baseline, frontier, sensitivity and worked-example values; overclaim hunting | Recomputation table plus an overclaim list |
| Rigor auditor | Claim strength vs evidence: precision, uncertainty, units and denominators, like-for-like comparisons, claim-strength words, and whether the audit's own findings are evidence-backed | Findings naming the claim, the strength claimed, the strength supported, and the required rewording |
| Logic auditor | Inference structure across section boundaries: task → model → result → recommendation, circular reasoning, unstated premises, limitations that do not bound their conclusion, cross-section contradictions | Broken or missing inference steps, quoting both ends; contradictions with both locations |
| Writer A | Method, data, notation, assumptions: traceability, definitions, assumption failure effects, citations, task coverage | Traceability and definition defects |
| Writer B | Results, validation, limitations, recommendations, Summary Sheet, letter, poster, figures, tables | Coverage, clarity and accessibility defects |

The rigor and logic roles exist because a paper can be numerically correct and
still overstate what it proves or reason in a circle. Keep their findings
separate from the writers': the writers check whether a section is complete and
traceable, rigor checks whether it is stated at the right strength, and logic
checks whether the chain of inference holds.

## Cross-Review Matrix

Cross-review is mandatory, because each role is blind to its own section. Every
cell must be reported, even when the result is "no findings" — silence is not a
result.

| Reviewer | Must report on |
|---|---|
| Writer A | Results, validation and letter claims: do they follow the method as written? |
| Writer B | Method and data: do they set up the results that are actually reported? |
| Modeler A | Figures, captions, poster and appendix: do they match the code and the frozen packet? |
| Modeler B | Summary Sheet and letter: do their numbers match the packet exactly? |
| Rigor | Every number's precision, conditions and qualifiers; every claim-strength word, wherever it appears |
| Logic | The end-to-end chain task → model → result → recommendation, across section boundaries |

The lead resolves contradictions between reviewers and records which role found
each item.

## Severity And Impact

Every finding carries one severity and one or more impact tags.

- **BLOCKER** — the deliverable is wrong or ineligible: a rules violation that
  disqualifies (page count, anonymity, missing AI disclosure), a number that
  contradicts the frozen packet, or an unsupported claim that changes the
  recommendation.
- **MAJOR** — a required task is unanswered or answered only by assertion; a
  model assumption that changes the conclusion is undisclosed; a stated result
  cannot be reproduced from the packet; a figure or table contradicts its
  caption or the text; a conclusion does not follow from its premises.
- **MINOR** — unclear notation, an unused symbol, a missing citation, wording
  that invites a wrong reading, a table or figure never referenced in prose, or
  a presentation defect that does not change the answer.
- **INFO / NEEDS-INPUT** — a question only the author or user can answer (was
  this a deliberate choice or a slip?), or a suspicion that cannot be graded
  without information the audit does not have. This is not a defect claim and
  must not be silently promoted to MINOR; it goes in its own block and the
  report says what answer would settle it.

Impact tags: `ELIGIBILITY` (affects submission compliance), `CONCLUSION`
(affects what the paper concludes), `CREDIBILITY` (affects how much a reader
should trust it), `PRESENTATION` (affects readability only). A finding may carry
more than one.

## Stages

1. **Freeze the artifact.** Write a hash manifest of the sources, the result
   packet, and the built PDF. State which numbers are frozen and where (result
   packet version, CSV paths). An audit of a document that is still changing is
   not valid, so a frozen packet is a precondition, not a convenience. Re-run
   the manifest at the end and diff it.
2. **Version-consistency gate.** Before dispatching any role, extract every
   number the paper states and compare it three ways: paper vs result packet vs
   contracts and ledgers. Report the mismatch table first, as its own section.
   A single version drift can generate dozens of downstream "findings" that all
   share one root cause, and it will otherwise drown the real ones. Do not
   dispatch until the version under audit is named.
3. **Recall the contract.** Re-read the problem statement and the internal
   contracts (`problem-contract.md`, `model-contract.md`, `evidence-ledger.md`,
   `ai-use-ledger.md`). Build the task-to-section-to-claim map before judging
   coverage; a judge scores the prompt, not the paper's own framing.
4. **Run the seven roles.** Dispatch in waves when concurrency is limited, and
   apply the dispatch ladder. Keep every role read-only and demand the output
   shape below.
5. **Cross-review.** Complete the matrix above, including the empty cells.
6. **Lead compliance audit.** Rules ledger with `source | date | requirement |
   where checked | result`: page count and the counted/uncounted split, first
   sheet, header control number and page number on every page, anonymity in the
   visible text and the PDF metadata, file size and naming, AI disclosure
   placement, inline AI citation, bibliography entry, and whether the AI report
   reproduces the prompts and outputs the current policy expects.
7. **Independently reproduce** every headline number and the extremal
   scenario/period named in the text, plus any value used in the Summary Sheet
   or the letter.
8. **Consolidate.** Deduplicate findings from all roles, keep the strongest
   evidence for each, assign severity and impact tags, and group them as
   model/content, compliance, rigor, logic, and language. Do not fix anything.
9. **Report.** Order by severity, give a count per prompt task, list what was
   checked and found sound, and state plainly what was or was not modified. If
   something was modified anyway, say exactly what and what it affected.

## Re-Audit Mode (After A Fix Pass)

A fix pass does not need the full seven-role run. Re-audit mode covers exactly
what a change can break:

- the lead compliance checklist, if page count, structure, headers, anonymity or
  disclosure were touched;
- modeler B recomputation of every number in a changed claim;
- the writer who owns each changed section;
- the rigor auditor whenever a claim's strength or qualification changed;
- the logic auditor whenever a conclusion, limitation or recommendation moved.

The report states `mode: re-audit` and lists which roles were skipped and why.
Skipped roles are named in the report, never silently omitted.

## Audit To Fix Handoff

An audit ends with findings, not edits. When the user then asks for fixes:

1. The user selects the items, or the lead proposes a subset with the reason.
2. Every selected item gets an owner (which role files the change) and an
   acceptance check (what evidence will show it is resolved).
3. INFO / NEEDS-INPUT items are answered by the user before they become work.
4. After the fix pass, re-freeze the packet and the paper, then run re-audit
   mode over the touched claims plus the lead checklist. Do not declare a fix
   verified because the file changed.
5. Record the fix pass and the re-audit in the AI use ledger, as with any other
   substantive agent work.
6. If a fix changes a frozen number, every downstream artifact — result packet,
   figures, text, Summary Sheet, letter and ledgers — is updated in the same
   pass, and the report says which version each now carries.

## Output Shape

```text
AUDIT | <artifact and version> | <date> | read-only | mode: full|re-audit
ROLES: <role> done | <role> inline | <role> skipped (<reason>)
Coverage: <which of the required tasks are answered, and how>
INTEGRITY: <manifest unchanged, or the files that changed and what it affects>
VERSION CONSISTENCY: <paper vs packet vs ledgers, or "single version confirmed">

FINDINGS
B-1 | BLOCKER | ELIGIBILITY,CONCLUSION | <file:line> | <quoted text> | <evidence> | <minimum change>
M-1 | MAJOR   | CONCLUSION | ...
m-1 | MINOR   | PRESENTATION | ...

NEEDS INPUT
I-1 | <the question> | <what answer settles it> | <who can answer>

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
- A required task answered only in the letter, or only by assertion, with no
  model or result behind it.
- A frozen result packet that was regenerated during the audit (a re-run of the
  model script, an overwritten CSV, or a re-rendered figure), so the paper now
  cites values the packet no longer produces. Treat the mismatch itself as the
  finding and state which version the paper was written against.
- A stronger word than the evidence carries: "optimal" for a solver gap,
  "validated" for an internal recomputation, "robust" for one scenario,
  "measured" for an assumed parameter, "independent" for a sibling agent.
- A limitation that says data are limited without saying which conclusion it
  bounds, or a recommendation that needs a step the paper never takes.
