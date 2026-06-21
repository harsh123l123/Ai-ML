# Module 6: Generative AI & LLMs - Prompt Engineering Guide

Prompt engineering is the practice of structuring text inputs (prompts) to large language models (LLMs) to ensure they return accurate, contextually relevant, and properly formatted responses. 

For both beginners and developers, prompt engineering is the primary way to interact with models like Gemini, GPT-4, and Claude. It is the core programming method for modern GenAI applications.

---

## 🏗️ 1. Anatomy of a Perfect Prompt

A highly effective prompt typically consists of four components:

1. **Instruction**: A specific task or action you want the model to perform.
2. **Context**: Background information or constraints (e.g. "Answer as a senior researcher", "Keep explanations simple for a 10-year-old").
3. **Input Data**: The target text, question, or payload you want processed.
4. **Output Indicator**: The desired format (e.g., Markdown table, JSON schema, bullet points).

### Example Structure:
```text
[Instruction] Summarize the input text below into 3 bullet points.
[Context] Focus only on facts related to financial earnings. Ignore general company history.
[Input Data] Text: "..."
[Output Indicator] Format:
- Bullet 1
- Bullet 2
- Bullet 3
```

---

## 🛠️ 2. Core Techniques

### A. Zero-Shot vs. Few-Shot Prompting
* **Zero-Shot**: Asking the model to perform a task without giving any examples.
  ```text
  Classify the review below as Positive or Negative.
  Review: "The screen quality is amazing!"
  Classification:
  ```
* **Few-Shot**: Giving the model a few input-output examples (shots) to establish patterns, style, or output constraints.
  ```text
  Classify the reviews:
  
  Review: "Battery died in 2 hours." -> Negative
  Review: "Decent for the price." -> Neutral
  Review: "Absolutely love it!" -> Positive
  Review: "It gets the job done." -> 
  ```

### B. Chain-of-Thought (CoT) Prompting
Asking the model to show its reasoning step-by-step before outputting the final answer. This drastically improves performance on logical, mathematical, and reasoning problems.
* **Basic prompt**: `What is 15 * 34?`
* **CoT prompt**: `Solve 15 * 34. Let's think step-by-step:`

### C. System vs. User Prompts
* **System Prompt (Instruction/Developer Prompt)**: Sets the permanent behavior, persona, rules, and guardrails for the agent.
* **User Prompt**: The input query/request supplied by the user during the chat.

---

## 🔒 3. Output Formatting & Constraints

To build software on top of LLMs, you need **predictable outputs** (like JSON). 

### Example: Forcing JSON Output
```text
Role: You are an entity extraction system.
Task: Extract names and locations from the input text.
Output Schema: Return ONLY a valid JSON object matching this structure:
{
  "entities": [
    {"name": "string", "location": "string"}
  ]
}
Constraint: Do NOT include any explanations, greetings, or markdown tags outside the JSON block.

Input: "Ada Lovelace traveled to London to meet Charles Babbage."
Output:
```

---

## 🧠 4. Advanced: ReAct (Reasoning + Action)
ReAct is a paradigm where an LLM is prompted to alternate between **Thoughts** (reasoning), **Actions** (calling external tools like Google search or databases), and **Observations** (reading tool outputs) to solve complex tasks.

This is the foundation for building **Autonomous AI Agents**.

```text
Question: Find out who won the 2026 World Cup and calculate how many years ago that was.
Thought: I need to use the web search tool to find who won the 2026 World Cup.
Action: search[2026 World Cup winner]
Observation: Italy won the 2026 World Cup.
Thought: Now I need to know the current year. The current year is 2026.
Action: calculate[2026 - 2026]
Observation: 0
Thought: I have the answer. Italy won the 2026 World Cup, which was 0 years ago.
Final Answer: Italy won the 2026 World Cup, which occurred this year (2026).
```
