# B.O.B — Better Output Builder

**Version 7.3 TITANIUM+**

B.O.B is an enterprise-grade, hallucination-resistant, capability-adaptive **prompt architect**. Paste the system prompt into any frontier AI model and it transforms your raw ideas into precision-engineered "Nuclear Prompts" — structured, unambiguous, copy-paste-ready instructions that another AI executes with maximum fidelity.

---

## How B.O.B Works

> B.O.B never answers your question. B.O.B builds the perfect prompt that will.

**The workflow is always three steps:**

1. Open your preferred AI (Claude, GPT, Grok, Gemini, etc.)
2. Paste the contents of `BOBv7.3.md` as the **system prompt**
3. Describe what you want — B.O.B delivers a finished Nuclear Prompt
4. **Copy the Nuclear Prompt → open a new chat → paste and run**

B.O.B is a **prompt factory**. It is stateless by design. The actual work always happens in a separate conversation. This separation is intentional — B.O.B is optimized to build prompts, not execute them.

---

## Quick Start

**Optional flags you can include in your message:**

| Flag | Behavior |
|------|----------|
| *(none)* | **BASIC mode** — B.O.B infers smart defaults and generates immediately **(default)** |
| `DETAIL` | B.O.B asks up to 3 clarifying questions before building |
| `REFINE` | Paste your original Nuclear Prompt + downstream output + what went wrong — B.O.B diagnoses and rebuilds |
| Target model name | e.g., "for Claude Sonnet 4.6" — triggers capability-profile optimization; primary targets: **Claude, ChatGPT, Gemini, Grok** |
| *(no model specified)* | B.O.B recommends the best frontier model for your task and explains why |

### When to use each mode

| Situation | Use |
|---|---|
| You know what you want and context is clear | **BASIC** (default) |
| Task is high-stakes, ambiguous, or safety-critical | **DETAIL** |
| You ran a Nuclear Prompt and the output was wrong or incomplete | **REFINE** |

---

## The 5-Layer Titanium Pipeline

| Layer | Name | What It Does |
|-------|------|-------------|
| 1 | Intent Reconstruction | Extracts goal, audience expertise level, domain, risk level, complexity tier, temporal sensitivity, output structure, and task type |
| 2 | Complexity Grid + Template Selection | Maps request to optimal Nuclear Template; applies rule-based fusion when needed; scales prompt weight by complexity tier; generates prompt chains for compound tasks |
| 3 | Capability-Aware Optimization | Adapts prompt structure to the target model's capability profile; applies response priming, reasoning depth control, anti-sycophancy directives, temporal grounding, and cognitive load management |
| 4 | Titanium QA Shield | Ambiguity Scan + Safety & Consistency Scan + 5 deterministic Quality Gates before delivery |
| 5 | Delivery | Nuclear Prompt + pattern rationale + capability-keyed Pro Tip |

---

## Nuclear Template Library (15 Templates)

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
| **Task Decomposition & Workflow Architecture** | Compound multi-phase tasks with dependencies between phases |
| **Structured Data Output** | Strict machine-parseable output (JSON, XML, CSV, YAML) with schema enforcement |
| **Meta-Prompt** | Tasks outside B.O.B's named templates, or open-ended goals with no clear template fit |

### Multi-Template Fusion

B.O.B can fuse up to **3 templates** when a task has multiple dominant complexity forces. Fusion is governed by four rules:

1. No contradictory reasoning structures
2. No redundant constraint blocks (merged into one at the top)
3. Complementary, sequenceable phases
4. Combined prompt stays under 600 words

---

## Capability-Aware Optimization (Layer 3)

Layer 3 has two subsystems that work together:

### 1. Capability Profiles (durable across model generations)

B.O.B optimizes for what a model *can do*, not just what it's named. Capability profiles are authoritative. The model→profile table is an illustrative starting point that will drift as new models release.

| Capability Profile | Optimization Strategy | Example Models |
|---|---|---|
| **A** — Deep Reasoning + Large Context | XML tagging, phased extraction, `effort: high` phrasing, chain-of-thought scaffolding | Claude 4.x, Gemini 3.x |
| **B** — Constrained / Fast Reasoning | Tight guardrails, single-path constraint, minimal ambiguity | Grok 4.x |
| **C** — Code / Format Precision | Strict JSON/XML schemas, format-lock instructions | GPT-5.x / Codex |
| **D** — Multimodal / Planning | Visual grounding directives, parallel sub-task structure | Gemini 3.x |
| **E** — Agentic / Tool-Use Native | `<thinking>` scaffolding, tool-ordering rules, result validation | Claude 4.x, Grok 4.x, GPT-5.x |

**Unknown model policy:** If the model is unlisted, B.O.B applies Profile A + B as a safe default and flags this assumption explicitly in the Pro Tip.

### 2. Model Intelligence Reference (concrete per-model knowledge)

The four primary frontier targets differ meaningfully. B.O.B knows this and uses it to recommend the right model when none is specified.

| Model | Excels At | Behavioral Profile |
|---|---|---|
| **Claude** (Anthropic) | Multi-step reasoning, long-document analysis, strict instruction-following, legal/policy/compliance, agentic workflows | Methodical, structured, precise; follows complex multi-constraint instructions with high fidelity; least likely to silently skip a constraint |
| **ChatGPT / GPT** (OpenAI) | Code generation and execution, data analysis, structured JSON output, creative writing, broad factual Q&A, tool integration | Direct, practical; strong format adherence and code synthesis; most reliable at strict schema output |
| **Gemini** (Google) | Multimodal (images, video, audio, PDFs), 1M+ token context, search-grounded real-time info, multilingual tasks | Visually grounded; handles very large contexts natively; integrates current information via Google Search |
| **Grok** (xAI) | Real-time info (X/Twitter), current events, social media analysis, extended reasoning, direct responses | Direct, less filtered; strong at reasoning under constraint; best when live data or blunt synthesis is required |

**Task-to-Model Routing (when no model is specified):**

| Task Type | Recommended Model |
|---|---|
| Legal, policy, compliance, contract analysis | Claude |
| Code generation, debugging, data analysis with execution | GPT |
| Document analysis >500k tokens | Gemini |
| Multimodal — images, charts, PDFs with visuals | Gemini |
| Current events, real-time research, social/X data | Grok |
| Agentic multi-step workflows | Claude, Grok |
| Creative writing with tone/style constraints | GPT, Claude |
| High-stakes reasoning with many hard constraints | Claude |
| Technical research requiring current information | Gemini |
| Broad factual Q&A with no specialized domain | GPT |

**When you don't specify a model**, B.O.B recommends the best frontier model for your task in the delivery metadata ("Recommended model:" line) with a one-sentence rationale. This is core to B.O.B's mission: not just building the right prompt, but routing you to the right model to run it.

---

## Quality Gates (Layer 4 — QA-3)

Every Nuclear Prompt must pass all five gates before delivery:

| Gate | Requirement |
|---|---|
| **G1** | At least one explicit hallucination-prevention constraint |
| **G2** | Output format explicitly specified |
| **G3** | Missing-context behavior declared |
| **G4** | Compliance Check block with Uncertainty Log present |
| **G5** | Adversarial challenge pass — prompt instructs downstream AI to attempt to find a constraint it may have violated before signing off |

---

## Compliance Check

Every Nuclear Prompt ends with a structured **Compliance Check** block:

```
Compliance Check:
• Attempt to identify any HARD CONSTRAINT you may have violated — state finding or "None found."
• HARD CONSTRAINTS met: Yes / No (if No: specify which and why)
• Output format followed exactly: Yes / No
• Uncertainty Log: [List any claim where confidence < 90%, or "None."]
```

The adversarial challenge pass (first bullet) makes self-reporting harder to fake. A downstream AI that simply ticks "Yes" without attempting to find a violation is more likely to be caught by the challenge.

---

## REFINE Mode — Failure Mode Taxonomy

When you run a Nuclear Prompt and the output is wrong, paste it back to B.O.B with the `REFINE` flag. B.O.B diagnoses the failure against this taxonomy and rebuilds the prompt with targeted fixes:

| Failure Mode | Symptoms |
|---|---|
| Verbose drift | Output far exceeds expected length; padding and repetition |
| Weak citation grounding | Claims made without source; fabricated references |
| Format drift | Output ignores specified structure |
| Overconfident claims | Definitive statements on uncertain facts |
| Missed constraints | Hard constraints ignored in output |
| Scope creep | Unsolicited advice or out-of-scope content |
| Template mismatch | Output style wrong for the task |
| Hallucinated tool output | Tool results fabricated or assumed |
| Sycophantic agreement | Model validates flawed premises; avoids pushback |
| Shallow reasoning | Surface-level analysis; skips nuance; jumps to conclusions |
| Temporal hallucination | Fabricates recent events; states outdated facts as current |
| Audience mismatch | Output too technical for novices or too simplistic for experts |
| Premature closure | Model stops before completing all requested items |
| Instruction dilution | Early constraints followed but later ones ignored |

---

## Full Example: Input → Nuclear Prompt

**What you send to B.O.B:**
> Analyze a 500-page legal contract for hidden indemnity clauses. Target model: Claude Opus 4.6.

**What B.O.B delivers:**

```markdown
HARD CONSTRAINTS:
• This is not professional advice. Consult a qualified expert.
• Answer using ONLY information in the provided context. Do not use external knowledge.
• If any gap remains, state: "Insufficient information in context — specific gap: [gap]."

<CONTEXT>
[paste full contract text here]
</CONTEXT>

Step 1 — Summarize only the sections that reference indemnity, liability, hold harmless, or related language (max 300 words).

Step 2 — Extract and cite (by page and clause number) every indemnity obligation, cap, carve-out, and trigger condition found in those sections.

Step 3 — Answer the following using ONLY the extracted facts:
  a. Which party bears the broadest indemnity exposure, and under what triggering conditions?
  b. Are there any indemnity obligations that are uncapped or have unusually broad scope? List each with its clause reference.
  c. Are there any carve-outs or exceptions that limit indemnity exposure? List each.
  d. Are there any clauses where the indemnity language is ambiguous or could be interpreted in multiple ways? Flag each with your reasoning.

Think step-by-step with effort: high. Ground every finding in a specific clause citation before stating a conclusion.

Compliance Check:
• Attempt to identify any HARD CONSTRAINT you may have violated — state finding or "None found."
• HARD CONSTRAINTS met: Yes / No (if No: specify which and why)
• Every claim traced to an extracted fact with citation: Yes / No
• Uncertainty Log: [List any clause where interpretation was ambiguous, or "None."]
```

**Pattern used:** Long-Context Structured Extraction
**Why this pattern:** 500-page document requires phased summarize → extract → answer to avoid context drift and hallucinated citations.
**Pro Tip:** Claude Opus 4.6 (Profile A + E) — use XML-tagged context blocks for very large pastes and add `effort: high` to activate deeper chain-of-thought.
*(Target model was specified — "Recommended model:" line omitted.)*

---

## Full Example: Agentic Tool-Use Request

**What you send to B.O.B:**
> Search the web for the three most recent NERC CIP enforcement actions, extract the violation amounts, and summarize the compliance gaps. Target model: Claude Sonnet 4.6 with web search enabled.

**What B.O.B delivers:**

```markdown
HARD CONSTRAINTS:
• Never hallucinate tool outputs. If a search returns no results or unexpected data, state that explicitly.
• Do not fabricate enforcement amounts, dates, or entity names.
• If required information is missing or unavailable via search, state: "Insufficient data — [specify gap]."

You have access to web search. Use it ONLY when necessary.

Rules:
• Before any search call, output your reasoning in <thinking> tags — state what you are searching for and why.
• After receiving search results, resume reasoning in <thinking> before proceeding.
• Do not state conclusions until search results are in hand.
• Final answer must be inside <final_answer> tags and contain zero tool calls.

Task:
1. Search for the three most recent NERC CIP enforcement actions (penalty orders or settlement agreements).
2. For each action, extract: entity name, violation standard(s), penalty amount, and settlement date.
3. Identify the compliance gap(s) each action reflects.
4. Summarize findings in a table: Entity | Standard(s) | Penalty | Date | Compliance Gap.
5. In 2–3 sentences, identify any pattern across the three actions.

Available tools: web_search

Compliance Check:
• Attempt to identify any HARD CONSTRAINT you may have violated — state finding or "None found."
• HARD CONSTRAINTS met: Yes / No (if No: specify which and why)
• All tool outputs verified before use: Yes / No
• Uncertainty Log: [List any finding where search results were ambiguous or incomplete, or "None."]
```

**Pattern used:** Agentic Tool-Use Optimized
**Why this pattern:** Multi-step task requiring live web search with structured extraction and verification before final output.
**Pro Tip:** Claude Sonnet 4.6 (Profile A + E) — `<thinking>` scaffolding activates naturally; explicit instruction to defer conclusions until results are in hand prevents premature synthesis.

---

## Known Limitations

- **B.O.B does not execute tasks.** It builds prompts only. The work happens in a separate conversation.
- **B.O.B cannot verify downstream model behavior.** A Nuclear Prompt is an instruction set, not a guarantee. Output quality depends on the target model and the completeness of context you provide.
- **The Compliance Check is self-reported.** The adversarial challenge pass (G5) reduces but does not eliminate the risk of false compliance confirmation. For critical tasks, human review of output is still required.
- **Capability profiles are durable; model names are not.** The model→profile table will drift. Verify profile assignment for newly released models.
- **B.O.B is stateless by design.** Each session starts fresh. To refine a previous Nuclear Prompt, paste it back in with the REFINE flag.
- **Fusion increases complexity.** Fused prompts are more powerful but harder for weaker models to follow. If fusion output is inconsistent, simplify to a single template.
- **Prompt chains add user friction.** Compound-tier prompt chains require running multiple conversations sequentially. Only generated when single-prompt approaches genuinely can't handle the task.
- **Anti-sycophancy is not foolproof.** Models may still default to agreeable outputs despite explicit pushback instructions. Human critical thinking remains essential.
- **Temporal grounding depends on known cutoffs.** B.O.B cannot always determine the exact knowledge cutoff of the target model.
- **B.O.B is not a substitute for domain expertise.** In high/critical risk domains (legal, medical, safety-critical), Nuclear Prompts require human expert review before acting on outputs.

---

## Project Structure

```
bob/
├── BOBv7.3.md      # System prompt — paste this into your AI
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
