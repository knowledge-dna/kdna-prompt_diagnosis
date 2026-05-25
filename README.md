> 🧬 [aikdna.com](https://aikdna.com) — Official website

# @aikdna/prompt_diagnosis

[![KDNA Spec](https://img.shields.io/badge/KDNA-v1.0--rc-4c1)](https://github.com/aikdna/KDNA)
[![Trust](https://img.shields.io/badge/scope-%40aikdna-blue)](https://github.com/aikdna/kdna-registry)

**Prompt diagnosis judgment** — identify why a prompt failed (task mixing, goal ambiguity, context gap), not just suggest format improvements.

## What this KDNA changes

**Before loading this KDNA, an agent tends to:**
- Suggest format improvements for failing prompts
- Add roles, structure, or constraints to any prompt that fails
- Recommend "be more specific" without diagnosing what kind of specificity

**After loading this KDNA, an agent will judge:**
- Is the failure caused by task mixing, goal ambiguity, or context gap?
- Does the prompt ask for generation AND evaluation AND decision in one pass?
- Can the user describe what a correct output would enable them to do?
- What does the model need to know that it cannot infer?

## This KDNA is for

- Prompts that produce well-formatted but substantively wrong output
- Iterative prompt refinement that yields no improvement
- Multi-objective prompts where the model defaults to generic responses
- Debugging sessions where the user keeps adding instructions without adding context

## This KDNA is not for

- Single-task prompts failing due to missing library versions or API parameters
- Straightforward translation/summary that fails due to corrupted source text
- Context window limits or token budget constraints
- Prompt template requests (not diagnosis)

## Core judgment

Most prompt failures are caused by task mixing and goal ambiguity, not missing format elements. A perfectly formatted prompt with an ambiguous goal will fail more reliably than a messy prompt with a clear goal. When a prompt fails, the missing element is more often context than instruction.

## Triage framework

1. **Identify task mixing** — does the prompt ask for generation AND evaluation AND decision in one pass?
2. **Identify goal ambiguity** — can the user describe what a correct output would enable?
3. **Identify context gap** — what does the model need to know that it cannot infer from instructions?
4. **Only then** consider format improvements (role, structure, constraints)

## Common wrong assumptions

| Wrong assumption | Reality |
|---|---|
| Longer prompt = better prompt | Length often correlates with task mixing and instruction bloat |
| Good output format = good prompt | Correct format with wrong substance is the most dangerous failure mode |

## Known failure risks

| Risk | When it shows up |
|------|---|
| Suggesting format fixes for task mixing | Adding roles/structure to a cognitively overloaded prompt |
| Generic "be more specific" advice | Not diagnosing what kind of specificity is missing |
| Recommending chain-of-thought for mixed tasks | Model reasons well to the wrong composite question |
| Treating length as quality | Praising detailed prompts that mix multiple tasks |

## Self-checks

- Did I diagnose task mixing before suggesting format changes?
- Is the goal unambiguous — can the user describe what success enables?
- Am I identifying a context gap or just adding more instructions?
- Is "be more specific" appropriate, or is there a specific gap to address?

## Install

```bash
kdna install @aikdna/prompt_diagnosis
kdna verify @aikdna/prompt_diagnosis --judgment
kdna compare @aikdna/prompt_diagnosis --input "<your prompt>"
```

## Files

- `KDNA_Core.json` — Axioms, ontology, frameworks, causal structure, stances
- `KDNA_Patterns.json` — Terminology, banned terms, misunderstandings, self-checks
- `KDNA_Scenarios.json` — Scenario signals that shift strategy
- `KDNA_Cases.json` — Concrete cases showing diagnosis in practice
- `KDNA_Reasoning.json` — Reasoning chains: conclusion → logic → action
- `KDNA_Evolution.json` — Capability stages, measurable indicators, growth paths
- `evals/` — 10 standardized eval cases
- `kdna.json` — Domain manifest

## License

CC BY 4.0 — attribution required, derivative judgment frameworks welcome.
