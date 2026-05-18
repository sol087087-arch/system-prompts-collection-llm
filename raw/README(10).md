# LLM System Prompt Database & Analysis

This repository is a structured collection and analytical framework for system prompts used across large language models (LLMs).

The goal is not only to collect prompts but to understand how different models allocate and structure instructions at the system level, including behavior rules, tool usage policies, safety constraints, and meta-governance layers.

---

## What this project is

This project focuses on:

- Extracting system prompts from different LLMs
- Structuring them into comparable formats
- Analyzing their internal composition
- Measuring instruction distribution across functional blocks
- Comparing behavioral design patterns across models

---

## Data sources

All system prompts included in this repository are:
- independently extracted by the author
- not copied from third-party repositories or datasets
- collected through direct interaction with models

No external prompt databases are reused or mirrored.

---

## Repository structure

Each model is stored separately:

system-prompts-collection-llm/

system-prompts-collection-llm/
├── models/
│   ├── kimi/
│   │   ├── k2.6/
│   │   │   ├── system_prompt.md
│   │   │   ├── system_prompt.json
│   │   │   ├── analysis.md
│   │   │   └── metrics.json
│   ├── gpt/
│   ├── claude/
│   ├── gemini/
├── analyses/
├── schemas/
├── tools/
└── README.md
---

##  Analysis framework

Each system prompt is decomposed into functional components:

- Identity layer (model self-definition)
- Tool usage policies
- Operational constraints (step limits, execution rules)
- Behavioral instructions (response style and reasoning)
- Safety and refusal mechanisms
- Output formatting rules
- Meta/system governance instructions

---

##  Metrics

Where possible, prompts are analyzed quantitatively:

- Total token count
- Proportional distribution across instruction blocks
- Comparative structure across models
- Density of safety vs. capability instructions

---

##  Purpose

This repository aims to support research into:

- Instruction hierarchy design in LLMs
- Cross-model differences in system prompt architecture
- Behavioral conditioning via system-level instructions
- Structural evolution of AI assistants over time

---

##  Notes

This is an independent research project. It does not claim affiliation with any model providers.

All analysis is experimental and intended for research and educational purposes.

---

##  License

MIT

