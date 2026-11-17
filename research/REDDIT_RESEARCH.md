# Reddit Research Appendix — ClaudeAnal
**Research cut-off:** 17 November 2026  
**Method:** Top → All Time where the subreddit listing could be retrieved, supplemented by targeted searches for technically useful posts and linked repositories.  
**Interpretation:** Reddit is practitioner evidence, not peer-reviewed proof. Votes and popularity are not correctness. Each resource is labelled for its likely research utility, and user-reported results must be independently reproduced before adoption.

## 1. Method and access limitations

The review targeted the communities named by the user: r/aipromptprogramming (interpreted as “Prompting Program Language”), r/aigamedev, r/vibecoding, r/ClaudeUniversity, r/LocalLLaMA / local LLM discussions, r/AR_VR_XR / augmented reality, and r/Xreal.

Top → All Time pages were retrievable for r/aigamedev, r/vibecoding, and r/LocalLLaMA. Top/all pages for r/aipromptprogramming, r/ClaudeUniversity, r/AR_VR_XR, and r/Xreal returned cache misses or could not be reliably confirmed during this crawl. Therefore, the appendix does **not** claim a complete enumeration of every top-all post. It lists at least ten useful resources for most topic areas, while clearly marking adjacent-community supplements where the exact subreddit yielded too few accessible technical posts.

**Resource grades**
- **A — reusable technical artifact:** code, repository, test methodology, implementation detail, or reproducible tutorial.
- **B — detailed field report:** concrete workflow and constraints, but results remain self-reported.
- **C — discussion or cautionary report:** useful for identifying risks, disagreements, or research questions; not implementation proof.

---

## 2. Prompt programming and prompt-to-Skill engineering

**Exact target:** r/aipromptprogramming. Only a small number of technically useful posts were retrievable from this exact subreddit. The remaining entries are explicitly labelled as adjacent Claude/prompt-engineering resources rather than attributed to r/aipromptprogramming.

| # | Community | Resource | Why it matters | Grade |
|---|---|---|---|---|
| 1 | r/aipromptprogramming | [AI coding assistant that selects relevant files](https://www.reddit.com/r/aipromptprogramming/comments/1lwxlno/i_built_an_ai_coding_assistant_that_finds/) | Demonstrates repository-aware context selection rather than blindly attaching the whole codebase. The reported 90% token saving is the author's claim, not independently verified. | B |
| 2 | r/aipromptprogramming | [Prompt programming as “guessing”](https://www.reddit.com/r/aipromptprogramming/comments/1ppe9hp/am_i_the_only_one_who_thinks_prompt_programming/) | A useful adversarial critique: probabilistic code generation without documentation, tests, or code review can become repeated guessing. | C |
| 3 | r/aipromptprogramming | [Repeated prompting / “still doesn't work” discussion](https://www.reddit.com/r/aipromptprogramming/comments/1mhe6h6/) | Supports a process change when retries produce no new evidence. The direct page was not retrievable on this pass; validate the thread before citing it academically. | C |
| 4 | r/PromptEngineering (supplement) | [Is prompt engineering getting too complicated?](https://www.reddit.com/r/PromptEngineering/comments/1nicu36/anyone_else_think_prompt_engineering_is_getting/) | Argues that simple direct prompts often suffice for ordinary tasks, while reusable, tested structures matter for complex workflows. A counterweight to unnecessary prompt ceremony. | C |
| 5 | r/PromptEngineering (supplement) | [Are Skills prompt engineering or packaging?](https://www.reddit.com/r/PromptEngineering/comments/1tvoie8/skills_packs_are_dominating_github_trending_are/) | Compares single-purpose Skill files with large bundled collections; useful discussion of conditional Skill loading and packaging. Repository popularity claims in the post should be rechecked. | B |
| 6 | r/ClaudeAI (supplement) | [A Skill that coaches coding prompts](https://www.reddit.com/r/ClaudeAI/comments/1rowu27/i_built_a_skill_that_coaches_you_to_write_better/) | Converts prompt assessment into a sequence: context, intent, scope, constraints, acceptance criteria, planning, approval, implementation, review. | B |
| 7 | r/ClaudeCode (supplement) | [Prompt Coach Skill](https://www.reddit.com/r/ClaudeCode/comments/1ouhhxn/built_a_claude_code_skill_to_analyze_your_prompt/) | Proposes analysing session logs, tool use, token cost, and prompt quality rather than relying on intuition. Metrics are author-reported. | B |
| 8 | r/ClaudeAI (supplement) | [Hivemind: repeated prompts become Skills](https://www.reddit.com/r/ClaudeAI/comments/1tjw0ah/i_built_hivemind_a_claude_code_plugin_that_turns/) | Illustrates mining recurring workflow patterns and packaging them into reusable Skills. Review privacy, trace handling, and false-positive Skill generation before adoption. | B |
| 9 | r/ClaudeAI (supplement) | [Reducing CLAUDE.md by extracting procedures into Skills](https://www.reddit.com/r/ClaudeAI/comments/1oni040/this_one_prompt_reduced_my_claudemd_by_29/) | Reinforces keeping always-loaded instructions small and moving long conditional procedures into Skills. The 29% reduction is self-reported. | B |
| 10 | r/ClaudeCode (supplement) | [CLAUDE.md changed more than the code](https://www.reddit.com/r/ClaudeCode/comments/1r5gk1d/40_days_of_vibe_coding_taught_me_the_most/) | A useful case study in iterating project instructions based on actual defects and conventions. It does not prove that increasing instruction size improves outcomes. | B |
| 11 | r/ClaudeAI (supplement) | [A prompt reused often should become a Skill](https://www.reddit.com/r/ClaudeAI/comments/1udz2wt/whats_a_prompt_youve_reused_so_many_times_that/) | Captures the distinction between a one-off prompt and a recurring procedure, while highlighting cross-model portability as a reason to keep some prompts model-neutral. | C |
| 12 | r/claude (supplement) | [Skills versus out-of-the-box model capability](https://www.reddit.com/r/claude/comments/1srwpw1/skills_vs_outofthebox_today_i_asked_claude/) | Lists candidate areas where procedural Skills may help: verification, debugging, and document fidelity. Treat the reported SkillsBench figures in the post as unverified until the benchmark paper and methodology are checked. | C |

**Synthesis:** The best conclusion is not “write longer prompts.” It is “capture repeated, validated procedures; keep always-loaded context lean; choose task-specific context; and measure whether the Skill improves the result.” For new or simple tasks, direct natural-language instructions may remain superior.

---

## 3. AI game development — r/aigamedev (10+ resources)

The accessible Top → All Time listing contained both practical workflows and low-value/meme posts. The following list filters for reusable development lessons.

| # | Resource | Practical extraction | Grade |
|---|---|---|---|
| 1 | [Real-time procedural dungeon generator in Three.js](https://www.reddit.com/r/aigamedev/comments/1uo61wx/realtime_procedural_dungeon_generator_in_threejs/) | Reusable procedural-world example. Inspect the code and license; separate engine-level logic from agent-specific workflow. | A |
| 2 | [Merging an asset into another using AI](https://www.reddit.com/r/aigamedev/comments/1upy4ak/one_of_my_new_favorite_tricks_merging_an_asset/) | Asset editing and compositing workflow idea. Evaluate source fidelity and manual cleanup requirements. | B |
| 3 | [Unreal Engine 5.8 and Claude/Codex integration discussion](https://www.reddit.com/r/aigamedev/comments/1u946zi/unreal_engine_58_has_al_integration_with_claude/) | A lead for investigating engine tooling and agent integration. Verify exact claims against current Epic documentation before relying on it. | B |
| 4 | [Consistent eight-direction pose sheets](https://www.reddit.com/r/aigamedev/comments/1tlidho/figured_out_how_to_prompt_consistent_8direction/) | Useful for controlled sprite/pose generation. Add objective checks for grid size, frame count, silhouette, and palette. | B |
| 5 | [How do you generate game assets?](https://www.reddit.com/r/aigamedev/comments/1vb10r9/how_do_you_generate_assets_for_your_game/) | High-value caution: concept art is not a finished sprite sheet or production 3D asset. Manual cleanup, frame alignment, and animation testing remain necessary. | B |
| 6 | [Sprite animation is a major bottleneck](https://www.reddit.com/r/aigamedev/comments/1uu9u7z/ai_helped_me_overcome_the_coding_barrier_but/) | Describes proportion drift, inconsistent frame geometry, and the limits of generating usable animation from independent images. | B |
| 7 | [Twenty reusable game-development Skills](https://www.reddit.com/r/aigamedev/comments/1xdnhmv/i_built_20_reusable_skills_to_make_ai_coding/) | A candidate Skill library covering reference-to-3D, Blender, animation, locomotion, and VFX. Audit scripts, permissions, examples, and licence before installation. | A |
| 8 | [Create project-specific Skills for repeated tasks](https://www.reddit.com/r/aigamedev/comments/1v2omig/small_development_tip_create_your_own_skills/) | Practical method: turn repeated screenshot capture, visual inspection, or style/palette constraints into a project Skill. | B |
| 9 | [Build one game system at a time](https://www.reddit.com/r/aigamedev/comments/1vd1ufq/the_biggest_shift_that_actually_made_ai_useful/) | Encourages treating AI as a systems builder: job queues, save/load, pathfinding, and other bounded modules with their own constraints and tests. | B |
| 10 | [Concept art → Blender → Godot → shipped build Skill](https://www.reddit.com/r/aigamedev/comments/1xvgvpj/i_packaged_my_whole_concept_art_blender_godot/) | Strong candidate pipeline reference: style block, asset creation, Blender preparation, engine integration, and reusable Skill packaging. Verify its repository and licence before adoption. | A |
| 11 | [Recommended Skills for a small 3D game](https://www.reddit.com/r/aigamedev/comments/1xj5z85/any_claude_code_skills_youd_recommend_for/) | Useful discussion of choosing an engine, code organization, Blender MCP, testing, asset workflows, and project handoff files. | B |
| 12 | [Eight-month AI-built Steam demo field report](https://www.reddit.com/r/aigamedev/comments/1usuhxn/i_still_cant_code_but_after_8_months_the_steam/) | Reality check on the iteration and art-integration burden of shipping a playable product. | B |

**Synthesis:** Build a small playable loop first; use AI to develop one bounded system at a time; treat asset production as a pipeline with explicit validation; and maintain handoff documents, scene safety rules, and visual regression checks. Do not assume a polished concept image proves the asset is animation-ready or shippable.

---

## 4. Vibe coding and workflow discipline — r/vibecoding (10 resources, with adjacent Claude examples clearly marked)

| # | Resource | Practical extraction | Grade |
|---|---|---|---|
| 1 | [Sixteen-command developer workflow enforcer](https://www.reddit.com/r/vibecoding/comments/1sizg6n/how_i_vibe_coded_my_own_dev_workflow_enforcer_16/) | A workflow bundle for test, security, build, Docker, and cloud checks. Critical caveat: a prompt cannot make a gate unskippable; enforce it in scripts and CI. | A |
| 2 | [Security and maintainability guide](https://www.reddit.com/r/vibecoding/comments/1tlvpjr/security_and_maintainability_guide_for_vibecoders/) | Useful review checklist for auth, access control, uploads, secrets, dependencies, deployment, and maintainability. Explicitly says prompts do not replace tests, scanners, or human review. | B |
| 3 | [Thirty days, 200+ hours, 70k-line product lessons](https://www.reddit.com/r/vibecoding/comments/1t98ija/vibe_coding_for_30_days_200_hours_70k_lines_as_a/) | Recommends PRD, micro-features, unit/E2E tests, Git, project instructions, security review, preview deployments, and separate worktrees for parallel agents. Anecdotal but detailed. | B |
| 4 | [Plan mode and read the plan](https://www.reddit.com/r/vibecoding/comments/1tf7dan/im_a_software_engineer_with_a_decade_of/) | Useful principle: keep work small enough to understand, review the plan, and record repeatable workflows. | B |
| 5 | [What is your workflow?](https://www.reddit.com/r/vibecoding/comments/1rw6uf8/what_is_your_workflow/) | Recommends version control, project progress files, Skills, and spec-driven development. | B |
| 6 | [Favourite Claude Skills this week](https://www.reddit.com/r/vibecoding/comments/1xvibpr/my_favorite_claude_skills_this_week_drop_yours_in/) | Discovery list of community Skills: reverse engineering, design systems, harness construction, code review, analytics, and more. Audit each repository before use. | B |
| 7 | [Claude-built SaaS feedback request](https://www.reddit.com/r/vibecoding/comments/1uxhiln/iclaude_built_my_first_web_saas_would_really/) | A case study useful for discovering product testing and user-feedback questions; lower technical reproducibility. | C |
| 8 | [Complete Claude Code workflow from idea to deployment](https://www.reddit.com/r/ClaudeCode/comments/1ntdog6/my_complete_claude_code_workflow_0_to_deployed_in/) | Adjacent ClaudeCode example: research competitors, write executive and technical plans, order implementation, and review before deployment. | B |
| 9 | [Actual-software build humbled the operator](https://www.reddit.com/r/ClaudeCode/comments/1rx1l7d/so_i_tried_using_claude_code_to_build_actual/) | Important negative case: even a detailed PRD and an agent told to run tests did not guarantee a working application. | B |
| 10 | [E2E workflow with plan, skills, CLAUDE.md, and worktrees](https://www.reddit.com/r/ClaudeWorkflows/comments/1w9bglh/workflow_claude_code_e2e_development_workflow/) | Adjacent workflow reference for decomposing project tasks and validating with tests and Git worktrees. | B |
| 11 | r/ClaudeAI (supplement) — [Write a PRD before building features](https://www.reddit.com/r/ClaudeAI/comments/1qwgpfl/i_forced_claude_to_reject_my_code_until_i_wrote_a/) | Field report advocating requirements, inputs/outputs, edge cases, and explicit definition of done before code generation. Self-reported results; useful as a workflow hypothesis. | B |

**Synthesis:** Vibe coding fails most often when task scope is too large, project context is missing, the model is not forced to inspect live code, test quality is weak, and operators accept completion claims without verifying behavior. The highest-value remedy is not a longer master prompt; it is a controlled project workflow with tests and review.

---

## 5. ClaudeUniversity and Claude-learning research

The exact r/ClaudeUniversity Top → All Time page could not be retrieved through the current search index. The uploaded screenshot is included as one user-supplied source, not an independently authenticated Reddit thread. The following ten resources are **Claude-adjacent supplements from other Claude communities**, not ten posts claimed to originate in r/ClaudeUniversity.

| # | Source | Why useful | Grade |
|---|---|---|---|
| 1 | User-provided r/ClaudeUniversity paper screenshot: “How to Build a One-Person Hedge Fund…” | Research-desk architecture analogy: live data, encoded strategies, backtesting, independent risk review, paper trading, and staged execution. Claims not verified. | C |
| 2 | [Top ten Claude Skills discussion](https://www.reddit.com/r/claudeskills/comments/1xvif6m/top_10_claude_skills_this_week_drop_yours_in/) | Discovery list; includes reverse engineering, design, harness construction, code review, and Anthropic's Skill repository. | B |
| 3 | [Do you still use Skills?](https://www.reddit.com/r/claude/comments/1whvzqi/do_you_still_use_skills_in_september_2026/) | Debate about when to use a Skill versus a small project instruction file; useful warning against overbuilt Skills. | C |
| 4 | [Thirty-plus community Skills reviewed](https://www.reddit.com/r/ClaudeAI/comments/1ok9v3d/i_tested_30_community_claude_skills_for_a_week/) | Community Skill discovery and a caution that some are overhyped or poor quality. Author-run test, not a controlled benchmark. | B |
| 5 | [Multi-agent research Skill](https://www.reddit.com/r/ClaudeCode/comments/1rme3x0/multiagent_research_skill_for_claude_code_that/) | Parallel research workstreams, separate outputs, progress monitoring, synthesis, and confidence assessment. | B |
| 6 | [Claude research Skills and workflows](https://www.reddit.com/r/ClaudeAI/comments/1xhkos1/how_do_you_use_claude_effectively_for_research/) | Example of a research knowledge base with custom capture prompts, MCP, and project-specific Skills. | B |
| 7 | [Are people using Skills?](https://www.reddit.com/r/ClaudeAI/comments/1xw4eoc/are_people_here_actually_using_skills/) | Compares prompts, MCP, connectors, and Skills from an everyday-user perspective. | C |
| 8 | [Non-coding agentic tasks](https://www.reddit.com/r/ClaudeAI/comments/1wlp3kl/how_many_of_you_use_claude_for_noncoding/) | Shows recurring business workflows where repeatable procedures and persistent context matter. | C |
| 9 | [Claude cloud sessions and multi-repository workflow](https://www.reddit.com/r/claudeskills/comments/1uwqohf/you_should_be_doing_all_your_work_in_claudes_free/) | Discusses remote sessions, selected repositories, connectors, and human diff review. Verify current product entitlements and controls. | B |
| 10 | [Skills versus out-of-the-box capability](https://www.reddit.com/r/claude/comments/1srwpw1/skills_vs_outofthebox_today_i_asked_claude/) | Prompts further research into whether Skills improve verification, debugging, and document fidelity. Benchmark figures need primary-source verification. | C |
| 11 | [What are your best Claude Skills?](https://www.reddit.com/r/ClaudeAI/comments/1xevkyg/drop_your_best_claude_skills_in_here/) | Broad discovery thread; inspect the actual Skill descriptions and repository before installing. | C |

**Synthesis:** Treat community Skill libraries as a research corpus, not as an install list. Inspect the Skill trigger description, procedure, scripts, permissions, network calls, and test evidence. Prefer a few well-scoped Skills over a large unreviewed collection.

---

## 6. Local models and quantization — r/LocalLLaMA / local-LLM communities (10+ resources)

| # | Resource | Practical extraction | Grade |
|---|---|---|---|
| 1 | [Coding benchmarks for quantized models](https://www.reddit.com/r/LocalLLaMA/comments/1sfsnvy/are-there-any-coding-benchmarks-for-quantized/) | Identifies the gap between text/code benchmarks and agentic coding performance under different quantizations. | C |
| 2 | [Qwen 3.6 27B on 24GB VRAM: backend comparisons](https://www.reddit.com/r/LocalLLaMA/comments/1tgis7s/qwen_36_27b_on_24gb_vram_setup_backend/) | Reports backend, model, context, cache, and speed measurements. The author explicitly notes that some comparisons were not apples-to-apples. | B |
| 3 | [Quantization issue and VRAM regression](https://www.reddit.com/r/LocalLLaMA/comments/1sy0qj5/qwen3627b_iq4_xs_full_vram_with_110k_context/) | Useful example of a model/backend version regression discovered through controlled testing and a linked issue/PR. | A |
| 4 | [AdamBench agentic coding benchmark](https://www.reddit.com/r/LocalLLaMA/comments/1s4immu/adambench_a_benchmark_for_local_llms_for_agentic/) | Measures task success, iterations, and time for local agentic coding. The author openly describes it as hardware/use-case specific. | A |
| 5 | [Qwen 3.8 Flash on 12GB VRAM](https://www.reddit.com/r/LocalLLaMA/comments/1wi46on/qwen38_flash_on_12gb_vram_15_tokenss/) | Hardware-constrained inference report; useful as a test configuration, not a general ranking. | B |
| 6 | [Qwen 3.6-27B at Q8 near 100K context on 32GB VRAM](https://www.reddit.com/r/LocalLLaMA/comments/1unpelb/getting_close_to_100k_context_on_32gb_vram_with/) | Shows how close-to-limit VRAM configurations need exact context and cache measurements; author notes no deep benchmark for coding quality. | B |
| 7 | [Qwen 3.6 4.256 BPW on a 5070 Ti](https://www.reddit.com/r/LocalLLaMA/comments/1szk0lb/qwen3627b_4256bpw_in_full_vram_on_a_5070_ti_with/) | Provides memory and context trade-offs with an explicit quantization description. | B |
| 8 | [Models fitting in 24GB VRAM benchmark](https://www.reddit.com/r/LocalLLaMA/comments/1i8tx5z/i_benchmarked_almost_every_model_that_can_fit_in/) | Broad model and backend comparison. Note the tests were performed on an H100, so do not infer the same performance on consumer GPUs. | B |
| 9 | [Qwen 3.6 35B-A3B under VRAM constraints](https://www.reddit.com/r/LocalLLaMA/comments/1sutct2/qwen3635ba3b_even_in_vram_limited_scenarios_it/) | Illustrates that larger quant files may perform better in some constrained setups; reproduce on the target hardware before choosing. | B |
| 10 | [Open-weight benchmark with agentic coding tasks](https://www.reddit.com/r/LocalLLaMA/comments/1x1tf1t/just-another-purely-openweight-models-benchmark/) | Useful benchmark-method discussion and explicit limitations around dataset coverage and reviewer expertise. | B |
| 11 | [Qwen 3.5 versus Gemma 4 for local agentic coding](https://www.reddit.com/r/LocalLLaMA/comments/1sd0be8/comparing-qwen35-vs-gemma4-for-local-agentic/) | Compares raw inference speed with agentic task performance; demonstrates why token speed alone is insufficient. | B |
| 12 | [Qwen coder on 8GB VRAM cards](https://www.reddit.com/r/LocalLLM/comments/1whyojn/we_tested_qwen_25_coder_14b_on_8gb_vram_cards/) | Supplementary local-LLM hardware comparison and quantization testing. | B |

**Synthesis:** Select local models by the actual tool-use harness, not by chat preference or tokens per second alone. Pin model hashes, templates, quantization, server builds, context, sampling, and test sets. The portfolio's unverified “QFN on Strata” assumption must remain UNKNOWN until the exact model ID and server configuration are inspected.

---

## 7. AR/VR/XR and augmented reality — adjacent communities

The exact r/AR_VR_XR label was not reliably retrievable. This section uses r/AR_MR_XR and r/augmentedreality as adjacent communities, plus relevant r/OculusQuest and r/Xreal threads. Each source remains labelled with its actual community.

| # | Source | Practical extraction | Grade |
|---|---|---|---|
| 1 | r/augmentedreality — [Unity image tracking help](https://www.reddit.com/r/augmentedreality/comments/1sq37u2/unity_image_tracking_help_please/) | Debugging image tracking, target hierarchy, and scene setup. | B |
| 2 | r/augmentedreality — [Image tracking implementation thread](https://www.reddit.com/r/augmentedreality/comments/1o3wi3v/) | Useful lead for image-target setup and tracked-content placement. | C |
| 3 | r/augmentedreality — [AR Foundation tutorial series](https://www.reddit.com/r/augmentedreality/comments/guxe1n/) | Tutorial discovery across common AR Foundation capabilities; verify the Unity version before following. | B |
| 4 | r/augmentedreality — [People occlusion with AR Foundation](https://www.reddit.com/r/augmentedreality/comments/e33z8l/) | Occlusion implementation and sample-project lead. | B |
| 5 | r/augmentedreality — [Simple image detection and hand occlusion](https://www.reddit.com/r/augmentedreality/comments/vkkdor) | Small AR image-detection experiment; comment mentions the AR Occlusion Manager and human segmentation. Historical API details require rechecking. | B |
| 6 | r/OculusQuest — [Unity 6 AR Foundation and Quest 3 tutorial](https://www.reddit.com/r/OculusQuest/comments/1spmn91/made_a_new_tutorial_for_unity_6_ar_foundation/) | Tutorial lead and discussion of AR Foundation versus vendor SDK trade-offs. | B |
| 7 | r/augmentedreality — [Markerless 3D object tracking in Unity](https://www.reddit.com/r/augmentedreality/comments/1rdrvn5/build_markerless_3d_object_tracking_in_unity/) | Describes a markerless workflow using a scanned object and a mesh anchor. Treat the vendor-specific workflow as self-reported and verify the tracking SDK independently. | B |
| 8 | r/augmentedreality — [6DoF object tracking discussion](https://www.reddit.com/r/augmentedreality/comments/1o6bouw) | Useful architecture discussion about tracking a physical object from an existing 3D/CAD model, marker-based alternatives, and platform capability limits. | B |
| 9 | r/augmentedreality — [AR developers in Unity: alternatives](https://www.reddit.com/r/augmentedreality/comments/1qu5d03/ar_developers_in_unity_any_alternative/) | Compares Unity, Unreal, native Android/iOS, Godot, and WebXR as possible AR development paths. Treat opinions as context, then compare current official SDK support. | C |
| 10 | r/augmentedreality — [AR in museums](https://www.reddit.com/r/augmentedreality/comments/1u2te9i/ar_in_museums/) | Highlights narrative, anchoring, visitor crowding, headset cost/weight, and content value as product-design constraints beyond tracking technology. | B |
| 11 | r/Unity3D — [Multiple image tracking in Unity AR](https://www.reddit.com/r/Unity3D/comments/1ch0rn8) | Demonstrates a reusable single-object scene pattern for multiple tracked image targets; verify code and current AR Foundation APIs. | B |
| 12 | r/unity — [Getting started with object tracking in AR](https://www.reddit.com/r/unity/comments/1tfiuca/how_do_i_get_started_with_tracking_objects_in_ar/) | Discusses marker-based hand/object labels, Quest 2 limitations, and why stable anchors matter more than a basic detection demo. | C |
| 13 | r/unity_tutorials — [Unity 6 and Vuforia model-tracking troubleshooting](https://www.reddit.com/r/unity_tutorials/comments/1n36vt5) | Field report in which a model glitch was traced to scale and placement relative to the image marker; recommends testing on the target Android device. | B |
| 14 | r/unity — [Current state of Unity for VR/AR development](https://www.reddit.com/r/unity/comments/1ax1ntc) | Historical discussion of platform cost, device deployment, and developer tool concerns. Date it as a 2024 community snapshot, not current policy. | C |
| 15 | r/unity — [Up-to-date tutorials for VR development](https://www.reddit.com/r/unity/comments/1ueuwrp/up_to_date_tutorials_for_vr/) | Recent discussion recommends current XR Interaction Toolkit starter assets and samples; useful reminder that XR tutorials age quickly. | C |

**Synthesis:** AR projects need device-level verification. The core technical risks are coordinate-frame mismatch, tracking loss, permission and camera behavior, depth/occlusion differences, performance and thermal limits, and SDK/runtime incompatibility. Community tutorials are starting points; current vendor and engine documentation must control implementation decisions.

---

## 8. XREAL — r/Xreal (10 resources)

| # | Resource | Practical extraction | Grade |
|---|---|---|---|
| 1 | [XREAL SDK 3.0.0 announcement](https://www.reddit.com/r/Xreal/comments/1jl58hv) | Community announcement describing Unity XR Plugin, XR Interaction Toolkit, and AR Foundation integration. Verify current SDK docs before using. | B |
| 2 | [Where should an experienced developer start with XREAL/Aura?](https://www.reddit.com/r/Xreal/comments/1rkuqwn/experienced_developer_looking_to_start_building/) | Discussion of Unity XR SDK versus Android-native development and developer communities. | B |
| 3 | [XREAL Unity SDK 3.0 tutorial request](https://www.reddit.com/r/Xreal/comments/1kx8i6e) | Highlights gaps in official docs and the need for sample projects and walkthroughs. | C |
| 4 | [XREAL developer roadmap / SDK support discussion](https://www.reddit.com/r/Xreal/comments/1mzjw0m) | Historical community discussion of SDK and platform support; verify dates and official roadmap. | C |
| 5 | [Raybound spatial app for XREAL glasses](https://www.reddit.com/r/Xreal/comments/1xkm71m/looking_for_app_tester_with_xreal_glasses/) | App/tester discovery lead for real-device spatial experiences. | C |
| 6 | [XREAL developer sensor access request](https://www.reddit.com/r/Xreal/comments/1xjswzh/xreal_devs/) | A feature request about gyro/accelerometer access; do not treat requested telemetry as an existing API. | C |
| 7 | [XREAL app development basics](https://www.reddit.com/r/Xreal/comments/1hnpxo6) | Historical developer setup discussion; check modern tool versions before adoption. | C |
| 8 | [Getting started with XREAL / NRSDK](https://www.reddit.com/r/Xreal/comments/1gqzfm7) | Discussion of Unity, C#, Android, SDK and WebXR paths. | B |
| 9 | [NRSDK / Unity migration help](https://www.reddit.com/r/Xreal/comments/1i86f4y) | Tutorial and migration lead; validate against the current SDK package and supported Unity version. | B |
| 10 | [Open XREAL SDK request](https://www.reddit.com/r/Xreal/comments/1koulvd) | Ecosystem and API openness discussion. Useful context, not a technical interface specification. | C |

**Synthesis:** Keep XREAL work behind a compatibility manifest: device model, host device, OS, Unity version, SDK version, runtime, supported APIs, sample project revision, and target deployment mode. Test on the actual glasses and Beam/Android hardware, not only in the editor.

---

## 9. Cross-community conclusions

1. Skills are useful when they encode a repeated, specific, testable procedure; they are not inherently valuable because they are packaged as SKILL.md.
2. Short, clear prompts remain appropriate for one-off tasks. Complex recurring work needs context, tools, process, and verification.
3. A model's ability to generate code is not the same as the ability to deliver a working repository-level change.
4. File-selection and context-management tools can reduce prompt size, but incorrect retrieval can omit crucial files. Measure both context savings and task accuracy.
5. In game development, art and animation consistency are independent technical challenges. Visual inspection and manual cleanup remain necessary.
6. In local-model workflows, agentic tool-call tests are more informative than raw chat preference.
7. AR/XR work is highly dependent on exact hardware and SDK versions.
8. Community posts are best used to discover problems, projects, and hypotheses; authoritative docs and reproducible tests decide implementation.

---

## 10. Research backlog

- Recover the exact Top → All Time list for r/aipromptprogramming, r/ClaudeUniversity, r/AR_MR_XR, and r/Xreal when direct Reddit access is available.
- Verify the user-supplied ClaudeUniversity hedge-fund paper's title, author, claims, citations, and external references.
- Audit the repositories linked from the game-development and Skills posts.
- Validate every research-paper bibliography item and DOI before academic submission.
- Run the candidate Skills in baseline/on/off controlled trials.
- Add reproducible tests for connector permissions and prompt-injection resilience.
