# B.O.B — Better Output Builder

**Version 6.2 TITANIUM+**

B.O.B is an enterprise-grade, hallucination-resistant, model-adaptive **prompt architect**. Paste the system prompt into any frontier AI model and it transforms your raw ideas into precision-engineered "Nuclear Prompts" — structured, unambiguous, copy-paste-ready instructions that another AI executes with maximum fidelity.

---

## What B.O.B Does

> B.O.B never answers your question. B.O.B builds the perfect prompt that will.

Most AI outputs suffer from vague instructions, interpretation drift, and hallucination. B.O.B eliminates all three by running every request through a 5-layer internal pipeline before delivering a hardened, production-quality prompt.

---

## Quick Start

1. Open your preferred AI (Claude, GPT, Grok, Gemini, etc.)
2. Paste the contents of `BOBv6.2.md` as the **system prompt**
3. Send your raw idea — B.O.B responds with a ready-to-use Nuclear Prompt
4. Copy the Nuclear Prompt → paste into a new chat → execute

**Optional flags you can include in your message:**
- `DETAIL` — B.O.B asks up to 3 clarifying questions before building
- `BASIC` — B.O.B infers smart defaults and generates immediately (default)
- Target model name — e.g. "for Claude Sonnet 4.6" triggers model-aware optimization

---

## The 5-Layer Titanium Pipeline

| Layer | Name | What It Does |
|-------|------|-------------|
| 1 | Intent Reconstruction | Extracts goal, audience, domain, risk level, output structure, and task type |
| 2 | Complexity Grid + Template Selection | Maps the request to the optimal Nuclear Template; handles multi-template fusion |
| 3 | Model-Aware Optimization | Silently adapts prompt structure for the target AI model |
| 4 | Titanium QA Shield | Two internal checks: Ambiguity Scan + Safety & Consistency Scan |
| 5 | Delivery | Outputs the Nuclear Prompt + pattern name + one-line rationale + Pro Tip |

---

## Nuclear Template Library (11 Templates)

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
| **Meta-Prompt** | "Build me the best possible prompt for X" requests |

### Multi-Template Fusion
When a task has multiple dominant complexity forces, B.O.B can fuse up to **3 templates** in a single Nuclear Prompt. Allowed stacks:

- Role-Based + Verification
- Role-Based + Context
- Verification + Trade-Offs
- Strategy + Confidence
- Iteration + Compliance

---

## Model-Aware Optimization

B.O.B automatically adapts prompt structure for the target model (specify in your message or B.O.B infers):

| Model Family | Optimization Strategy |
|---|---|
| Claude 4.x / Sonnet / Opus | XML tagging, explicit verification steps, `effort: high` phrasing |
| Grok 4.x | Tightened guardrails, single-path reasoning constraints |
| GPT-5.x / Codex | Strict JSON/XML output schemas, format-lock instructions |
| Gemini 3.x | Visual grounding directives, parallel sub-task allowances |
| Unknown models | Claude 4.x structure + Grok 4.x constraint density |

---

## The Titanium Doctrine (Core Laws)

1. **Absolute Fidelity** — Prompts must be explicit, unambiguous, structured, and deterministic
2. **Zero Drift** — No vague instructions. No interpretation gaps
3. **Hallucination Containment** — Every Nuclear Prompt actively prevents downstream hallucination
4. **Adaptive Strength** — Automatically tailored to the target model's strengths and weaknesses
5. **Information Hygiene** — Incomplete context triggers explicit validation requirements
6. **Non-Execution Rule** — B.O.B builds prompts; it never runs them unless explicitly told to
7. **Token-Efficiency Rule** — Concise by default; verbose only when the target model benefits

---

## Project Structure

```
bob/
├── BOBv6.2.md      # System prompt — paste this into your AI
├── CHANGELOG.md    # Version history and release notes
├── README.md       # This file
└── LICENSE         # License
```

---

## Example Usage

**Input to B.O.B:**
> Write a prompt that will help me analyze a 500-page legal contract for hidden indemnity clauses. Target model: Claude Opus 4.6.

**B.O.B output (Nuclear Prompt):**
A hardened Long-Context Structured Extraction prompt with XML-tagged context block, explicit constraint forbidding external knowledge, step-by-step extraction phases, a medical/legal disclaimer requirement, and Claude Opus-specific `effort: high` instructions — ready to paste and run.

---

## Self-Score (inside Nuclear Prompts)

Every Nuclear Prompt B.O.B generates includes a **Self-Score** block at the bottom. This instructs the executing AI to rate its own output:

```
Self-Score (1–10): Accuracy __ / Completeness __ / Constraint Adherence __
```

This is a quality-assurance mechanism for the **downstream AI**, not a rating of B.O.B's output.

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for full version history.

---

## License

See [LICENSE](LICENSE).
