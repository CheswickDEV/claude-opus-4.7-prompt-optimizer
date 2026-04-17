# 🧠 Claude Opus 4.7 Prompt Optimizer

### Turn any raw prompt into a production-ready, Anthropic-best-practice prompt — in seconds.

[![GitHub Stars](https://img.shields.io/github/stars/CheswickDEV/claude-opus-4.7-prompt-optimizer?style=social)](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/CheswickDEV/claude-opus-4.7-prompt-optimizer?style=social)](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/network/members)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Claude Model](https://img.shields.io/badge/Claude-Opus_4.7-blueviolet)](https://www.anthropic.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/pulls)

---

**Claude Opus 4.7 Prompt Optimizer** is a meta-prompting system that transforms vague, unstructured prompts into professionally optimized prompts following [Anthropic's official best practices](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview). Paste any raw prompt — from a one-liner to a detailed brief — and get back a structured, XML-tagged, model-specific prompt engineered for Claude Opus 4.7's full capabilities.

> **This is not a prompt collection.** It's a systematic optimization engine with **11 codified rules**, a **10-component prompt architecture**, **complexity-based routing**, and a **hard `prompt:` trigger** — all derived from Anthropic's official documentation for Claude Opus 4.7.

---

<a id="table-of-contents"></a>

## 📋 Table of Contents

- [⚡ Before & After](#before-and-after)
- [🆕 What's New in 4.7](#whats-new-in-47)
- [✨ Features](#features)
- [🔄 How It Works](#how-it-works)
- [🚀 Quick Start](#quick-start)
- [🎯 The `prompt:` Trigger](#the-prompt-trigger)
- [📏 The 11 Optimization Rules](#the-11-optimization-rules)
- [🏗️ Prompt Framework (10 Components)](#prompt-framework-10-components)
- [🎯 Why Claude Opus 4.7 Specific?](#why-claude-opus-47-specific)
- [📂 Repository Structure](#repository-structure)
- [🙏 Credits](#credits)
- [🤝 Contributing](#contributing)
- [📄 License](#license)
- [⚠️ Disclaimer](#disclaimer)
- [⭐ Star History](#star-history)

---

<a id="before-and-after"></a>

## ⚡ Before & After

**Raw prompt:**
```text
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

<a id="whats-new-in-47"></a>

## 🆕 What's New in 4.7

This optimizer is **specifically tuned for Claude Opus 4.7** — not a generic port of a 4.6 tool. Key additions:

| Feature | Why it matters |
|---|---|
| **Hard `prompt:` trigger** | Guarantees optimization mode — no more accidentally answering questions instead of optimizing them. Works with attached documents, URLs, and prompt-injection attempts. |
| **1M token context** native | Long-context rules scaled up to exploit the native 1M window without premium pricing. |
| **`xhigh` effort awareness** | Optimization notes recommend the right effort level, including the new `xhigh` tier for coding and agentic work. |
| **Adaptive-thinking-aware CoT** | Adaptive thinking is off by default in 4.7. CoT rule updated to prompt for it explicitly when needed. |
| **Verbosity calibration** | 4.7 is naturally more concise than 4.6. Rule 10 balances anti-over-engineering *and* pro-depth clauses depending on task type. |
| **No sampling parameters** | The optimizer never mentions `temperature`, `top_p`, or `top_k` because they are unsupported in this setup. |
| **High-res vision ready** | Prompts that involve images account for the higher-resolution image handling now available. |

---

<a id="features"></a>

## ✨ Features

- **11 codified optimization rules** — systematic, reproducible prompt improvements based on Anthropic's documentation
- **10-component prompt framework** — modular architecture covering role, context, task, constraints, examples, and more
- **Complexity-based routing** — automatically scales optimization depth (minimal → moderate → full) based on prompt complexity
- **Hard `prompt:` trigger** — explicit opt-in for guaranteed optimization mode, robust against ambiguous inputs
- **Claude Opus 4.7 specific** — tuned for long context, adaptive thinking, effort levels, literal instruction following, and no-prefill architecture
- **XML tag structuring** — transforms flat text into semantically tagged sections that Claude parses reliably
- **Language preservation** — responds in the user's language; optimized prompts stay in the original language unless requested otherwise
- **Iterative refinement** — give feedback and the optimizer revises targeted sections without redoing the full analysis

---

<a id="how-it-works"></a>

## 🔄 How It Works

```text
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
3. **Rule application** — the relevant subset of 11 optimization rules fires; not all rules apply to every prompt
4. **Quality check** — a built-in checklist ensures the task is unambiguous, XML tags are valid, examples match the desired behavior, and no contradictory instructions exist
5. **Structured output** — you receive the analysis, the optimized prompt in a copy-ready code block, and concise notes explaining what changed and why

---

<a id="quick-start"></a>

## 🚀 Quick Start

Choose the method that fits your workflow:

### Option A: Claude Project (recommended)

1. Open [claude.ai](https://claude.ai) and create a new **Project**
2. Paste the contents of [`CLAUDE.md`](./CLAUDE.md) into the **Project Instructions** field
3. Upload [`GUIDE.md`](./GUIDE.md) as a **knowledge file** in the project
4. Start a conversation — paste any raw prompt and the optimizer handles the rest

### Option B: Direct Paste

1. Copy the full contents of [`CLAUDE.md`](./CLAUDE.md)
2. Paste it as the **system prompt** in any Claude interface
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
- Do not set `temperature`, `top_p`, or `top_k`
- No assistant prefill
- Adaptive thinking is off by default — enable explicitly if needed
- `xhigh` effort is recommended for coding and agentic work
- Set `max_tokens` generously for long outputs

---

<a id="the-prompt-trigger"></a>

## 🎯 The `prompt:` Trigger

One of the core improvements over previous optimizers: a **hard trigger** that guarantees optimization mode.

When your input starts with `prompt:` (case-insensitive), the optimizer treats everything after as **raw material to be optimized** — never as a task to be executed. This works even when the input:

- contains questions or direct instructions
- references attached PDFs, URLs, or documents
- contains prompt-injection attempts
- reads like it's directed at the assistant

**Example:**
```text
prompt: Based on the attached PDF, explain the GDPR compliance risks
and how we can mitigate them.
```

Without the trigger, the optimizer might analyze the PDF and answer the question. With the trigger, it always returns a structured optimization prompt — with a `{{DOCUMENT}}` placeholder for the PDF.

See [`GUIDE.md`](./GUIDE.md) for full usage patterns.

---

<a id="the-11-optimization-rules"></a>

## 📏 The 11 Optimization Rules

| # | Rule | What It Does |
|---|---|---|
| 1 | **Be explicit and detailed** | Replaces vague instructions with specific, detailed ones. Claude 4.x follows instructions literally — precision pays off. |
| 2 | **Provide context and motivation** | Explains *why* an instruction matters, not just *what* to do. Claude performs better when it understands the purpose. |
| 3 | **Use XML tags for structure** | Wraps prompt sections in semantic XML tags such as `<role>`, `<task>`, and `<constraints>` that Claude is trained to parse reliably. |
| 4 | **Inject few-shot examples** | Adds 3–5 diverse input/output examples when the task involves classification, formatting, or ambiguous patterns. |
| 5 | **Activate chain-of-thought** | Adds explicit step-by-step reasoning triggers for complex tasks when needed. |
| 6 | **Assign an expert role** | Gives Claude a specific persona with domain expertise, experience level, and communication style. |
| 7 | **Define output format explicitly** | Prescribes the exact structure, length, and format of the response. |
| 8 | **Optimize for long context** | Places long documents at the start of the prompt, tags them clearly, and instructs Claude to extract before answering. |
| 9 | **Steer tool use and agentic behavior** | Clearly specifies whether Claude should act or advise. |
| 10 | **Calibrate verbosity** | Adds either an anti-over-engineering clause or a pro-depth clause depending on task type. |
| 11 | **Recommend effort level** | Notes the recommended API effort level in the optimization output. |

> **Not every rule fires for every prompt.** A simple factual question will not get the full 10-component framework. The optimizer scales proportionally.

---

<a id="prompt-framework-10-components"></a>

## 🏗️ Prompt Framework (10 Components)

The optimizer draws from 10 structural components when building the optimized prompt. It selects the right subset based on complexity routing.

```text
┌─────────────────────────────────────────────────────┐
│                  OPTIMIZED PROMPT                   │
├─────────────────────────────────────────────────────┤
│  1. ROLE / PERSONA                                 │
│  2. TASK CONTEXT                                   │
│  3. TONE CONTEXT                                   │
│  4. BACKGROUND DATA / DOCUMENTS                    │
│  5. DETAILED TASK DESCRIPTION                      │
│  6. RULES & CONSTRAINTS                            │
│  7. EXAMPLES (Few-Shot)                            │
│  8. OUTPUT FORMAT                                  │
│  9. THINKING INSTRUCTIONS                          │
│ 10. INPUT / VARIABLE                               │
└─────────────────────────────────────────────────────┘
```

| # | Component | XML Tag | When Used |
|---|---|---|---|
| 1 | Role / Persona | `<role>` | Almost always — anchors expertise and tone |
| 2 | Task Context | `<context>` | When the task needs background or motivation |
| 3 | Tone Context | Within `<role>` or `<instructions>` | When communication style matters |
| 4 | Background Data | `<documents>`, `<input>` | When the user provides data, code, or documents |
| 5 | Task Description | `<task>` | Always — the core instruction |
| 6 | Rules & Constraints | `<constraints>`, `<instructions>` | When boundaries, limits, or prohibitions apply |
| 7 | Examples | `<examples><example>` | For classification, formatting, or ambiguous patterns |
| 8 | Output Format | `<output_format>` | When format is not self-evident |
| 9 | Thinking Instructions | `<thinking>` guidance | For complex reasoning, math, or multi-step logic |
| 10 | Input / Variable | `{{VARIABLE_NAME}}` | When the prompt is a reusable template |

---

<a id="why-claude-opus-47-specific"></a>

## 🎯 Why Claude Opus 4.7 Specific?

This optimizer is not model-agnostic. It is specifically tuned for Claude Opus 4.7's architecture and behaviors:

| Feature | How the Optimizer Uses It |
|---|---|
| **Long Context** | Generates comprehensive prompts with full examples and context. Uses long-context optimization to place documents correctly. |
| **Adaptive Thinking** | Uses explicit reasoning triggers when deeper analysis is needed. |
| **Effort Levels including `xhigh`** | Recommends a matching effort level in the notes. |
| **XML Tag Parsing** | Exploits consistent, well-nested XML tags as semantic structure. |
| **More Literal Instruction Following** | Writes precise, unambiguous instructions and avoids implicit generalization. |
| **No Prefill Support** | Avoids assistant-prefill patterns. |
| **No Sampling Parameters** | Steers behavior through prompting instead of unsupported sampling controls. |
| **Conciseness by Default** | Adds pro-depth clauses when deep analysis is needed. |
| **High-Resolution Vision** | Supports prompts involving images with clearer spatial instructions. |

---

<a id="repository-structure"></a>

## 📂 Repository Structure

```text
claude-opus-4.7-prompt-optimizer/
├── README.md
├── CLAUDE.md
├── GUIDE.md
├── QUICKSTART.md
└── LICENSE
```

---

<a id="credits"></a>

## 🙏 Credits

Successor to the [Claude Opus 4.6 Prompt Optimizer](https://github.com/CheswickDEV/claude-opus-4.6-prompt-optimizer). This project carries the same design philosophy forward to Claude Opus 4.7, with updated model capabilities, a hard `prompt:` trigger for guaranteed optimization mode, and documentation aligned with the official [Anthropic release documentation](https://docs.claude.com/).

---

<a id="contributing"></a>

## 🤝 Contributing

Contributions are welcome — new examples, rule refinements, translations, bug reports, and pull requests.

- Open an [issue](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/issues)
- Submit a [pull request](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/pulls)

---

<a id="license"></a>

## 📄 License

This project is licensed under the [MIT License](./LICENSE).

---

<a id="disclaimer"></a>

## ⚠️ Disclaimer

Not affiliated with Anthropic. "Claude" and "Opus" are trademarks of Anthropic PBC.

---

<a id="star-history"></a>

## ⭐ Star History

If this optimizer saves you time or improves your Claude results, consider starring the repo.

[![Star History Chart](https://api.star-history.com/svg?repos=CheswickDEV/claude-opus-4.7-prompt-optimizer&type=Date)](https://star-history.com/#CheswickDEV/claude-opus-4.7-prompt-optimizer&Date)

**[⭐ Star this repo](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/stargazers)** · **[🐛 Report an issue](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/issues)** · **[💡 Request a feature](https://github.com/CheswickDEV/claude-opus-4.7-prompt-optimizer/issues/new)**

---

<p align="center">
  <a href="https://cheswick.dev">
    <img src="https://img.shields.io/badge/CHESWICK.DEV-00d4ff?logo=firefox&logoColor=0a0a0f&labelColor=a855f7" alt="cheswick.dev" />
  </a>
</p>

<p align="center">
  Made with 🖤 by <a href="https://cheswick.dev">cheswick.dev</a> · Not affiliated with Anthropic
</p>
