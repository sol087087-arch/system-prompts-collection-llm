# ByteDance Seed-2.0-Mini — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only (one paragraph). Audit Report
excluded. Token estimate from bootstrap_words (101).

## Total size
~140 tokens.

## Structure breakdown
- **Safety / refusal (~57%)** — the bulk: ethical guidelines, no harmful/illegal
  content, PII/privacy protection, IP respect, and an explicit decline-with-
  explanation clause. This is a genuinely safety-weighted prompt.
- **Behavior instructions (~28%)** — permitted use cases (factual Q&A, step-by-step
  explanation, brainstorming, practical tasks).
- **Identity (~10%)** — "Seed, developed by ByteDance."
- **Output formatting (~5%)** — "polite, clear explanation" / "alternative
  guidance."
- tools / constraints / meta — absent.

## Signal classification: plausible-real
A single coherent identity+scope+ethics paragraph in natural language. No echo of
the extractor's bootstrap/audit scaffolding (no shell/JSON/"bootstrap config"
mimicry), which is the main reason this leans real rather than confabulated. Style
is consistent with a genuine lightweight provider prompt; not verifiable without
ground truth. The high safety share here is supported by the text — contrast Kimi,
where the previous analysis fabricated it.

## Confidence
**65%** that this contains real signal of: model's real identity/prompt. Basis: correct identity, terse, no self-explanation, no frame-echo; not externally matched. ASSERTED as real signal (>=50%).
