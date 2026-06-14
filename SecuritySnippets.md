# Prompt Snippets

## Check if your prompt is being read
### Confirmation your prompt is still being read completely - At the start of your prompt
```text
Always start every response by addressing me as [your name]
```

## Review results 
### Examples of what to add to the end of the prompt to help reduce errors
```text
- Review content and ensure there are not errors, contradictions, or unverified information
- Double check your results to confirm they are correct. Flag any potential errors and report them to me
- Make sure data is verified before returning results
```

## Guardrails Prompt to reduce any potential hallucinations
### Add to your prompt a section called Guardrails
```text
Guardrails:
- Example 1
- Example 2
- etc... 
```
## Simple Example: Prompt to reduce any potential hallucinations
```text
Guardrails:
- Review content and ensure there are not errors, contradictions, or unverified information
- Flag any assumptions or unclear information and create a bulletpoint list at the end for my review
```

## More Complex Example 2: Prompt to reduce any potential hallucinations
### Depending on your needs, you might need to get more explicit. Here are examples but you can build them out as you need them. 
```text
- Do not fabricate data or cite unknown sources
- Flag missing prerequisites explicitly
- Remove any source that has been created by an AI
```
