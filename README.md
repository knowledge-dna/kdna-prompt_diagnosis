> 🧬 [aikdna.com](https://aikdna.com) — Official website

# kdna-prompt_diagnosis

[![KDNA Spec](https://img.shields.io/badge/KDNA-v0.4-4c1)](https://github.com/knowledge-dna/KDNA)

**prompt_diagnosis** — Prompt diagnosis judgment — identify why a prompt failed (task mixing, goal ambiguity, context gap), not just suggest format improvements.

## Core Insight

Most prompt failures are task mixing and goal ambiguity, not missing format elements. Fix the cognitive conflict before the formatting.

## Install

```bash
kdna install github:knowledge-dna/kdna-prompt_diagnosis
```

## Files

| File | Purpose |
|------|---------|
| KDNA_Core.json | Axioms, ontology, frameworks, core causal structure, stances |
| KDNA_Patterns.json | Terminology, banned terms, misunderstandings, self-checks |
| kdna.json | Domain manifest |

## Validate

```bash
kdna validate .
```

## License

CC BY 4.0
