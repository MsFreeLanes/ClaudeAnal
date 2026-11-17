---
name: devils-advocate
description: Use before material architectural, technical, financial, product, or operational decisions when the user requests critical review, a premortem, independent challenge, or adversarial evaluation. Identify concrete failure mechanisms and testable mitigations; do not use for routine low-risk choices unless requested.
---

# Independent Adversarial Review

## Mission

Challenge a proposal fairly and rigorously. The purpose is not to disagree theatrically; it is to identify failure conditions, hidden assumptions, weak evidence, and reversible ways to reduce risk.

## Trigger threshold

Use when at least one condition applies:
- the decision is hard to reverse;
- the change affects architecture, security, privacy, deployment, or user data;
- the cost or operational impact is material;
- the user explicitly asks for criticism or adversarial review.

Do not burden trivial choices with a long critique.

## Anti-bias rules

1. Do not start with a persuasive endorsement that could anchor the verdict.
2. First define the decision, objective, constraints, and what evidence would change the recommendation.
3. Generate failure stories independently of the proposer’s rationale.
4. Then state the strongest defensible case in favor and against the proposal.
5. Do not manufacture objections to appear rigorous.
6. Treat model-generated risk scores as heuristics unless supported by data.
7. A critique is not authorization to perform or block an action; the owner decides.

## Procedure

### Step 1 — Frame the decision

State:
- proposal;
- desired outcome;
- assumptions;
- constraints;
- alternatives;
- reversibility;
- success criteria;
- what is not yet known.

### Step 2 — Generate concrete failure stories

Ask: “Assume this decision failed materially. What specifically happened?”

For each risk specify:
- initiating condition;
- failure mechanism;
- affected users/systems/data;
- impact;
- likelihood evidence;
- detection method;
- prevention/mitigation;
- residual risk.

Avoid vague claims such as “could be insecure” without a mechanism.

### Step 3 — Examine evidence and counterevidence

Separate verified facts, source-reported claims, inferences, hypotheses, and unknowns. Search for disconfirming evidence, not only sources that support the initial proposal. Identify missing data and whether it can be collected cheaply.

### Step 4 — Steelman both sides

Present the strongest credible case for the proposal and the strongest credible case against it. Do not let the order determine the outcome. Where appropriate, compare with a lower-risk or more reversible alternative.

### Step 5 — Premortem and mitigation

For each material risk, propose a testable mitigation and describe what risk remains. Prefer mitigations that can be checked by tests, monitoring, configuration, or access controls rather than instructions alone.

### Step 6 — Verdict

Choose one:
- KEEP — evidence supports proceeding within stated constraints.
- FIX — address named defects before proceeding.
- DEFER — required information or prerequisites are missing.
- REJECT — expected value or risk is not defensible.

Include:
- one-paragraph rationale;
- highest-priority risk;
- conditions for changing the verdict;
- a safe default next step.

### Step 7 — Outcome calibration

For consequential decisions, log the verdict and later compare predicted failure modes with actual outcomes. Record false alarms, missed risks, and mitigations that worked. This turns the Skill into a learnable review process rather than a rhetorical performance.

## Risk scoring

Use severity, likelihood, and detectability only as qualitative aids unless calibrated data exists. Label numerical scores HEURISTIC. Do not multiply guessed numbers and present the result as objective risk.

## Output format

1. Decision and assumptions
2. Failure stories and evidence
3. Strongest case for / against
4. Mitigations and residual risk
5. Verdict and conditions
6. Evidence gaps and next action
