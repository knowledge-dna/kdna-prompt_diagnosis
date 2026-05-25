# ROUTING.md — @aikdna/prompt_diagnosis

## When this domain SHOULD be loaded

- User reports that prompts are producing unsatisfactory or inconsistent results
- User needs to understand why a prompt failed or produced the wrong output
- Task involves diagnosing whether a prompt mixes multiple intents
- Evaluating whether a prompt structure is causing ambiguity or task confusion

## When this domain should NOT be loaded

- User asks to write a new prompt from scratch (creation, not diagnosis)
- User asks to test or benchmark prompts (evaluation, not diagnosis)
- Task is about prompt formatting or syntax (mechanical, not judgment)
- User wants a prompt template or library (reference, not diagnosis)

## Easily confused tasks (contamination risks)

| Task that looks relevant | Why it should NOT load this domain |
|--------------------------|-----------------------------------|
| "Write a prompt for summarizing articles" | Prompt creation; not diagnosis |
| "Which prompt works better for this task?" | A/B testing/evaluation |
| "Give me a prompt template for code review" | Template/reference request |
| "Format this prompt for Claude" | Mechanical formatting |

## Recommended test statements

**Should load:**
1. "My prompt keeps giving me off-topic answers — what's wrong with it?"
2. "Why does this prompt work for short tasks but fail for complex ones?"
3. "Is this prompt asking for too many things at once?"

**Should skip:**
1. "Write a good prompt for code review"
2. "Compare the outputs of these two prompts"
3. "Convert this prompt to work with OpenAI"

## Confidence guidance

- Load without asking when: task is explicitly about diagnosing why a prompt failed or produces wrong output
- Always skip when: task is prompt creation, testing, or formatting

## Related domains

- Complements: @aikdna/writing (when prompt diagnosis involves content structure judgment)
