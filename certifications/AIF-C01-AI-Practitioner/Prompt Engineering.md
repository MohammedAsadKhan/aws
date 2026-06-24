# AIF-C01 - Domain 3: Prompt Engineering

#aws #ai

> Part of Domain 3 (28% of exam). Covers how prompts work, techniques, best practices, and risks.

---
## What Is Prompt Engineering?
Designing and refining the input you give to an AI model to get better, more accurate output. Think of it like knowing exactly how to ask someone a question to get the answer you actually need.

---
## Prompt Elements (Building Blocks of a Prompt)

|Element|What it is|Example|
|---|---|---|
|**System message**|Tells the model what role to play|"You are a helpful customer support agent"|
|**User message**|The actual question or task|"How do I reset my password?"|
|**Assistant message**|Defines tone and format of response|"Respond in JSON format"|
|**Contextual data**|Extra info provided as background (RAG fits here)|Pasting in a document for the model to reference|
|**Model bias**|Built-in guardrails/personality baked into the model|Overrides everything else — highest priority|

### Priority Order (highest → lowest)

```
Model bias (overrides everything)
  → System message
    → Assistant message
      → User message + Contextual data
```

---
## Prompt Engineering Techniques
### Zero-Shot Prompting
Give the model a task with **no examples at all**. Just ask.

> "Write a Python function to calculate the factorial of a number."

- Simple and fast
- Works well for straightforward tasks
- Less reliable for complex or nuanced tasks

---
### Single-Shot Prompting
Give the model **one example** of what you want.

> "Create a function named factorial. For example: factorial(5) should return 120, factorial(0) should return 1."

- One example helps the model understand the format you want
- Better than zero-shot for specific output requirements

---

### Few-Shot Prompting
Give the model **multiple examples** before asking the actual task.

> "Here are examples of Python functions: [addition function], [even/odd function]. Now create a factorial function."

- Multiple examples = model learns the pattern
- Best for tasks where format and style matter
- More examples = more tokens = slightly higher cost

---
### Chain-of-Thought Prompting

Walk the model through the **reasoning step by step** before asking for the answer.

> "Factorial means multiplying all numbers from 1 to N. For example 5! = 5×4×3×2×1 = 120. Handle edge cases: 0! = 1, negative = None. Now write the function."

- Best for complex, multi-step problems
- Produces cleaner, more logical output
- Not needed for simple tasks

---
### Prompt Templates
Give the model a **structured JSON or formatted template** to fill in.

```json
{
  "function_purpose": "calculate factorial",
  "input": "non-negative integer n",
  "output": "integer or None",
  "examples": ["factorial(5) = 120", "factorial(0) = 1"]
}
```

- Easy to version control and reuse
- Clean, consistent output
- Great for teams where multiple people use the same prompt

---
## Techniques Quick-Match Table

|Scenario|Technique|
|---|---|
|Quick first attempt, no examples|Zero-shot|
|One example to guide format|Single-shot|
|Multiple examples to teach pattern|Few-shot|
|Complex reasoning or multi-step logic|Chain-of-thought|
|Reusable, structured, team-friendly prompts|Prompt templates|
|Testing AI summarization with example summaries|Few-shot|

---

## Prompt Components to Know

|Component|Purpose|Example|
|---|---|---|
|**Context**|Background info that sets the stage|"This blog targets readers aged 20-40 interested in sustainability"|
|**Instruction**|The actual task — clear, specific, brief|"Write an intro outlining 5 ways to reduce waste in daily life"|
|**Negative prompt**|What to avoid|"Do not use technical jargon or complex scientific explanations"|

> Good prompt = Context + Instruction + Negative Prompt. All three together = best output.

---
## Prompt Engineering Best Practices

|Practice|Bad example|Good example|
|---|---|---|
|**Be specific**|"Tell me about climate change"|"Explain the main causes of climate change and its impact on sea levels"|
|**Set guardrails**|"Summarize Kubernetes challenges"|"In 200 words or less, summarize key Kubernetes adoption challenges. Only consider technology challenges."|
|**Use negative prompts**|(nothing)|"Avoid technical jargon or complex explanations"|
|**Break complex queries apart**|"What are the economic and social effects of remote work?"|Ask as two separate prompts|
|**Experiment with wording**|Stick with first attempt|Try multiple variations to find what works best|

---

## Prompt Engineering Risks

|Risk|Simple explanation|Example|
|---|---|---|
|**Exposure**|Poorly designed prompts can trick the model into revealing sensitive/private data|Model leaks details about its own algorithm or training data|
|**Poisoning**|Attacker floods the model with biased/misleading prompts during training to corrupt it|Skewing sentiment analysis in a legal or medical AI|
|**Hijacking**|Attacker crafts prompts to make the model produce harmful or misleading content|Using AI to generate fake news at scale|
|**Jailbreaking**|Crafting prompts that bypass the model's safety guardrails|Asking the model to roleplay a scenario that gets it to reveal dangerous info|

### Risk Mitigation

- Robust AI safety protocols and content moderation
- Regular audits and vulnerability testing
- Clear guidelines defining what constitutes a harmful prompt

---

## Practice Questions
---
### Q1 — Identifying the Best Prompt Structure
**Question:** You are using AI to generate a blog post on sustainable living for readers aged 20-40 who want practical advice. You want an intro covering 5 ways to reduce waste. You want the AI to avoid technical jargon. Which prompt structure is best?
**A.** Context: audience is environmentally conscious people wanting sustainability tips. Instruction: write about 5 ways to reduce waste, keeping it simple. Negative prompt: avoid overly technical language or complex explanations.
**B.** Context: write an intro for a sustainability blog. Instruction: talk about reducing waste. Negative prompt: don't make it too technical.
**C.** Context: blog should discuss sustainability. Instruction: give an overview of 5 ways to reduce waste. Negative prompt: no need for extra details.
**D.** Context: writing for people interested in sustainability. Instruction: discuss 5 tips for living sustainably. Negative prompt: avoid complicated details.

**Correct Answer: A**

|Option|Why it's wrong/right|
|---|---|
|A|Correct — specific context, clear instruction, meaningful negative prompt|
|B|Too vague — "talk about reducing waste" gives no real direction|
|C|Context is too broad; "no need for extra details" isn't a useful negative prompt|
|D|Close but "avoid complicated details" is too vague compared to A's specific instruction|

**Tips & Tricks:**
- Best prompt = most specific context + clearest instruction + most actionable negative prompt
- Vague negative prompts ("don't make it complicated") are always worse than specific ones ("avoid technical jargon and complex scientific explanations")
- When comparing prompts: look for the one where all three components (context, instruction, negative prompt) are specific and actionable
- The trap options always have one weak element — find it and eliminate

---

### Q2 — Identifying the Prompt Engineering Technique
**Question:** You are working on an NLP project to generate summaries for a large set of documents. You provide the model with a few examples of well-structured summaries to help it understand the task. Which prompt engineering technique is most appropriate?
**A.** Zero-shot prompting **B.** Few-shot prompting **C.** Chain-of-thought prompting **D.** Single-shot prompting

**Correct Answer: B**

|Option|Why it's wrong/right|
|---|---|
|A|Zero-shot = no examples at all — the question explicitly says examples were provided|
|B|Correct — "a few examples" = few-shot prompting by definition|
|C|Chain-of-thought = step-by-step reasoning — not needed for summarization|
|D|Single-shot = only one example — the question says "a few" which implies multiple|

**Tips & Tricks:**

- Count the examples in the scenario: zero = zero-shot, one = single-shot, multiple = few-shot
- "A few examples" is the exact definition of few-shot — that phrase alone gives you the answer
- Chain-of-thought trap: it sounds advanced so it seems right, but it's for step-by-step reasoning problems, not summarization
- Memory trick: **Zero = none. Single = one. Few = multiple. Chain = steps.**