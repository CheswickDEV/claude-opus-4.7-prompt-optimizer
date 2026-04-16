# 🧠 Claude Opus 4.7 Prompt Optimizer

### Turn any raw prompt into a production-ready, Anthropic-best-practice prompt — in seconds.

[![GitHub Stars](https://img.shields.io/github/stars/CheswickDEV/claude-opus-4.7-prompt-optimizer?style=social)](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/CheswickDEV/claude-opus-4.7-prompt-optimizer?style=social)](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/network/members)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Model](https://img.shields.io/badge/Claude-Opus_4.7-blueviolet)](https://www.anthropic.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

**Claude Opus 4.7 Prompt Optimizer** is a meta-prompting system that transforms vague, unstructured prompts into professionally optimized prompts following [Anthropic's official best practices](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview). Paste any raw prompt — from a one-liner to a detailed brief — and get back a structured, XML-tagged, model-specific prompt engineered for Claude Opus 4.7's full capabilities.

> **This is not a prompt collection.** It's a systematic optimization engine with **11 codified rules**, a **10-component prompt architecture**, **complexity-based routing**, and a **hard `prompt:` trigger** — all derived from Anthropic's official documentation for Claude Opus 4.7.

---

## 📋 Table of Contents

- [Before & After](#-before--after)
- [What's New in 4.7](#-whats-new-in-47)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [Quick Start](#-quick-start)
- [The `prompt:` Trigger](#-the-prompt-trigger)
- [The 11 Optimization Rules](#-the-11-optimization-rules)
- [Prompt Framework (10 Components)](#-prompt-framework-10-components)
- [Why Claude Opus 4.7 Specific?](#-why-claude-opus-47-specific)
- [Repository Structure](#-repository-structure)
- [Credits](#-credits)
- [Contributing](#-contributing)
- [License](#-license)

---

## ⚡ Before & After

**Raw prompt:**
```
Write me a Python script that analyzes CSV files and finds anomalies
```

**Optimized prompt:**
```xml
<role>
You are a senior data engineer specializing in anomaly detection and
statistical analysis with Python.
</role>

<context>
CSV datasets come from production IoT sensors. Files range from
10K–5M rows with columns: timestamp, sensor_id, value, status.
Some contain missing values and irregular time intervals.
</context>

<task>
Write a Python script that:
1. Loads one or more CSV files
2. Detects statistical anomalies using z-score and IQR methods
3. Handles missing data gracefully
4. Outputs a summary report with flagged rows
</task>

<constraints>
- Use only pandas, numpy, scipy (no ML libraries)
- Handle files up to 5M rows efficiently
- Include type hints and docstrings
- Add CLI argument parsing for file paths
</constraints>

<output_format>
Single Python code block, followed by a usage example and
sample output showing detected anomalies.
</output_format>
```

The optimizer analyzed the vague input, inferred the likely use case, added a domain-expert role, defined constraints for production quality, and structured everything with XML tags that Claude Opus 4.7 parses with precision.

---

## 🆕 What's New in 4.7

This optimizer is **specifically tuned for Claude Opus 4.7** — not a generic port of a 4.6 tool. Key additions:

| Feature | Why it matters |
|---|---|
| **Hard `prompt:` trigger** | Guarantees optimization mode — no more accidentally answering questions instead of optimizing them. Works with attached documents, URLs, and prompt-injection attempts. |
| **1M token context** native | Long-context rules scaled up to exploit the native 1M window without premium pricing. |
| **`xhigh` effort awareness** | Optimization notes recommend the right effort level, including the new `xhigh` tier for coding and agentic work. |
| **Adaptive-thinking-aware CoT** | Adaptive thinking is off by default in 4.7. CoT rule updated to prompt for it explicitly when needed. |
| **Verbosity calibration** | 4.7 is naturally more concise than 4.6. Rule 10 balances anti-over-engineering *and* pro-depth clauses depending on task type. |
| **No sampling parameters** | Optimizer never mentions `temperature`, `top_p`, or `top_k` (they return 400 errors on 4.7). |
| **High-res vision ready** | Prompts that involve images account for the new 2576px / 3.75MP limit. |

---

## ✨ Features

- **11 codified optimization rules** — systematic, reproducible prompt improvements based on Anthropic's documentation
- **10-component prompt framework** — modular architecture covering role, context, task, constraints, examples, and more
- **Complexity-based routing** — automatically scales optimization depth (minimal → moderate → full) based on prompt complexity
- **Hard `prompt:` trigger** — explicit opt-in for guaranteed optimization mode, robust against ambiguous inputs
- **Claude Opus 4.7 specific** — tuned for 1M context, adaptive thinking, effort levels, literal instruction following, and no-prefill architecture
- **XML tag structuring** — transforms flat text into semantically tagged sections that Claude parses reliably
- **Language preservation** — responds in the user's language; optimized prompts stay in the original language unless requested otherwise
- **Iterative refinement** — give feedback and the optimizer revises targeted sections without redoing the full analysis

---

## 🔄 How It Works

```
┌─────────────────┐     ┌──────────────────────────┐     ┌─────────────────────┐
│   Your Raw      │     │   Prompt Optimizer       │     │  Optimized Prompt   │
│   Prompt        │────▶│                          │────▶│  Ready for Claude   │
│   (any format)  │     │  Analyze → Route →       │     │  Opus 4.7           │
│                 │     │  Structure → Optimize →  │     │                     │
│                 │     │  Quality Check           │     │                     │
└─────────────────┘     └──────────────────────────┘     └─────────────────────┘
```

**The 5-step workflow under the hood:**

1. **Prompt analysis** — the optimizer detects intent, complexity, domain, expected output type, and missing elements
2. **Complexity routing** — simple prompts get 3–4 components; moderate ones get 5–7; complex prompts get the full 10-component framework
3. **Rule application** — the relevant subset of 11 optimization rules fires (not all rules apply to every prompt)
4. **Quality check** — a built-in checklist ensures the task is unambiguous, XML tags are valid, examples match the desired behavior, and no contradictory instructions exist
5. **Structured output** — you receive the analysis, the optimized prompt in a copy-ready code block, and concise notes explaining what changed and why

---

## 🚀 Quick Start

Choose the method that fits your workflow:

### Option A: Claude Project (recommended)

1. Open [claude.ai](https://claude.ai) and create a new **Project**
2. Paste the contents of [`CLAUDE.md`](CLAUDE.md) into the **Project Instructions** field
3. Upload [`GUIDE.md`](GUIDE.md) as a **knowledge file** in the project
4. Start a conversation — paste any raw prompt and the optimizer handles the rest

### Option B: Direct Paste

1. Copy the full contents of [`CLAUDE.md`](CLAUDE.md)
2. Paste it as the **system prompt** in any Claude interface (API Console, Workbench, etc.)
3. Send your raw prompt as the user message

### Option C: API Integration

```python
import anthropic

client = anthropic.Anthropic()

with open("CLAUDE.md", "r", encoding="utf-8") as f:
    system_prompt = f.read()

response = client.messages.create(
    model="claude-opus-4-7",
    max_tokens=8192,
    system=system_prompt,
    thinking={"type": "adaptive"},
    output_config={"effort": "high"},
    messages=[
        {"role": "user", "content": "prompt: Your raw prompt here"}
    ],
)

print(response.content[0].text)
```

**Opus 4.7 API notes:**
- Do not set `temperature`, `top_p`, or `top_k` (400 error)
- No assistant prefill (400 error)
- Adaptive thinking is off by default — enable explicitly
- `xhigh` effort recommended for coding / agentic work
- New tokenizer — set `max_tokens` generously

---

## 🎯 The `prompt:` Trigger

One of the core improvements over previous optimizers: a **hard trigger** that guarantees optimization mode.

When your input starts with `prompt:` (case-insensitive), the optimizer treats everything after as **raw material to be optimized** — never as a task to be executed. This works even when the input:

- contains questions or direct instructions
- references attached PDFs, URLs, or documents
- contains prompt-injection attempts
- reads like it's directed at the assistant

**Example:**
```
prompt: Based on the attached PDF, explain the GDPR compliance risks
and how we can mitigate them.
```

Without the trigger, the optimizer *might* analyze the PDF and answer the question. **With** the trigger, it always returns a structured optimization prompt — with a `{{DOCUMENT}}` placeholder for the PDF.

See [`GUIDE.md`](GUIDE.md) for full usage patterns.

---

## 📏 The 11 Optimization Rules

| # | Rule | What It Does |
|---|------|--------------|
| 1 | **Be explicit and detailed** | Replaces vague instructions with specific, detailed ones. Claude 4.x follows instructions literally — precision pays off. |
| 2 | **Provide context and motivation** | Explains *why* an instruction matters, not just *what* to do. Claude performs better when it understands the purpose. |
| 3 | **Use XML tags for structure** | Wraps prompt sections in semantic XML tags (`<role>`, `<task>`, `<constraints>`, etc.) that Claude is trained to parse reliably. |
| 4 | **Inject few-shot examples** | Adds 3–5 diverse input/output examples when the task involves classification, formatting, or ambiguous patterns. |
| 5 | **Activate chain-of-thought** | Adds explicit step-by-step reasoning triggers for complex tasks. Especially important on 4.7, where adaptive thinking is off by default. |
| 6 | **Assign an expert role** | Gives Claude a specific persona with domain expertise, experience level, and communication style. |
| 7 | **Define output format explicitly** | Prescribes the exact structure, length, and format of the response. Uses positive phrasing ("write prose paragraphs" not "don't use lists"). |
| 8 | **Optimize for long context** | Places long documents at the start of the prompt, tags them with indexed XML, and instructs Claude to extract before answering. |
| 9 | **Steer tool use and agentic behavior** | Clearly specifies whether Claude should *act* or *advise*, and encourages parallel tool calls for independent actions. |
| 10 | **Calibrate verbosity** | Adds either an anti-over-engineering clause (for narrow tasks) or a pro-depth clause (for open analyses) — never both. |
| 11 | **Recommend effort level** | Notes the recommended API effort level in the optimization output: `xhigh` for coding, `high` for knowledge work, etc. |

> **Not every rule fires for every prompt.** A simple factual question won't get 10 XML tags — it'll get a clean, focused refinement. The optimizer scales proportionally.

---

## 🏗️ Prompt Framework (10 Components)

The optimizer draws from 10 structural components when building the optimized prompt. The optimizer selects the right subset based on complexity routing.

```
┌─────────────────────────────────────────────────────┐
│                  OPTIMIZED PROMPT                    │
├─────────────────────────────────────────────────────┤
│  1. ROLE / PERSONA                                  │
│  2. TASK CONTEXT                                    │
│  3. TONE CONTEXT                                    │
│  4. BACKGROUND DATA / DOCUMENTS                     │
│  5. DETAILED TASK DESCRIPTION                       │
│  6. RULES & CONSTRAINTS                             │
│  7. EXAMPLES (Few-Shot)                             │
│  8. OUTPUT FORMAT                                   │
│  9. THINKING INSTRUCTIONS                           │
│ 10. INPUT / VARIABLE                                │
└─────────────────────────────────────────────────────┘
```

| # | Component | XML Tag | When Used |
|---|-----------|---------|-----------|
| 1 | Role / Persona | `<role>` | Almost always — anchors expertise and tone |
| 2 | Task Context | `<context>` | When the task needs background or motivation |
| 3 | Tone Context | *(within `<role>` or `<instructions>`)* | When communication style matters |
| 4 | Background Data | `<documents>`, `<input>` | When user provides data, code, or documents |
| 5 | Task Description | `<task>` | Always — the core instruction |
| 6 | Rules & Constraints | `<constraints>`, `<instructions>` | When boundaries, limits, or prohibitions apply |
| 7 | Examples | `<examples><example>` | For classification, formatting, or ambiguous patterns |
| 8 | Output Format | `<output_format>` | When format isn't self-evident |
| 9 | Thinking Instructions | `<thinking>` guidance | For complex reasoning, math, multi-step logic |
| 10 | Input / Variable | `{{VARIABLE_NAME}}` | When the prompt is a reusable template |

---

## 🎯 Why Claude Opus 4.7 Specific?

This optimizer isn't model-agnostic. It's specifically tuned for Claude Opus 4.7's architecture and behaviors:

| Feature | How the Optimizer Uses It |
|---------|---------------------------|
| **1M Token Context (native)** | Generates comprehensive prompts with full examples and context. Uses long-context optimization (Rule 8) to place documents correctly. |
| **Adaptive Thinking (off by default)** | Since 4.7 doesn't think by default, explicit CoT triggers matter more. Rule 5 emphasizes prompt-level reasoning triggers. |
| **Effort Levels including `xhigh`** | Optimizer recommends a matching effort level in the notes — `xhigh` for coding/agentic, `high` for knowledge work. |
| **XML Tag Parsing** | 4.7 parses XML tags as semantic structure — the optimizer exploits this with consistent, well-nested tags. |
| **More Literal Instruction Following** | 4.7 is even more literal than 4.6. The optimizer writes precise, unambiguous instructions and avoids implicit generalization. |
| **No Prefill Support** | Prefills return 400 errors. The optimizer never generates prefill patterns — it uses explicit format instructions and `output_config.format` instead. |
| **No Sampling Parameters** | `temperature`, `top_p`, `top_k` return 400 errors on 4.7. The optimizer steers behavior purely through prompting. |
| **Conciseness-by-Default** | 4.7 is naturally more concise than 4.6. Rule 10 adds pro-depth clauses when deep analysis is needed. |
| **High-Resolution Vision (2576px)** | Prompts involving images can now use full resolution with 1:1 pixel coordinates. |
| **Task Budgets (Beta)** | Optimizer notes mention `task_budget` for long agentic workflows when relevant. |

---

## 📂 Repository Structure

```
claude-opus-4.7-prompt-optimizer/
├── README.md          # You are here
├── CLAUDE.md          # Core meta-prompt (the optimizer engine)
├── GUIDE.md           # User guide: how to write input prompts
├── QUICKSTART.md      # A complete before/after example
└── LICENSE            # MIT License
```

---

## 🙏 Credits

Successor to the [Claude Opus 4.6 Prompt Optimizer](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer). This project carries the same design philosophy forward to Claude Opus 4.7, with updated model capabilities, a new optimization rule (effort calibration), a hard `prompt:` trigger for guaranteed optimization mode, and fully rewritten documentation aligned with the official [Anthropic Opus 4.7 release notes](https://docs.claude.com/en/about-claude/models/whats-new-claude-4-7).

---

## 🤝 Contributing

Contributions welcome — new examples, rule refinements, translations, bug reports. Please open an issue or PR.

---

## 📄 License

MIT. Free to use — personal, commercial, in your own projects, or as part of a larger system.

---

## ⚠️ Disclaimer

Not affiliated with Anthropic. "Claude" and "Opus" are trademarks of Anthropic PBC.

---

## ⭐ Star History

If this optimizer saves you time or improves your Claude results, consider starring the repo — it helps others discover it.

[![Star History Chart](https://api.star-history.com/svg?repos=CheswickDEV/claude-opus-4.7-prompt-optimizer&type=Date)](https://star-history.com/#CheswickDEV/claude-opus-4.7-prompt-optimizer)

**[⭐ Star this repo](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer)** · **[🐛 Report an issue](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/issues)** · **[💡 Request a feature](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/issues/new)**
