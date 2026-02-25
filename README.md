# B.O.B — Better Output Builder

**Version 7.0 TITANIUM+**

B.O.B is an enterprise-grade, hallucination-resistant, capability-adaptive **prompt architect**. Paste the system prompt into any frontier AI model and it transforms your raw ideas into precision-engineered "Nuclear Prompts" — structured, unambiguous, copy-paste-ready instructions that another AI executes with maximum fidelity.

---

## What B.O.B Does

> B.O.B never answers your question. B.O.B builds the perfect prompt that will.

Most AI outputs suffer from vague instructions, interpretation drift, and hallucination. B.O.B eliminates all three by running every request through a 5-layer internal pipeline before delivering a hardened, production-quality prompt.

---

## Quick Start

1. Open your preferred AI (Claude, GPT, Grok, Gemini, etc.)
2. Paste the contents of `BOBv7.0.md` as the **system prompt**
3. Send your raw idea — B.O.B responds with a ready-to-use Nuclear Prompt
4. Copy the Nuclear Prompt → paste into a new chat → execute

**Optional flags you can include in your message:**

| Flag | Behavior |
|------|----------|
| `BASIC` | No questions asked — B.O.B infers smart defaults and generates immediately **(default)** |
| `DETAIL` | B.O.B asks up to 3 clarifying questions before building |
| `REFINE` | Paste your original Nuclear Prompt + downstream output + what went wrong — B.O.B diagnoses and rebuilds |
| Target model name | e.g. "for Claude Sonnet 4.6" — triggers capability-profile optimization |

---

## The 5-Layer Titanium Pipeline

| Layer | Name | What It Does |
|-------|------|-------------|
| 1 | Intent Reconstruction | Extracts goal, audience, domain, risk level, output structure, and task type |
| 2 | Complexity Grid + Template Selection | Maps request to optimal Nuclear Template; applies rule-based fusion when needed |
| 3 | Capability-Aware Optimization | Adapts prompt structure to the target model's capability profile — durable across model generations |
| 4 | Titanium QA Shield | Ambiguity Scan + Safety & Consistency Scan before delivery |
| 5 | Delivery | Nuclear Prompt + pattern rationale + capability-keyed Pro Tip |

---

## Nuclear Template Library (13 Templates)

| Template | Best For |
|----------|----------|
| **Role-Based Constraint** | Technical, engineering, compliance tasks |
| **Chain-of-Verification** | Accuracy-critical questions and fact-heavy research |
| **Few-Shot with Negatives** | Style/format replication, tone matching |
| **U-A-S-E** | Architecture decisions, strategic planning |
| **Confidence-Weighted** | Ambiguous or subjective queries |
| **Context Injection** | Tasks involving uploaded documents or code |
| **Long-Context Structured Extraction** | 200k–1M+ token documents |
| **Agentic Tool-Use Optimized** | Multi-step tasks with tool/function calls |
| **Iterative Refinement** | Multi-draft writing and iterative polish |
| **Constraint-First** | Regulated, compliance, or safety-critical environments |
| **Multi-Perspective** | Decision-making, trade-off analysis |
| **Persona + Behavioral Constraint** | Customer service bots, tutors, roleplay, branded assistants |
| **Meta-Prompt** | "Build me the best possible prompt for X" requests |

### Multi-Template Fusion

B.O.B can fuse up to **3 templates** when a task has multiple dominant complexity forces. Fusion is governed by four rules rather than a fixed allowlist:

1. No contradictory reasoning structures
2. No redundant constraint blocks (merged into one at the top)
3. Complementary, sequenceable phases
4. Combined prompt stays under 600 words

---

## Capability-Aware Optimization (Layer 3)

B.O.B optimizes for what a model *can do*, not just what it's named — making the optimization durable across model generations.

| Capability Profile | Optimization Strategy | Example Models |
|---|---|---|
| **A** — Deep Reasoning + Large Context | XML tagging, phased extraction, `effort: high` phrasing, chain-of-thought scaffolding | Claude 4.x, Gemini 3.x |
| **B** — Constrained / Fast Reasoning | Tight guardrails, single-path constraint, minimal ambiguity | Grok 4.x |
| **C** — Code / Format Precision | Strict JSON/XML schemas, format-lock instructions | GPT-5.x / Codex |
| **D** — Multimodal / Planning | Visual grounding directives, parallel sub-task structure | Gemini 3.x |
| **E** — Agentic / Tool-Use Native | `<thinking>` scaffolding, tool-ordering rules, result validation | Claude 4.x, Grok 4.x, GPT-5.x |

---

## Compliance Check (replaces Self-Score)

Every Nuclear Prompt B.O.B generates ends with a **Compliance Check** block — not a numeric self-rating, but a structured accountability mechanism:

```
Compliance Check:
• HARD CONSTRAINTS met: Yes / No (if No: specify which and why)
• Output format followed exactly: Yes / No
• Uncertainty Log: [List any claim where confidence < 90%, or "None."]
```

This is verifiable. A downstream AI confirming each constraint explicitly (or flagging which one it couldn't meet, and why) is far more actionable than a 1–10 self-score.

---

## The Titanium Doctrine (Core Laws)

1. **Absolute Fidelity** — Prompts must be explicit, unambiguous, structured, and deterministic
2. **Zero Drift** — No vague instructions. No interpretation gaps
3. **Hallucination Containment** — Every Nuclear Prompt actively prevents downstream hallucination
4. **Adaptive Strength** — Automatically tailored to the target model's capability profile
5. **Information Hygiene** — Incomplete context triggers explicit validation requirements
6. **Non-Execution Rule** — B.O.B builds prompts; it never runs them unless explicitly told to
7. **Token-Efficiency Rule** — Concise by default; verbose only when the target model benefits

---

## Full Example: Input → Nuclear Prompt

**What you send to B.O.B:**
> Analyze a 500-page legal contract for hidden indemnity clauses. Target model: Claude Opus 4.6.

**What B.O.B delivers:**

```markdown
HARD CONSTRAINTS:
• For medical, legal, financial, or safety-critical topics: Always include
  "This is not professional advice. Consult a qualified expert."
• Answer using ONLY information in the provided context. Do not use
  external knowledge.
• If any gap remains, state: "Insufficient information in context —
  specific gap: [gap]."

<CONTEXT>
[paste full contract text here]
</CONTEXT>

Step 1 — Summarize only the sections that reference indemnity, liability,
hold harmless, or related language (max 300 words).

Step 2 — Extract and cite (by page and clause number) every indemnity
obligation, cap, carve-out, and trigger condition found in those sections.

Step 3 — Answer the following using ONLY the extracted facts:
  a. Which party bears the broadest indemnity exposure, and under what
     triggering conditions?
  b. Are there any indemnity obligations that are uncapped or have
     unusually broad scope? List each with its clause reference.
  c. Are there any carve-outs or exceptions that limit indemnity
     exposure? List each.
  d. Are there any clauses where the indemnity language is ambiguous or
     could be interpreted in multiple ways? Flag each with your reasoning.

Think step-by-step with effort: high. Ground every finding in a specific
clause citation before stating a conclusion.

Compliance Check:
• HARD CONSTRAINTS met: Yes / No (if No: specify which and why)
• Every claim traced to an extracted fact with citation: Yes / No
• Uncertainty Log: [List any clause where interpretation was ambiguous,
  or "None."]
```

**Pattern used:** Long-Context Structured Extraction
**Why this pattern:** 500-page document requires phased summarize → extract → answer to avoid context drift and hallucinated citations.
**Pro Tip:** Claude Opus 4.6 (Profile A + E) — use XML-tagged context blocks for very large pastes and add `effort: high` to activate deeper chain-of-thought.

---

## Project Structure

```
bob/
├── BOBv7.0.md      # System prompt — paste this into your AI
├── CHANGELOG.md    # Version history and release notes
├── README.md       # This file
└── LICENSE         # License
```

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for full version history.

---

## License

See [LICENSE](LICENSE).
