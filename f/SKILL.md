---
name: f
description: Wrapper skill that chains translate and dogify. Use when the user invokes "$f" and wants one response containing (1) the full output of "$translate <original text>" and (2) image-generation prompts created from each sentence in "$dogify <translation output>".
---

# f

Follow this workflow strictly:
1. Run the translate behavior on the original user text.
2. Run the dogify behavior on the full translate output.
3. Return exactly two sections in this order:

```
TRANSLATION:
<verbatim translate output>

IMAGE PROMPTS:
Create an image for "<dogify sentence 1>" with the same dog, same style and same colors
Create an image for "<dogify sentence 2>" with the same dog, same style and same colors
...
```

Formatting rules:
- Keep the TRANSLATION content verbatim from translate output.
- Convert each non-empty line from dogify output into one image prompt line.
- Keep German sentence punctuation inside the quote.
- Do not add extra explanations, metadata, or headings beyond `TRANSLATION:` and `IMAGE PROMPTS:`.
