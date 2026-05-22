> 🧬 [aikdna.com](https://aikdna.com) — Official website

# kdna-prompt_diagnosis

[![KDNA Spec](https://img.shields.io/badge/KDNA-v1.0--rc-4c1)](https://github.com/knowledge-dna/KDNA)
[![Trust](https://img.shields.io/badge/scope-%40aikdna-blue)](https://github.com/knowledge-dna/kdna-registry)

**Prompt diagnosis judgment** — identify why a prompt failed (task mixing, goal ambiguity, context gap), not just suggest format improvements.

## Core Insight

Most prompt failures are caused by task mixing and goal ambiguity, not missing format elements. Fix the cognitive conflict before the formatting.

## The Four Questions (v2.1 governance)

### 1. Where does it come from?

- **Authored by**: KDNA Team
- **Evidence type**: practice patterns + observed cases across prompt engineering, LLM evaluation, and agent design
- **Signed by**: `@aikdna` official trust key (fingerprint `43d22af8f0e1`)

### 2. Where does it apply?

This KDNA helps agents diagnose **prompt failures** in:

- prompts that produce well-formatted but substantively wrong output
- iterative prompt refinement that yields no improvement
- multi-objective prompts where the model defaults to generic responses
- debugging sessions where the user keeps adding instructions without adding context

### 3. How is it verified?

- `kdna verify @aikdna/prompt_diagnosis --judgment` — checks v2.1 governance fields
- `kdna compare @aikdna/prompt_diagnosis --input "<your prompt>"` — runs with/without KDNA
- `evals/` directory contains 10 standard eval cases for task mixing detection, goal ambiguity diagnosis, context gap identification, and banned term avoidance

### 4. When does it NOT apply?

**Do not load** when:

- the prompt is strictly single-task but fails due to missing library versions or incorrect API parameters
- the prompt is a straightforward translation or summary that fails due to corrupted source text
- the failure is due to context window limits or token budget constraints
- the user is asking for prompt templates rather than diagnosis

## Known Failure Risks

| Risk | When it shows up |
|------|---|
| Suggesting format fixes for task mixing | Adding roles, structure, or constraints to a cognitively overloaded prompt |
| Generic "be more specific" advice | Telling the user to add instructions without diagnosing what kind of specificity is missing |
| Recommending chain-of-thought for mixed tasks | The model reasons well to the wrong composite question |
| Treating length as quality | Praising detailed prompts that mix multiple tasks |

## Prompt Triage Framework

1. **Identify task mixing** — does the prompt ask for generation AND evaluation AND decision in one pass? If yes, split into sequenced prompts.
2. **Identify goal ambiguity** — can the user describe what a correct output would enable them to do next? If no, define outcome before rewriting.
3. **Identify context gap** — what does the model need to know that it cannot infer from the instructions?
4. **Only then** consider format improvements (role, structure, constraints).

## Files

| File | Purpose |
|------|---------|
| `KDNA_Core.json` | Axioms (with v2.1 boundaries), ontology, frameworks, causal structure, stances |
| `KDNA_Patterns.json` | Terminology, banned terms, misunderstandings (with v2.1 boundaries), self-checks |
| `KDNA_Scenarios.json` | Scenario signals that should shift strategy |
| `KDNA_Cases.json` | Concrete cases showing diagnosis in practice |
| `KDNA_Reasoning.json` | Reasoning chains: conclusion → logic → so_what |
| `KDNA_Evolution.json` | Capability stages (format optimist → task decomposer → prompt architect), measurements |
| `evals/` | 10 standard eval cases for verification |
| `kdna.json` | Domain manifest (name, version, signature, judgment_version) |

## License

CC BY 4.0 — attribution required, derivative judgment frameworks welcome.

---

## Install

```bash
kdna install @aikdna/prompt_diagnosis
kdna verify @aikdna/prompt_diagnosis --judgment
```
