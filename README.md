# ClaudeAnal — Claude Analysis & Engineering Research

A research and engineering knowledge base for advanced Claude prompting, reusable Agent Skills, software engineering, systematic troubleshooting, game and XR development, connectors, and model evaluation.

## Contents

### Start here
- [Master Claude index](CLAUDE_MASTER_INDEX.md) — unified research synthesis and phase-by-phase operating framework.
- [Master operational prompt](prompts/MASTER_OPERATIONAL_PROMPT.md) — reusable controller prompt for complex work.

### Skills
- [python-ai-builder](skills/python-ai-builder/SKILL.md) — read-first, plan-first, minimal and test-backed software changes.
- [debug-troubleshoot](skills/debug-troubleshoot/SKILL.md) — scientific debugging and root-cause confirmation.
- [devils-advocate](skills/devils-advocate/SKILL.md) — independent adversarial review for material decisions.

### Engineering and evaluation
- [Software engineering playbook](docs/SOFTWARE_ENGINEERING_PLAYBOOK.md) — repository discovery, architecture, implementation, tests, security, game and XR workflows.
- [Skill and model evaluation specification](evals/SKILL_AND_MODEL_EVALUATION_SPEC.md) — baseline comparisons, metrics, test suites, stop-rule experiment, and training-data preparation.

### Research
- [Reddit research appendix](research/REDDIT_RESEARCH.md) — curated posts from the requested communities, with exact subreddit provenance and access limitations identified.
- [Prompt and Skill library review](research/PROMPT_LIBRARY_REVIEW.md) — official Anthropic collections, curated prompt libraries, and evaluation tools.
- [Three-Skill critical review](docs/THREE_SKILL_CRITICAL_REVIEW.md) — strengths, flaws, and experiments required before the supplied portfolio can be considered validated.
- [Benchmark palette reference](docs/BENCHMARK_PALETTE_REFERENCE.md) — user-supplied V6.5 palette; LOCKED values are separated from PROPOSED values and unresolved freeze decisions.

## Operating principles

1. Identify the actual repository and environment before changing anything.
2. Distinguish verified facts, source-reported facts, inferences, hypotheses, proposals, heuristics, and unknowns.
3. Research primary documentation and use prompt libraries and Reddit as discovery sources, not proof.
4. Require approval for destructive, externally visible, or high-impact actions.
5. Diagnose failures with reproducible evidence and falsifiable hypotheses.
6. Verify changes with tests and report only observed results.
7. Do not confuse inference-time Skills with model-weight training.

## Repository status

Initialized on the main branch. The research index, three draft Skills, master operational prompt, software playbook, evaluation specification, Reddit research appendix, and palette companion draft are included in this repository.

## Evidence boundary

The index incorporates the supplied “Prompting is dead” image, connector infographic, r/ClaudeUniversity paper screenshot, and the supplied 560-line HTML three-Skill portfolio. The portfolio describes a design artifact, not empirical results; its author explicitly states that no experimental runs were performed. The “QFN on Strata” model label remains unverified.

The requested r/ClaudeUniversity and r/AR_VR_XR Top → All Time pages were not reliably retrievable through the available search index. Their sections therefore identify the user-supplied screenshot or adjacent-community supplements rather than attributing those resources to inaccessible subreddits. Reddit posts are practitioner reports, not peer-reviewed validation.

## Primary documentation

- [Claude Platform documentation](https://platform.claude.com/docs/en/home)
- [Anthropic Agent Skills overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- [Anthropic Skill authoring best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)
- [Promptfoo evaluation documentation](https://www.promptfoo.dev/docs/intro/)
- [Langfuse prompt management](https://langfuse.com/docs/prompt-management/overview)
- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
