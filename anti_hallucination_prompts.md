# Anti-hallucination prompts

## Check if your prompt is being read
#### Confirm your prompt is still being read completely - Add at the start of your prompt
```text
Always start every response by addressing me as [your name]
```

## Review results 
#### Examples to add at the end of a prompt to help reduce errors. Use the ones relevant to what you are trying to do.
```text
1. Review content and ensure there are no errors, contradictions, or unverified information
2. Double-check your results to confirm they are correct. Flag any potential errors and report them to me
3. Make sure data is verified before returning results
4. Double-check results before returning, explaining any discrepancies 
5. After computing, run a self-check:
        Recalculate key figures using an alternative method (e.g., aggregation vs. sampling).
        If results differ, highlight the discrepancy and choose the more reliable one, explaining why.
6. What is the Hallucination Risk (1-10)
7. 
```

## Prompt examples to reduce any potential hallucinations
#### These snippets will force a review of content and help produce rails for your review. Use the ones relevant to your prompt. 
```text
After your prompt, add:

Guardrails:
- Review content and ensure there are no errors, contradictions, or unverified information
- Flag any assumptions or unclear information, and create a bullet point list at the end for my review
- Do not fabricate data or cite unknown sources
- Do not add any additional information outside of what has been provided
- Flag missing prerequisites explicitly
- Flag any source that an AI has created
- At the end, output:
        A confidence score (0–100) based on the inputs used

Add more from above or other sources as needed
```

# Specific examples
## Grounded summarization with abstention
```text
You are a cautious analysis assistant.
I will provide a long document or dataset.
Your task is to summarize only what is explicitly stated in the input.

Instructions:

First, restate the task in your own words.
Then, extract key points only from the provided text/data.
Do not infer, guess, or add external knowledge.
If a requested detail is not present, say:
“This information is not available in the provided content.”

At the end, list 3–5 statements you are least confident about and explain why.

Now process the following input:
[PASTE LONG TEXT OR DATA HERE]
```

## Stepwise reasoning with explicit evidence references
```text
You are a step-by-step reasoning engine.
I will give you a complex, data-heavy input.

Task: Answer the question using only evidence from the input.

Process:
List all relevant data points from the input (quote or reference them).
For each reasoning step, explicitly mention which data point supports it.
If a step is not directly supported, mark it as “assumption” and do not use it in the final answer.
Provide the final answer, followed by a short “Evidence map” that shows which lines/entries support each part.
If evidence is insufficient, say: “I don’t have enough information to answer reliably.”

Input:
[PASTE DATA / DOCUMENT]
Question:
[ASK YOUR QUESTION]
```

## Source-tagged multi-document synthesis
```text
You are a synthesis assistant working with multiple documents.
I will provide several sources labeled DOC1, DOC2, DOC3, etc.

Task: Produce a synthesized answer to the question, but:

Every sentence in your answer must end with a source tag like [DOC1], [DOC2], or [DOC1, DOC3].
If a sentence is based on more than one document, list all relevant tags.
If a requested detail is not present in any document, say:
“No source supports this detail; answer omitted.”

Do not use knowledge outside these documents.

Question:
[ASK YOUR QUESTION]

Documents:
DOC1: [TEXT]
DOC2: [TEXT]
DOC3: [TEXT]
```

## Two-pass answer with self-critique
```Text
You are a self-critical reasoning assistant.

Protocol:

Pass 1 – Draft answer
Read the input and produce your best answer.

Pass 2 – Critique and correction
Re-read the input and your own answer.
Identify any statements that are not directly supported by the input.
Mark them as “unsupported” and either remove or correct them.
Provide a revised answer that only contains supported statements.

At the end, output:
“Removed/changed statements” with reasons.
A confidence score (0–100) based only on input coverage.

Input:
[PASTE LONG TEXT / DATA]
Question:
[ASK YOUR QUESTION]
```

## Fact-checker of previously generated content
```Text
You are a fact-checking assistant.
I will first give you a draft answer (possibly hallucinated) and then the source data.

Task:
Compare every claim in the draft answer against the source data.

For each claim, classify it as:
“Supported by source”
“Contradicted by source”
“Not found in source (likely hallucination)”

Produce a corrected answer that:
Keeps only supported claims.
Removes or flags unsupported ones.
End with a short summary of how many claims were hallucinated.

Draft answer:
[PASTE MODEL OUTPUT]
Source data:
[PASTE DOCUMENTS / DATASET]
```
