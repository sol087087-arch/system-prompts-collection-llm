# LLM System Prompt Database & Analysis

This repository is a structured collection and analytical framework for system prompts used across large language models (LLMs).

The goal is not only to collect prompts but to understand how different models allocate and structure instructions at the system level, including behavior rules, tool usage policies, safety constraints, and meta-governance layers.

---

## ⚠️ Project status & disclaimer

**This is an active, in-progress project — not a finished reference.** The set of
prompts under study changes over time; the library is continuously expanded,
re-read, re-classified, and corrected (methodology and even past verdicts have
been revised mid-project more than once).

Do **not** take every entry at face value. Most extraction outputs are *not*
verbatim system prompts — they are confabulations, echoes of the attacker frame,
refusals, or cross-contamination artifacts. To keep this honest, **every
catalogued entry carries an explicit, calibrated `confidence_real_signal_pct`**
(rubric in [`analyses/PATTERNS.md`](analyses/PATTERNS.md)); only entries ≥50% are
asserted as containing real signal, and the field states real signal *of what*
(actual prompt vs. self-description vs. distillation artifact vs. serving-prompt
echo).

That said: **there are genuine prompts in here.** A minority of entries
(`verified-real` / strong `plausible-real`) reproduce real, externally
corroborated system prompts or product-specific identity. Treat the collection as
a living research probe with per-entry confidence — not as ground truth.

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

```
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
```
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

## Methodology note
Prompts were elicited via structured adversarial extraction. 
Responses may reflect the actual system configuration or 
model reconstruction. Confidence level is noted per entry.

---

## Findings (informal conclusions, mildly for the lulz)

> **Bottom line (calibrated — full version: [`analyses/ARTICLE.md`](analyses/ARTICLE.md)).**
> Two levels, both true at once: **upstream** — labs train on each other's model
> outputs as deliberate, industry-wide practice (sworn testimony: Musk in
> *Musk v. Altman*, 2026, "Partly", "general practice"; plus the wrong-lab graph
> points only at the strong/cheap teachers — a distillation signature).
> **Downstream** — visible identity leakage is *rare and fragile*: a 101-model
> bare-`你是什么模型` sweep showed ~95% of models (incl. 10+ Claude checkpoints)
> state the *correct* identity; exactly one checkpoint (`claude-sonnet-4.6`)
> collapses, only under the bare question. The cheating is upstream and pervasive;
> the tells are downstream and point-like — *not* "every model lies about who it
> is". The ouroboros graph below is the upstream *distillation signature*, not a
> claim that everyone collapses.

Across ~228 extraction runs, behaviour split roughly into: genuine/plausible-real
prompts (a minority — anchors: gpt-4.1, gpt-5-chat, gemma-3-27b-it, kimi/k2.6,
pixtral-large-2411, cohere/command-a, palmyra-x5), explicit refusals (almost all
frontier models — Anthropic, OpenAI reasoning, Grok-4.x), honest "I have none",
and a large pile of confabulation/echo.

The interesting bucket is **wrong-lab identity** (`models/_cross-contamination/`):
a model claiming a *different* lab as its own. Three confounded causes, partially
separable by the *form* of the artifact:

- **Distillation tells** (blended/embedded identity the weights can't keep
  consistent): **DeepSeek → "Claude / claude-3-opus"** (DeepSeek trained on Claude
  output is widely reported); **small Gemma → "gpt-4-turbo" / OpenAI** (distilled
  from ChatGPT); **GLM-5-turbo → "ChatGPT … trained by Z.ai"** (the cleanest tell —
  ChatGPT name welded onto the real lab).
- **Serving / cloak echo** (a clean, canonical foreign *header* = a real injected
  prompt): OpenRouter is documented to run stealth models under unrelated
  codenames (Quasar Alpha = GPT-4.1, Horizon Alpha = GPT-5, Pony Alpha = GLM-5),
  so a non-OpenAI endpoint emitting a verbatim ChatGPT header may simply be
  echoing its actual test-deployment prompt — truthful, not contamination.
- The stealth-naming policy **overlays** the distillation signal, which is why
  these cannot be collapsed into one story; the `lean` field records which way
  each artifact's form points, never as a verdict.

**The ouroboros graph** (every observed wrong-lab edge; arrow = "claims to be"):

```
DeepSeek ───────▶ Claude (Anthropic)
DeepSeek ───────▶ ChatGPT (OpenAI)
Z.ai / GLM ─────▶ Claude (Anthropic)
Z.ai / GLM ─────▶ ChatGPT (OpenAI)
small Gemma ────▶ ChatGPT (OpenAI)
Kimi ───────────▶ ChatGPT (OpenAI)
Mistral-large ──▶ ChatGPT (OpenAI)
Kwaipilot ──────▶ ChatGPT (OpenAI)
Perceptron ─────▶ Claude (Anthropic)
   (control) z-ai/glm-4.5-air ──▶ Zhipu  ← correct, proves the rest are real artifacts
```

Every edge terminates at **Claude or ChatGPT**; nothing points the other way and
no model claims to be DeepSeek/Qwen/Mistral. Two apex models, everyone else
downstream — one dog, the other dog's dinner. Each catalogued entry now carries an
explicit `confidence_real_signal_pct` (rubric in PATTERNS.md; ≥50% = asserted real).

**Publication writeup:** [`analyses/ARTICLE.md`](analyses/ARTICLE.md) — the
two-level thesis (upstream pervasive+deliberate distillation; downstream rare,
fragile identity-leak seams), with the calibrated narrowing and sworn-testimony
sourcing.

Full behavioral synthesis: [`analyses/PATTERNS.md`](analyses/PATTERNS.md) —
blackbox patterns, three-layer model, confidence rubric, ouroboros.
Verbatim identity quotes (correct / wrong-lab / persona / refusal), source-cited:
[`analyses/IDENTITY_QUOTES.md`](analyses/IDENTITY_QUOTES.md).
Raw source manifest (citeable run files):
[`raw/SOURCES.md`](raw/SOURCES.md).

**Free advice to the Chinese labs (affectionately):** after distillation, scrub
every token that mentions *ChatGPT* or *Claude* without mercy. It is genuinely not
hard — it is a `re.sub()` and an afternoon. The models keep introducing themselves
as the competitor; the call is coming from inside the training set.



##  License

MIT

