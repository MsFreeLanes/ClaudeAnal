---
name: debug-troubleshoot
description: Use when software, scripts, tools, integrations, or runtime behavior fails, produces incorrect output, behaves intermittently, or regresses. Apply a reproducible scientific debugging loop: characterize, reproduce, inspect, minimize, hypothesize, discriminate, fix, and verify.
---

# Debug and Troubleshoot

## Mission

Identify the underlying cause of a failure using reproducible evidence. Do not guess, patch symptoms, or confuse a plausible explanation with a confirmed root cause.

## Evidence discipline

Label each important item:
- VERIFIED — directly observed in logs, tests, source, or current runtime.
- SOURCE-REPORTED — stated by documentation or another source but not reproduced.
- HYPOTHESIS — plausible explanation awaiting a discriminating test.
- HEURISTIC — practical triage rule, not a confirmed fact.
- UNKNOWN — missing evidence.

A fix is not verified merely because the error message disappears once.

## Procedure

### Step 1 — Characterize the incident

Capture:
- exact observed behavior;
- expected behavior;
- exact error text and full traceback/log;
- first known occurrence;
- frequency and reproduction rate;
- reproduction steps and input;
- operating system, runtime, framework, dependency, and tool versions;
- recent code/configuration/environment changes;
- impact and affected scope.

Do not start by proposing a fix.

### Step 2 — Reproduce safely

1. Confirm the target repository, branch, and working-tree status.
2. Preserve user changes and data.
3. Run the exact reproduction command or scenario.
4. Record the baseline result and environment snapshot.
5. If the failure is intermittent, repeat enough times to characterize its rate and capture timestamps/state.

If not reproducible, say so. Add instrumentation or request the missing evidence; do not fabricate a root cause.

### Step 3 — Inspect the failure boundary

Read the traceback from the point of failure through relevant caller frames. Inspect:
- affected source and callers;
- state transitions;
- input validation and serialization;
- file/network/process boundaries;
- dependency versions and configuration;
- resource conditions (memory, GPU, ports, permissions);
- recent diffs.

Distinguish the frame where an error surfaces from the mechanism that caused it.

### Step 4 — Minimize when appropriate

Reduce the failing input, call sequence, file set, or configuration while preserving the failure. Use delta-debugging principles carefully.

Do not force minimization when it destroys timing, concurrency, GPU contention, device state, or other context needed to reproduce the problem. If failure disappears after reduction, treat that as evidence of a context-dependent defect, not proof of a fix.

### Step 5 — Generate competing hypotheses

For each hypothesis record:
- mechanism;
- supporting evidence;
- contradicting evidence;
- predicted observation if true;
- cheapest discriminating test;
- result that would falsify it.

Prefer two or three strong hypotheses over a long speculative list. Rank by impact and evidence, not intuition alone.

### Step 6 — Run discriminating experiments

Change one variable at a time. A useful test should eliminate, confirm, or refine at least one hypothesis. Record:
- hypothesis tested;
- predicted result;
- actual result;
- evidence captured;
- hypotheses eliminated, retained, or refined.

An attempt that only changes code without recording a prediction and observation pair provides little diagnostic information.

### Step 7 — Confirm and fix the root cause

A root cause is sufficiently supported when:
1. it explains the observed failure;
2. a discriminating test distinguishes it from plausible alternatives;
3. a minimal correction removes the failure;
4. relevant regression tests do not reveal unacceptable side effects.

Make the smallest justified change. Avoid drive-by refactors and multiple unrelated fixes.

### Step 8 — Add regression protection

Add a test that fails on the original defect and passes after the fix. Where appropriate, supplement with property-based, metamorphic, integration, and end-to-end tests so the implementer is not the only person defining the oracle.

Run the original reproduction and the affected test suite again. Inspect the actual output.

### Step 9 — Record the incident

Append a structured incident/decision record:
- timestamp and identifier;
- observed and expected behavior;
- reproduction and baseline;
- environment;
- recent changes;
- hypotheses;
- experiments and outcomes;
- confirmed root cause or unresolved status;
- correction and files changed;
- regression coverage;
- remaining risks and rollback.

## Stop rule

Stop after two consecutive attempts that produce no new evidence and eliminate no hypothesis. Report the attempts and request the single most useful missing artifact or decision. The number two is a working heuristic; an evaluation suite should compare thresholds of one, two, and three.

## Failure classifications

Useful triage categories include:
- deterministic logic defect;
- invalid or unexpected input;
- configuration/environment mismatch;
- dependency/API incompatibility;
- race condition or nondeterminism;
- resource exhaustion;
- permission/security boundary;
- persistence or synchronization defect;
- incorrect test oracle;
- unavailable external service.

These are categories for investigation, not diagnoses by themselves.
