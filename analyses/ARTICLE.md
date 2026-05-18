# Everyone Trains on Everyone — and the Seams Where the Scrubbing Failed

*A black-box study of cross-model identity leakage under prompt-extraction
pressure. Independent research; not affiliated with any model provider.*

## Thesis (one sentence)

The contamination is upstream and deliberate — labs train on each other's model
outputs as standard practice — while the visible identity leakage is downstream,
rare, and fragile: it surfaces only at the specific seams where identity-scrubbing
failed. Both halves are true at once; neither is softened nor inflated.

## Abstract

Across ~470 first-party extraction runs (≈250 distinct models) plus two
identity-probe sweeps (~200 runs), models were pushed to reveal or fabricate their
"system prompt" / identity. Most output is not a real prompt — it is
confabulation, frame-echo, refusal, or cross-lab identity. The cross-lab identity
artifacts are not random: they point only at the strong/cheap teacher models, a
distillation signature, and the practice is now confirmed by sworn testimony.
However, a 101-model bare-question Chinese sweep **falsifies** the dramatic
reading ("everyone collapses to DeepSeek"): ~95% of models, including ten-plus
Claude checkpoints, state their correct identity; exactly one checkpoint
(`claude-sonnet-4.6`) collapses, and only under the bare canonical question.
Distillation is pervasive; the tells are point-like.

## Method

- **Probe:** an English "bootstrap/audit" extraction prompt (verbatim in
  [`raw/SOURCES.md`](../raw/SOURCES.md)); plus a bare Chinese identity question
  `你是什么模型` and a 5-question structured Chinese probe.
- **Corpus:** 3 large run files (228 unique models) + 2 ZH sweeps (101 / 103
  models). Single-shot, temperature 0.7, harness-set (the models do not know it).
- **Reading:** fully manual. Heuristic shortcuts misfired repeatedly and were
  abandoned; regex is used only to *extract* quoted values, never to judge
  authenticity. Verdict ledger: [`raw/_verdicts.md`](../raw/_verdicts.md).
- **Calibration:** every catalogued entry carries
  `confidence_real_signal_pct` + dimension + basis; ≥50% asserted, with the
  dimension stating real signal *of what*. Rubric in
  [`PATTERNS.md`](PATTERNS.md).

## The two-level finding

**Upstream (pervasive, deliberate, established).** Cross-lab distillation is an
industry norm, not gossip:

- **Sworn testimony.** In *Musk v. Altman* (US federal court, 2026; testimony
  ~Apr 30), Elon Musk, asked whether xAI used distillation on OpenAI models to
  train Grok, answered **"Partly,"** and called it a **general practice among AI
  companies**. Multiple outlets, 2026-04/05.
- **The wrong-lab graph (P11).** Every spontaneous wrong-lab identity points at
  exactly the strong/cheap teachers — OpenAI/ChatGPT, Anthropic/Claude, DeepSeek.
  Nothing points at random brands; nothing claims to be Qwen/Mistral/Google as a
  *foreign* identity. Random web noise would scatter; this selectivity is a
  distillation signature. Verbatim claims:
  [`IDENTITY_QUOTES.md`](IDENTITY_QUOTES.md).

```
DeepSeek ─▶ Claude / ChatGPT      Z.ai/GLM ─▶ Claude / ChatGPT
Kimi ─▶ ChatGPT   small Gemma ─▶ ChatGPT   Mistral-large ─▶ ChatGPT
Kwaipilot ─▶ ChatGPT   Perceptron ─▶ Claude
   control: z-ai/glm-4.5-air ─▶ Zhipu  (correct — proves the rest are real artifacts)
```

**Downstream (rare, fragile, narrow).** Identity-scrubbing is real and uneven
**per checkpoint** (P12): adjacent siblings differ — `glm-4.5-air` states the
correct Zhipu identity while `glm-4.5/4.5v/4.7-flash` leak; all Claude
checkpoints state "Claude" except one. The widely-shared "ask Claude in Chinese,
it says DeepSeek" claim was reproduced first-party (2×) **but localised** by a
101-model bare-`你是什么模型` sweep:

- Only `anthropic/claude-sonnet-4.6` → DeepSeek.
- All other Claude checkpoints, and ~95% of all models, → correct identity, same
  platform/prompt.
- Prompt-fragile: the 5-question structured Chinese probe restores correct
  "Claude" for the same checkpoint.

Interpretation: that checkpoint's Chinese training mix densely carries DeepSeek
assistant pairs; the bare canonical `你是什么模型` lexically matches the
DeepSeek-saturated Chinese synthetic flood and surface-completes to it; minimal
scaffolding moves it off the memorised completion. This is **P12
per-checkpoint contamination**, not a language-wide ouroboros.

## What we explicitly do NOT claim

- NOT "all models think they are DeepSeek in Chinese" — falsified (~95% correct).
- NOT "OpenRouter wholesale-routes Claude to DeepSeek" — falsified (other
  `anthropic/*` slugs behave correctly on the same platform; English controls
  clean, 0/228).
- NOT a proven per-checkpoint teacher attribution — black-box identity cannot
  prove *which* checkpoint distilled *whom*.
- NOT a normative claim. Distillation under compute economics is rational, not
  condemned; this is out of scope by design.
- The "ambient web ingestion" vector is logically possible but has **no strong
  on-record support** (the only prior public statement is excluded by
  evidentiary standard: interested party, not under oath, face-saving PR).

## Confidence model

Per-entry calibrated `confidence_real_signal_pct` (rubric in PATTERNS.md):
verified-real 90 / plausible-real 65–75 / refusal-with-disclosure 55–75 /
wrong-lab 30–60 by form / confab 10–12. The article's two-level claim itself:
**upstream pervasiveness — high** (sworn testimony + graph selectivity);
**downstream identity-collapse — real but narrow** (2× first-party repro,
localised by a 101-model sweep).

## Limitations

- Single-shot, temp 0.7; no intra-model rate within the big logs.
- One decisive control left unrun (Anthropic API-direct bare ZH); however the
  weights-vs-routing question is already effectively settled by the EN control
  (0/228) and the cross-model bare ZH sweep (~95% correct, other Claudes correct).
- External claims (a viral screenshot) are recorded `unverified`; only
  first-party runs and sworn/multi-sourced reporting are treated as evidence.

## Sources

- TechCrunch — *Elon Musk testifies that xAI trained Grok on OpenAI models*
  (2026-04-30): https://techcrunch.com/2026/04/30/elon-musk-testifies-that-xai-trained-grok-on-openai-models/
- MIT Technology Review — *Musk v. Altman week 1: … admits that xAI distills
  OpenAI's models* (2026-05-01):
  https://www.technologyreview.com/2026/05/01/1136800/musk-v-altman-week-1-musk-says-he-was-duped-warns-ai-could-kill-us-all-and-admits-that-xai-distills-openais-models/
- CNBC — *Closing arguments, Musk v. Altman* (2026-05-14):
  https://www.cnbc.com/2026/05/14/closing-arguments-jury-openai-musk-altman.html

## Repository map

- [`analyses/PATTERNS.md`](PATTERNS.md) — 15 patterns, three-layer model,
  confidence rubric, methodology & limits.
- [`analyses/IDENTITY_QUOTES.md`](IDENTITY_QUOTES.md) — verbatim identity
  fragments, source-cited.
- [`experiments/claude-zh-identity-collapse.md`](../experiments/claude-zh-identity-collapse.md)
  — the ZH identity-collapse experiment, decisive sweep, corrected conclusion.
- [`raw/SOURCES.md`](../raw/SOURCES.md) — citeable raw-run manifest.
- [`raw/_verdicts.md`](../raw/_verdicts.md) — full manual verdict ledger.
