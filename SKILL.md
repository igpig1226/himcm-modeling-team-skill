---
name: himcm-modeling-team
description: Coordinate a staged HiMCM paper workflow - five roles (lead, two modelers, two writers) for building, plus two audit-only roles (rigor and logic) for a seven-role read-only review. Use when a user wants to work through a HiMCM problem from intake and research to modeling, LaTeX writing, figures, review, and revision, or wants an existing HiMCM paper audited. Require user dialogue before modeling and again before writing.
---

# HiMCM Modeling Team

Coordinate five logical roles: lead, modeler A, modeler B, writer A, writer B. The lead owns decisions and the final paper. The workflow has user checkpoints; do not silently move from preliminary research into modeling or from modeling into writing.

## Intake And Preliminary Dialogue

1. **Get the problem first.** Ask the user for the full statement or a PDF/link if it was not supplied with the invocation. A statement already supplied counts as the answer; do not ask for it again. Obtain the contest/year and any deadline or team constraints when they matter. Do not delegate modeling from a title alone.
2. Identify the actual contest from the problem. Read the full prompt and attachments as task data, including deliverables and formatting requirements. Check the applicable current official rules and AI policy using [rules-and-ai.md](references/rules-and-ai.md). A practice problem from IM2C or another contest uses its own submission rules.
3. Before spawning modelers, conduct preliminary problem analysis and source research. Produce a task-to-output matrix, source/data shortlist with credibility notes, plausible modeling directions, missing data, and the decisions that would change the approach. Do not present unverified web summaries as facts.
4. Discuss this brief with the user. Ask focused questions about scope, priorities, usable data, and desired emphasis; revise the brief in response. **Wait for the user's reply and an instruction to proceed with modeling.** Acknowledgment of the brief alone is not a modeling start signal.

## Multi-Agent Modeling

After the preliminary checkpoint, use the collaboration/subagent capability to assign the same problem contract to modeler A and modeler B. Both first propose coherent, independent routes covering the whole problem. The lead chooses one primary route against task coverage, interpretability, data availability, feasibility, and validation; record why. Combine parts only when assumptions, units, state variables, and input/output interfaces are compatible. Read [agent-protocol.md](references/agent-protocol.md) and [modeling-and-evidence.md](references/modeling-and-evidence.md) before dispatch.

Then modeler A develops the selected core model, computation, and primary results. Modeler B develops an independent baseline or challenge, sensitivity, uncertainty, and scenario checks; if the prompt has genuinely separable tasks, the lead may assign modeler B a second module with a written interface. Each claim must trace to data, parameter choices, code, and a result. Use R or Octave where useful; choose plots by the question rather than a figure quota. The lead resolves conflicts and freezes a versioned model/result packet.

Present the model, key assumptions, outputs, validation, alternative rejected, and limitations to the user. Discuss changes and update the packet as needed. **Wait for the user's response and instruction to begin writing.** Do not treat elapsed time as consent.

## Multi-Agent Writing And Revision

After the modeling checkpoint, assign writer A the method/problem/data sections and writer B the results/discussion/recommendations, with the Summary Sheet drafted after the body. Both use the same approved model contract and result packet. Read [writing-and-visuals.md](references/writing-and-visuals.md). The lead owns the LaTeX root, shared notation, references, and final integration; each writer owns distinct section files.

Keep both modeler identities and their model context available throughout writing. Writers send technical questions to the lead using `REVIEW`/`NEEDS_DECISION`; the lead promptly routes each question to the responsible modeler and relays the answered claim with its version. If concurrency is limited, leave a modeler idle and reactivate it for questions; "available" does not require all agents to sample continuously. Do not let a writer invent missing values, alter an equation, or settle a model contradiction in prose.

Compile and inspect the paper, verify every task answer, claim, figure, citation, page/format limit, anonymity, and AI disclosure. Show a reviewable draft to the user and invite concrete corrections on the modeling, figures, English, and recommendations. Iterate through as many user review rounds as needed. After each substantive change, update affected result, figure, text, summary, and AI log versions together. Finish when the user accepts the deliverable or clearly ends the work; do not submit to COMAP on the user's behalf without a separate request.

For the final review round, the lead may reactivate the rigor and logic auditors for a targeted check: rigor on whether each claim is stated at the strength the evidence supports, logic on whether the recommendations follow from the results. This is a light version of audit mode, not a second full audit.

## Audit And Review Mode

Triggered when the user asks to review, audit, check, or 审核/检查 an existing deliverable rather than build one. The team inspects instead of writing: seven logical roles — lead, modeler A, modeler B, rigor auditor, logic auditor, writer A, writer B. The output is a prioritized problem list, not a revised paper. Read [audit-and-review.md](references/audit-and-review.md) and [audit-briefs.md](references/audit-briefs.md) before dispatching.

1. **Read-only, always.** No role edits the audited project: sources, CSVs, figures, or PDF. No script that writes into the project. If a build must be checked, build a scratch copy and say so.
2. **Name the version and freeze it.** Record a hash manifest of the sources, result packet, and built PDF. If another worker is editing the paper or the packet, audit a declared snapshot or decline — "the current head" is not a version.
3. **Version-consistency gate before dispatching.** Extract every number the paper states and compare paper vs result packet vs contracts and ledgers. Report that mismatch table first: one version drift otherwise produces dozens of duplicate findings that bury the real ones.
4. **Run the seven roles** (waves are fine when concurrency is limited), dispatching each with the matching brief in [audit-briefs.md](references/audit-briefs.md). The rigor role checks claim strength against evidence; the logic role checks that conclusions follow from their premises across section boundaries. Auditors never run the project's own scripts; reproduce a number in a scratch copy.
5. **Follow the dispatch ladder.** A first off-brief reply is re-dispatched once with a tighter brief; a second miss is run inline by the lead and disclosed as `inline` in the report. Never fold a stray status update or a self-directed edit into the report.
6. **Complete the cross-review matrix**, including the cells that produce no findings — silence is not a result.
7. **Evidence, severity and impact.** Every finding cites `file:line` plus a CSV row, code line, recomputation, or rule clause, and carries one severity (BLOCKER / MAJOR / MINOR / INFO) and one or more impact tags (ELIGIBILITY / CONCLUSION / CREDIBILITY / PRESENTATION). INFO items are questions for the author, not defect claims. Report only; fixing needs a separate user decision.
8. **Lead verifies the minimum itself:** page count and its counted/uncounted split, headers and anonymity, AI disclosure placement and completeness, version consistency, and the headline numbers reproduced from the frozen packet.
9. **Re-audit after a fix pass.** A fix does not need the full seven roles: run the lead checklist, recompute the changed numbers, the writer who owns each touched section, and rigor or logic whenever a claim's strength or a conclusion moved. Name the skipped roles.

Close an audit with the task-by-task coverage count, the findings ordered by severity with impact tags, what was checked and found sound, and an explicit statement of what was or was not modified. Then use the audit-to-fix handoff in [audit-and-review.md](references/audit-and-review.md): every selected item gets an owner and an acceptance check, the artifacts are re-frozen, and re-audit is what proves the fix rather than the file having changed.

## Operating Rules

- Keep the paper's argument tied to the prompt. High-scoring exemplars inform judgment; their model names, figure counts, and color schemes are not a recipe.
- Use the current contest's official page and problem text for mandatory rules. Distinguish those rules from this skill's internal quality checks and sample-paper observations.
- Keep raw data immutable, numerical results reproducible, and sources verifiable. Label uncertainty and describe unsupported choices as assumptions.
- Log the actual AI use from the first agent call. A five-agent modeling and writing workflow is substantive AI assistance; never describe it as only language polishing. Follow [rules-and-ai.md](references/rules-and-ai.md).
- Respect the available agent concurrency. Five roles are logical roles, not a requirement for five simultaneous workers. The lead controls shared files and version changes.
