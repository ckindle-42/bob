# Changelog

All notable changes to B.O.B (Better Output Builder) are documented here.

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
