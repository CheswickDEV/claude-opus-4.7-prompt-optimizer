# Guide: How to Write Your Input for the Optimizer

## First Things First

You don't need a **fixed format**. The optimizer is built to work with raw text. But: the more context you provide, the more precise the result.

---

## The `prompt:` Trigger (recommended)

When you want to **guarantee** an optimization — even if your input looks like a question or references attached documents — start your message with the prefix `prompt:`.

**Example:**

```
prompt: Based on the attached PDF, explain what GDPR risks
our CRM has and how we can mitigate them.
```

Without the prefix, the optimizer might, in edge cases, try to answer the question directly or analyze the PDF. With the prefix, you **always** get an optimized prompt back — including a placeholder for the document.

The prefix is case-insensitive: `prompt:`, `Prompt:`, `PROMPT:` all work.

**Rule of thumb:**
- Input is a clear optimization request? → Prefix optional.
- Input reads like a question, contains document references, or direct instructions? → **Use the prefix.**

---

## Minimal Version (always works)

Just write what you want:

```
Write me a Python script that merges CSV files
```

The optimizer automatically detects intent, domain, and complexity, and fills in what's missing.

---

## Better Version: The Four-Sentence Method

If you want better results, answer these four questions in one to two sentences each:

**1. WHAT should Claude do?** — the concrete task
**2. FOR WHOM / WHY?** — audience and purpose
**3. HOW should the result look?** — format, length, style, language
**4. WHAT SHOULD BE AVOIDED?** (optional) — explicit no-gos

**Example:**

```
Write a blog article about AI in recruiting.
Audience: HR leadership at mid-sized companies.
Roughly 1,500 words, hands-on with concrete tool recommendations.
No marketing speak, no overblown promises.
```

---

## Pro Version: Context Block

For complex tasks you can provide additional context in a structured way. You do **not** need to write XML tags — the optimizer adds those. Write naturally:

```
Task: Design a migration strategy from our on-premise Exchange to Microsoft 365.

Context: Mid-sized company with 200 employees,
3 locations, currently running Exchange 2016.
Budget around $50,000. IT team: 4 people.

Deliverable: A structured document with a phased plan,
risk assessment, cost breakdown, and checklist.

Important: Data privacy regulations must be considered.
A works council exists — change management matters.
```

---

## Special Cases

### Coding Prompts
Name the language, use case, and quality markers:

```
Python function that merges multiple PDFs.
Should handle large files (500+ pages), include error handling,
usable as a CLI tool.
```

### Creative Prompts
Specify tone, mood, audience, and length:

```
Short story in a sci-fi noir style.
Protagonist: AI forensics investigator in Neo-Berlin 2087.
About 3,000 words, dark tone, plot twist at the end.
```

### Analysis Prompts
State data source, question, and desired result:

```
Analyze the attached quarterly figures and find
the three biggest cost drivers. Result as an executive summary
for the C-suite, max one page.
```

### System Prompt Optimization
When optimizing your own system prompt, say so explicitly:

```
Optimize the following system prompt for my support project:
[your system prompt here]
The system should classify support tickets and suggest replies.
```

---

## What You DON'T Need to Do

- You don't need to write XML tags — the optimizer adds them.
- You don't need to define a role — the optimizer picks the right one.
- You don't need to know prompt engineering techniques — that's exactly what this tool is for.
- You don't need polished prose — bullet points and rough notes work fine.

---

## What Happens After Optimization?

1. You receive the optimized prompt in a code block — **one click to copy**.
2. Paste it into a new Claude conversation, a project, or your API call.
3. If something's off: tell the optimizer. It revises targeted sections.

**Tips for iterative feedback:**
- "Make the prompt shorter."
- "Add few-shot examples."
- "Change the role to [XYZ]."
- "Calibrate verbosity: this should be a deep analysis."
- "Recommend a matching effort level for API use."

**Good to know for API users:**
Opus 4.7 has no thinking enabled by default. If the optimized prompt requires multi-step reasoning, enable `thinking: {"type": "adaptive"}` in your API request and set a matching effort level (`xhigh` for coding/agentic, `high` for knowledge work). For very long agentic loops, the beta feature `task_budget` is worth a look.
