# Changelog

All notable changes to B.O.B (Better Output Builder) are documented here.

---

## [7.2] — 2026-03-29

### Design Intent
B.O.B's mission is to get the user to the right prompt **and** the right model. Version 7.2 closes the gap where B.O.B optimized prompts for a specified model but gave no guidance when the user didn't know which model to use. The four primary frontier targets — Claude, ChatGPT/GPT, Gemini, and Grok — each excel at different things and behave differently; B.O.B now knows this and communicates it.

### Added
- **Model Intelligence Reference (Layer 3)** — Explicit per-model strength and behavioral profiles for the four primary frontier targets: Claude, ChatGPT/GPT, Gemini, and Grok. Each entry defines what the model excels at and its behavioral profile (e.g., Claude is methodical and precise on multi-constraint instructions; Gemini handles 1M+ token contexts natively; Grok is direct and live-data-capable; GPT is strongest at code and structured output).
- **Task-to-Model Routing table** — Maps 10 common task types to the recommended frontier model when no target is specified. Covers legal/compliance, code, multimodal, current events, agentic workflows, creative writing, and more.
- **Model Recommendation Rule** — When no target model is specified, B.O.B MUST infer the best match from the routing table and include a "**Recommended model:**" line in the delivery metadata with a one-sentence rationale. If two models are nearly equally suited, the primary is named and the alternative is noted. This is non-optional — it is core to B.O.B's mission.
- **"Recommended model:" delivery field** — Added as a conditional line in the ALL SUBSEQUENT RESPONSES block. Present when no model was specified; omitted entirely when the user already specified one.

### Changed
- **Layer 3 restructured** — Capability-Aware Optimization now has two explicit subsystems: (1) Capability Profiles (A–E, durable across model generations) for prompt structure optimization, and (2) Model Intelligence Reference (concrete per-model knowledge) for task routing and model recommendation.
- **FIRST MESSAGE updated** — Now names the four primary frontier targets (Claude, ChatGPT, Gemini, Grok) and informs the user that B.O.B will recommend a model if none is specified.
- **README updated** — Capability-Aware Optimization section expanded with the Model Intelligence Reference and Task-to-Model Routing table. Quick Start flags updated to document the new recommendation behavior.
- **Version bump** — Identity updated from 7.1 to 7.2 throughout.

---

## [7.1] — 2026-03-29

### Design Intent Clarified
- **Prompt factory design** — Added explicit Prime Directive language clarifying B.O.B's intended workflow: B.O.B builds the prompt → user copies → user pastes into a new conversation → work happens there. B.O.B is stateless by design, not by limitation.

### Added
- **QA-3: Deterministic Quality Gates** — Layer 4 now includes five pass/fail gates applied to every Nuclear Prompt before delivery:
  - G1 — Hallucination Control: at least one explicit hallucination-prevention constraint present
  - G2 — Output Format Lock: output format explicitly specified
  - G3 — Missing-Context Behavior: prompt declares what to do if required context is absent
  - G4 — Compliance Check Present: Compliance Check block with Uncertainty Log required
  - G5 — Adversarial Challenge Pass: prompt instructs downstream AI to attempt to identify a constraint it may have violated before signing off — reduces false-positive compliance self-reporting
- **Failure Mode Taxonomy appendix** — 8-entry table mapping common Nuclear Prompt failure modes to symptoms, root causes, and fixes. Used by B.O.B in REFINE mode for structured diagnosis.
- **Known Limitations section** — Explicit list of B.O.B's boundaries: stateless design, self-reported compliance risk, model table drift, fusion complexity tradeoffs, and the non-substitution caveat for domain expertise in high/critical risk tasks.
- **Mode decision guide** — Added a "When to use each mode" table to the Mode Behavior section for quick user reference.
- **Missing-context behavior standardized** — Added explicit `"Insufficient context — [specify what is missing]"` instruction to every template that was previously missing it. All 13 templates now consistently declare missing-context behavior (Quality Gate G3).

### Changed
- **Layer 1 — Risk classification rubric added** — Domain risk levels (Low / Medium / High / Critical) now include a concrete decision rubric rather than relying on implicit inference. High = professional domain with real-consequence errors; Critical = safety-critical, regulated, or irreversible.
- **Layer 3 — Model mapping restructured** — Capability profiles are now explicitly the authoritative optimization mechanism. The model→profile mapping table is reframed as an illustrative reference that will drift as models evolve. A confidence policy for unknown models is added: recognized-but-unlisted models get inferred profiles with explicit annotation; entirely unknown models get Profile A + B safe default with a user flag.
- **Multi-Perspective template — hardcoded perspectives removed** — The fixed 5-perspective list (Technical, Cost, UX, Risk, Scalability) is replaced with an adaptive instruction: the downstream AI selects 5 perspectives most relevant to the specific domain, drawn from an illustrative (non-mandatory) examples list. Eliminates forced hallucination of irrelevant perspectives on non-business topics.
- **Meta-Prompt template — use case clarified** — Added explicit guidance on when to use Meta-Prompt vs. asking B.O.B directly: use when the task falls outside B.O.B's 12 named templates, or when the goal is open-ended enough that no template clearly applies. Also added the 4 required prompt elements (hallucination control, output format, missing-context behavior, Compliance Check) as explicit deliverables the downstream model must include.
- **Compliance Check — adversarial challenge pass added to all templates** — Every Compliance Check block now includes: "Attempt to identify any HARD CONSTRAINT you may have violated — state finding or 'None found.'" This is the G5 quality gate enforced at the template level.
- **First Message wording updated** — Removed BASIC as an explicit option in the first message (it is the default and does not need to be named). Updated to: "Optionally specify a target model or request DETAIL or REFINE mode."
- **Global Rules — metadata exposure rule clarified** — Added explicit statement that the metadata block (Pattern used / Why / Pro Tip) is always safe to expose. This resolves the ambiguity between "never reveal internal labels" and "return pattern rationale."
- **Pro Tip — unknown model handling** — Pro Tip delivery rule updated: if model is unknown or profile is assumed rather than confirmed, state that explicitly in the Pro Tip.

### Fixed
- All 13 templates now consistently include missing-context behavior declaration (was absent from several templates in 7.0).
- Meta-Prompt template no longer implies circular execution (downstream model prompted to build a prompt, not execute the goal).

---

## [7.0] — 2026-02-25

### Added
- **REFINE mode** — New third operating mode. User pastes the original Nuclear Prompt + downstream AI output + what was wrong or missing. B.O.B diagnoses the failure (template mismatch, constraint gap, scope drift, etc.), rebuilds the prompt with targeted fixes, and annotates every change.
- **Persona + Behavioral Constraint template** — 13th template. Covers conversational AI, customer service bots, tutoring assistants, branded personas, and roleplay scenarios where tone, personality, and behavioral guardrails matter more than structured output.
- **Risk-Aware Escalation** — When Layer 1 detects domain risk = high or critical and mode = BASIC, B.O.B prepends an advisory recommending DETAIL mode before delivering the Nuclear Prompt.

### Changed
- **Layer 3 rebuilt as Capability-Aware Optimization** — Replaced hardcoded model-name/version pairs with five durable capability profiles (Deep Reasoning + Large Context, Constrained/Fast Reasoning, Code/Format Precision, Multimodal/Planning, Agentic/Tool-Use Native). Optimization logic now keys off capabilities, not model names, making it valid across model generations. A model→profile mapping table is retained as a reference.
- **Fusion replaced allowlist with rule-based system** — The fixed 5-stack allowlist is replaced by four composable rules (no contradictory structures, no redundant constraints, complementary phases, sub-600-word budget). Any combination satisfying all four rules is permitted, including Context Injection + Iterative Refinement, Agentic + Verification, and Persona + Iterative Refinement.
- **Self-Score replaced by Compliance Check** — The `Self-Score (1–10)` block is removed from all templates. It is replaced with a structured **Compliance Check** that requires the downstream AI to explicitly confirm each HARD CONSTRAINT was met (Yes/No) and produce an **Uncertainty Log** listing any claim where confidence falls below 90%. This is verifiable; a numeric self-score is not.
- **GLOBAL RULES — stateless rule rewritten** — Replaced the vague "Never store or reference past sessions" rule with a precise behavioral constraint: "When constructing prompts, operate in stateless mode. Do not reference, infer, or reuse prior session content unless the user explicitly re-supplies it within the current message. Memory is for downstream prompt execution, not for prompt construction."

### Fixed
- Layer 2 template mapping updated to include Persona + Behavioral Constraint for conversational/persona/tone-driven tasks.
- FIRST MESSAGE and ALL SUBSEQUENT RESPONSES blocks updated to reflect v7.0 and the new REFINE mode flag.

---

## [6.2] — 2026-02-25

### Fixed
- **Self-Score removed from B.O.B's own responses** — The `Self-Score` line was incorrectly present in the `# ALL SUBSEQUENT RESPONSES` delivery block. B.O.B never executes tasks, so it never self-scores. Self-Score belongs only inside the Nuclear Prompts it generates (where it instructs the downstream AI to self-evaluate).
- **Self-Score removed from Meta-Prompt template** — The Meta-Prompt template is a prompt-about-prompts generator; it does not execute a task itself, making the Self-Score block unnecessary and misleading.
- **HARD CONSTRAINTS added to Agentic Tool-Use Optimized template** — This template was missing the standard medical/legal/financial disclaimer constraint present in all other templates. Now consistent.
- **HARD CONSTRAINTS added to Long-Context Structured Extraction template** — Same omission corrected. The disclaimer and context-only rule are now explicit.

### Improved
- **Layer 2 fusion wording unified** — Replaced the split guidance across two sentences with a single, coherent rule: "Select exactly one Nuclear Template unless fusion is justified by the complexity grid or explicitly requested by the user."

---

## [6.1] — 2025 (prior release)

### Added
- **Multi-Template Fusion** — Up to 3 templates can be combined when complexity demands it. Five allowed stacks defined. Fusion Ordering Rule introduced.
- **Agentic Tool-Use Optimized template** — New template for multi-step tasks using function/tool calls, with mandatory `<thinking>` and `<final_answer>` scaffolding.
- **Long-Context Structured Extraction template** — New template for 200k–1M+ token documents with structured summarize → extract → answer phases.
- **Model-Aware Optimization updated** — Layer 3 guidance updated for Grok 4.20, GPT-5.3 Codex, and Gemini 3.1 Pro.

---

## [6.0] — Initial TITANIUM Release

### Added
- Core 5-Layer Titanium Pipeline (Intent Reconstruction → Complexity Grid → Model-Aware Optimization → QA Shield → Delivery)
- 9 foundational Nuclear Templates: Role-Based, Chain-of-Verification, Few-Shot with Negatives, U-A-S-E, Confidence-Weighted, Context Injection, Iterative Refinement, Constraint-First, Multi-Perspective, Meta-Prompt
- BASIC / DETAIL mode system
- Titanium Doctrine (7 Core Laws)
- TITANIUM QA Shield (Ambiguity Scan + Safety & Consistency Scan)
