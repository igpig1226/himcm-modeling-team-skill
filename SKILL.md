---
name: himcm-modeling-team
description: Coordinate a five-agent HiMCM paper workflow with two modelers, two writers, and a lead agent. Use when a user wants to work through a HiMCM problem from intake and research to modeling, LaTeX writing, figures, review, and revision, or wants an existing HiMCM paper audited in read-only review mode. Require user dialogue before modeling and again before writing.
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

## Audit And Review Mode

Triggered when the user asks to review, audit, check, or 审核/检查 an existing deliverable rather than build one. This mode runs the same five roles with the writing stage replaced by inspection: the output is a prioritized problem list, not a revised paper. Read [audit-and-review.md](references/audit-and-review.md) before dispatching.

1. **Read-only, always.** No role edits the audited project: sources, CSVs, figures, or PDF. No script that writes into the project. If a build must be checked, build a scratch copy and say so.
2. **Freeze and map first.** Record a hash manifest of the sources, result packet, and built PDF; re-read the prompt and the internal contracts; and build the task-to-section-to-claim map before judging coverage. Re-check the manifest before reporting: a packet that changed mid-audit is itself a finding.
3. **Run all five roles** (waves are fine when concurrency is limited): the lead owns rules, page, anonymity, AI disclosure, and consolidation; modeler A audits the formulation against the code; modeler B independently recomputes the numbers and hunts inferential overreach; writer A audits method/data/notation traceability; writer B audits results, summary, letter, and poster against the packet. Auditors never run the project's own scripts; reproduce a number in a scratch copy instead.
4. **Cross-review is mandatory** — writers check the other side's sections against the model, and modelers check figures, captions, and the poster against the frozen packet.
5. **Verify sub-agent compliance.** Accept a reply as an audit result only if it carries the assigned TASK-ID, stays in scope, uses the required output shape, and stayed read-only. An off-brief reply or a self-directed edit is not an audit result: re-dispatch tighter, or run that role inline. Never fold a stray status update into the report.
6. **Evidence and severity.** Every finding cites `file:line` plus a CSV row, code line, recomputation, or rule clause, and is graded BLOCKER / MAJOR / MINOR. Report only; fixing needs a separate user decision.
7. **Lead verifies the minimum itself:** page count and its counted/uncounted split, headers and anonymity, AI disclosure placement and completeness, and the headline numbers reproduced from the frozen packet. A "no defect found" claim is issued only after that.

Close an audit with the task-by-task coverage count, the findings ordered by severity, what was checked and found sound, and an explicit statement of what was or was not modified. If an unintended edit happened during the audit, name it and its side effects (page count, numbering, rebuild) rather than quietly keeping it.

## Operating Rules

- Keep the paper's argument tied to the prompt. High-scoring exemplars inform judgment; their model names, figure counts, and color schemes are not a recipe.
- Use the current contest's official page and problem text for mandatory rules. Distinguish those rules from this skill's internal quality checks and sample-paper observations.
- Keep raw data immutable, numerical results reproducible, and sources verifiable. Label uncertainty and describe unsupported choices as assumptions.
- Log the actual AI use from the first agent call. A five-agent modeling and writing workflow is substantive AI assistance; never describe it as only language polishing. Follow [rules-and-ai.md](references/rules-and-ai.md).
- Respect the available agent concurrency. Five roles are logical roles, not a requirement for five simultaneous workers. The lead controls shared files and version changes.
