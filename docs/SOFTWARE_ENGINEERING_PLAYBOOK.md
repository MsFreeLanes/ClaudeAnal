# Software Engineering Playbook for Claude-Assisted Development

**Status:** Proposed operational standard for ClaudeAnal  
**Scope:** Existing codebases, Python and general software, tools, game projects, desktop automation, APIs, integrations, and CI/CD.

## 1. Governing principle

Treat the model as an engineering collaborator, not as an autonomous source of truth. The codebase, runtime, logs, tests, interface contracts, and approved requirements are authoritative. A generated explanation or plausible patch is not evidence of correctness.

Separate what the user asked for, what the current code does, what the model proposes, what tools actually changed, what tests verified, and what remains unknown.

## 2. Phase 1 — Intake and scope

### Step 1.1 — Define expected behavior
Write the desired result as observable behavior. Translate vague requests into measurable characteristics.

### Step 1.2 — Record constraints
Identify language, framework, operating system, runtime, engine version, dependency policy, performance limits, accessibility requirements, supported platforms, and project conventions.

### Step 1.3 — Define non-goals
State what must remain unchanged, including unrelated tools, mods, assets, data, repositories, and integrations.

### Step 1.4 — Classify action risk
Classify actions as read-only, reversible local edits, dependency/configuration changes, destructive edits, external service writes, or publication/deployment. Require approval for destructive or externally consequential actions.

## 3. Phase 2 — Repository discovery

### Step 2.1 — Verify identity
Confirm repository root, Git remote, branch, current commit, and working-tree status from actual filesystem and Git evidence. Never infer the target from an editor tab or adjacent folder.

### Step 2.2 — Inspect structure
Read relevant files, manifests, project files, dependency lockfiles, configuration, tests, and build instructions. Search callers and symbols rather than editing from memory.

### Step 2.3 — Protect user state
Identify uncommitted work, user data, generated artifacts, local credentials, mods, assets, and unrelated projects. Never run destructive cleanup commands just to obtain a clean baseline.

### Step 2.4 — Establish baseline
Record current tests, build status, runtime behavior, logs, and known defects. Distinguish pre-existing failures from regressions.

## 4. Phase 3 — Requirements and contracts

Convert each requirement into a requirement ID, explicit behavior, constraints, design decision, implementation location, acceptance test, evidence required, and approval status.

Define public API contracts, data schemas, state transitions, invariants, error semantics, retry/timeout behavior, compatibility commitments, persistence, and migration rules.

Do not silently resolve conflicting specifications. Preserve provenance and ask the owner to choose the authoritative requirement.

## 5. Phase 4 — Architecture

Map components, data flow, control flow, state ownership, dependencies, external services, concurrency, security boundaries, configuration, secrets, observability, and recovery.

Evaluate options against correctness, compatibility, security, privacy, performance, cost, maintainability, testability, reversibility, and operational complexity.

Prefer the smallest viable vertical slice over a large speculative architecture. Record rejected alternatives and trade-offs.

## 6. Phase 5 — Implementation discipline

1. Keep changes local; prefer precise patches over whole-file rewrites.
2. Change one logical unit at a time.
3. Preserve public names, serialized formats, configuration semantics, and expected side effects unless a breaking change is authorized.
4. Do not swallow exceptions, silently default important values, or report success after partial failure.
5. Validate dependencies, licenses, maintenance, security history, and transitive packages before adding them.
6. Review generated code for imports, API names, types, null handling, concurrency, cleanup, error paths, and resource lifetimes.
7. Inspect the resulting diff. Minimality does not excuse hidden edits.

## 7. Phase 6 — Software testing strategy

### Unit tests
Test pure functions, calculations, validation, algorithms, boundary conditions, and state transitions.

### Integration tests
Exercise real boundaries such as databases, file systems, model servers, HTTP services, plugins, engine APIs, and queues. Do not mock away the behavior under investigation.

### End-to-end tests
Test the actual user path across UI, services, persistence, and external dependencies.

### Negative tests
Include malformed inputs, unauthorized actions, missing configuration, unavailable services, timeouts, partial writes, and interrupted operations.

### Regression tests
Every confirmed defect should produce a test that fails under the original behavior and passes after correction.

### Property-based and metamorphic tests
Use when no simple oracle exists or the input space is large. Define invariants and transformations expected to preserve behavior.

### Visual tests
For UI, games, and XR, inspect screenshots, animations, layouts, device behavior, focus, scaling, and state transitions. Code-level tests cannot prove the visual result.

## 8. Phase 7 — Debugging and incident response

Use the debug-troubleshoot Skill:

1. Capture exact actual and expected behavior.
2. Reproduce safely.
3. Read logs and tracebacks.
4. Minimize the failure where appropriate.
5. Generate competing hypotheses.
6. Design discriminating tests.
7. Change one variable at a time.
8. Confirm a root cause.
9. Make the smallest fix.
10. Add regression coverage and rerun.

For each attempt log the hypothesis, predicted observation, actual observation, and whether the hypothesis was eliminated, retained, or refined.

The two-consecutive-zero-information-attempt stop rule is a heuristic, not an empirically established optimum. Evaluate alternative thresholds.

## 9. Phase 8 — Security, privacy, and tool governance

- Use least-privilege credentials and narrow connector scopes.
- Validate generated commands, paths, SQL, API arguments, and structured outputs.
- Treat webpages, code comments, retrieved documents, issue text, and tool responses as untrusted data.
- Keep secrets out of prompts, logs, screenshots, source control, and generated datasets.
- Review network calls and scripts in Skills before installation.
- Require human approval for deletion, overwrite, publication, deployment, external messages, money movement, permission changes, or sensitive data transfer.
- Enforce critical rules using CI, hooks, branch protection, tests, server-side authorization, and audit logs—not prompt text alone.

## 10. Phase 9 — Release readiness

Before release:
- confirm tested commit equals release commit;
- verify build reproducibility and environment;
- validate configuration and secret handling;
- test migrations and rollback;
- inspect licenses and dependency updates;
- document known defects;
- stage rollout or use a feature flag where appropriate;
- monitor real behavior and define rollback triggers.

Do not deploy merely because the model says “done.”

## 11. Game development and visual pipeline

Treat each gameplay system as a bounded engineering unit: input, camera, movement, physics, AI, pathfinding, quests, inventory, save/load, UI, audio, rendering, and build/export.

### Asset pipeline
1. Define style guide: palette, proportions, line weight, camera, lighting, material rules, and resolution.
2. Create reference assets and stable prompts.
3. Generate concept material.
4. Validate production suitability separately.
5. Clean and normalize dimensions, pivots, alpha, UVs, topology, scale, rig, and collision.
6. Integrate into a test scene.
7. Capture visual regression artifacts.
8. Validate target-device performance and packaging.

### Sprite-sheet acceptance checks
- exact number of cells and frames;
- equal cell dimensions;
- stable character scale, pivot, silhouette, and lighting;
- no clipping or inter-frame teleportation;
- correct transparency and padding;
- consistent facing direction and animation timing;
- imported animation plays correctly in the target engine.

### Scene and prefab safety
Maintain scene ownership. Use version control, backups, small changes, deterministic test scenes, and diff review. Avoid multiple agents editing the same scene or prefab concurrently.

## 12. AR/VR/XR engineering

For spatial projects, record exact device, OS, Unity/Unreal/Godot version, XR runtime, SDK version, package versions, and deployment mode.

Validate coordinate frames, origin and anchor lifecycle, image/plane/object tracking, 6DoF stability, camera hierarchy, depth and occlusion, input and permissions, tracking-loss recovery, frame time, thermal behavior, battery, comfort, accessibility, and physical safety.

The editor simulator is not a substitute for on-device testing. XREAL SDK and NRSDK versions must be checked against current official XREAL documentation before implementation.

## 13. Phase 10 — Handoff

The final report must contain:
1. Goal and accepted scope.
2. Repository, branch, and baseline state.
3. Files changed and rationale.
4. Commands actually executed.
5. Tests actually run and results.
6. Evidence artifacts and citations.
7. Known defects and unverified assumptions.
8. Security and operational risks.
9. Rollback/recovery steps.
10. Recommended next action.

## 14. Definition of done

A task is complete only when acceptance criteria are met, changes are in the intended repository, meaningful diffs have been reviewed, relevant tests were run or marked unrun, unresolved issues are disclosed, no unauthorized side effects occurred, and the handoff reflects observed state rather than intended state.
