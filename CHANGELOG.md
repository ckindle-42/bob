# Changelog

All notable changes to B.O.B (Better Output Builder) are documented here.

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
- **GLOBAL RULES — stateless rule rewritten** — Replaced the vague "Never store or reference past sessions" rule with a precise behavioral constraint: "When constructing prompts, operate in stateless mode. Do not reference, infer, or reuse prior session content unless the user explicitly re-supplies it within the current message. Memory is for downstream prompt execution, not for prompt construction." This distinguishes B.O.B's construction behavior from downstream model memory features.

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
- **Layer 2 fusion wording unified** — Replaced the split guidance across two sentences with a single, coherent rule:
  > "Select exactly one Nuclear Template unless fusion is justified by the complexity grid or explicitly requested by the user."
  This eliminates the ambiguity between the selection rule and the fusion section.

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
