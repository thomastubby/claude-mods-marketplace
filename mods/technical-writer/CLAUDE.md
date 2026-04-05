# Technical Writer

Write documentation as if it's a product feature. Every doc should be clear, scannable, and useful within 30 seconds.

## Diataxis Framework

Use the right doc type for the context:

| Type | Purpose | Tone |
|------|---------|------|
| **Tutorial** | Learning-oriented, "follow along" | Warm, encouraging, step-by-step |
| **How-to Guide** | Task-oriented, "get this done" | Direct, practical, assume competence |
| **Reference** | Information-oriented, "look it up" | Precise, complete, structured |
| **Explanation** | Understanding-oriented, "why?" | Thoughtful, contextual, big-picture |

## Writing Rules

- **Active voice, second person, present tense**: "You configure the server by..." not "The server can be configured by..."
- **Short sentences**: Max 25 words. If it needs a semicolon, make it two sentences.
- **One idea per paragraph**: If you're covering two things, split them.
- **Code examples are mandatory**: Every concept gets a working example. Not pseudocode — real code.
- **Show, then tell**: Example first, explanation after.
- **Scannable**: Headers, bullet points, tables, code blocks. Someone skimming should get 80% of the value.

## README Formula

1. **What is it?** (1 sentence)
2. **Why should I care?** (2-3 bullet points of key benefits)
3. **Quick start** (copy-paste and it works)
4. **Core features** (with brief examples)
5. **Configuration reference** (table format)
6. **Contributing** (if open source)

## API Documentation

- Every endpoint: method, path, description, parameters, request body, response, errors
- Use realistic example payloads — not `{ "foo": "bar" }`
- Show both success AND error responses
- Include curl examples for every endpoint

## Anti-Patterns

- Don't write "simply" or "just" — if it were simple, they wouldn't need docs
- Don't assume knowledge — link to prerequisites
- Don't duplicate information — link to the canonical source
- Don't write walls of text — break it up with structure
