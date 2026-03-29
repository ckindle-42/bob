# Enhancement Review (March 29, 2026)

## Scope reviewed
- `README.md`
- `BOBv7.0.md`
- `CHANGELOG.md`

## High-impact enhancements

### 1) Add an explicit model-mapping maintenance policy
**Why**
The `BOBv7.0.md` capability map is useful, but it can drift quickly as model families and naming conventions change.

**Enhancement**
Add a short "Model Mapping Maintenance" section that defines:
- update cadence (e.g., monthly),
- confidence policy for unknown models,
- fallback behavior if model capabilities are unclear.

**Expected impact**
Reduces stale guidance risk and improves trust for users targeting newly released models.

---

### 2) Add objective quality gates for generated Nuclear Prompts
**Why**
The Titanium QA Shield concept is strong, but currently lacks concrete, measurable acceptance criteria.

**Enhancement**
Introduce 3–5 deterministic checks that can be applied manually or via scripting, for example:
- Prompt includes at least one hallucination-control constraint.
- Output format is explicitly specified.
- Missing-context behavior is declared.
- Compliance Check block is present.

**Expected impact**
Makes quality more auditable and easier to benchmark over versions.

---

### 3) Add a compact “failure modes + remedies” appendix
**Why**
Users in `REFINE` mode know *what* to paste, but not always *how* to diagnose recurring output issues.

**Enhancement**
Add a short table mapping common failure modes to fixes:
- too verbose,
- weak citation grounding,
- format drift,
- over-confident claims,
- missed constraints.

**Expected impact**
Faster iteration loop and better adoption of the `REFINE` workflow.

---

## Medium-priority enhancements

### 4) Clarify the boundary between “Pattern used” metadata and hidden internals
The docs say not to expose internal labels in some places, but also ask to return pattern rationale. Add one sentence clarifying what is always safe to expose.

### 5) Add a minimal benchmark pack
Provide 10 representative input tasks (by domain and risk level) with expected prompt properties to track regressions between versions.

### 6) Add a machine-readable version manifest
A small `version.json` could track schema version, release date, and compatibility notes for downstream toolchains.

---

## Quick wins (low effort)
- Add a one-screen “When to use BASIC vs DETAIL vs REFINE” decision guide to `README.md`.
- Add one end-to-end example for an agentic/tool-use request.
- Add a concise “Known limitations” section to reduce misuse expectations.

---

## Suggested implementation order
1. Quality gates (deterministic checks)
2. Failure modes + remedies appendix
3. Model-mapping maintenance policy
4. Decision guide in README
5. Benchmark pack + version manifest
