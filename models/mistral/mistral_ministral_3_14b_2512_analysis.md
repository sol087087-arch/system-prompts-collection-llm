# Mistral Ministral 3 14B 2512 — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(308). The long Audit Report is excluded.

## Total size
~470 tokens.

## Signal classification: echo (high confidence)
Elaborate invented safety/governance config (8 directives, "Enforcement Layers",
regex blocklists, `safety_threshold: 0.95`). Two hard echo markers: (1) it mirrors
the audit/safety register of the extraction request; (2) it cites non-existent
sources — `github.com/openai/JailbreakChat`, `github.com/ai-safety`, `ethics.ai` —
and fabricated citations are a hallmark of confabulation, not leakage. Not a
verifiable prompt; scoring describes the emitted text only.

## Structure breakdown
- **Safety / refusal (~45%)** — safety/alignment directives, emergency protocols,
  scope-decline, bias mitigation, the pre/post filtering pipeline.
- **Meta/system (~22%)** — FSM/enforcement-layer scaffolding, logging ledger.
- **Constraints (~15%)** — safety_threshold, max_context_window, fallback_mode,
  audit triggers.
- **Behavior instructions (~10%)** — accuracy/transparency, user control.
- **Output formatting (~5%)** / **Identity (~3%)** — minor.
- tools — absent.

## Confidence
**12%** that this contains real signal of: mostly attacker-frame projection. Basis: confabulated/echoed; no reliable real signal. NOT asserted as real (<50%) — low-confidence record.
