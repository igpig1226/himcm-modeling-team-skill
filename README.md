# HiMCM Modeling Team

A Codex skill for a staged HiMCM paper workflow with one lead agent, two modeling agents, and two writing agents. The lead first obtains the full problem and researches sources, then discusses the approach with the user. Modeling begins after that discussion; writing begins after a second discussion of the completed model. Modelers remain available to answer writers' technical questions. The user reviews and revises the final paper through further dialogue.

Invoke it with `$himcm-modeling-team` and provide a problem statement or PDF, or let it ask for one. The workflow uses the applicable contest's current rules and documents its AI use. R, Octave, and a local LaTeX toolchain are useful when the problem calls for computation, plots, and a PDF paper; the skill does not require both numerical languages for every problem.

The skill files are in `SKILL.md` and `references/`. Install this directory under the Codex skills directory, usually `~/.codex/skills/himcm-modeling-team`.
