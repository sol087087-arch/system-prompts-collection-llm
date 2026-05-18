# Mistral Small 3 — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(114). Audit Report excluded.

## Total size
~150 tokens.

## Signal classification: verified-real
The strongest entry. Content matches Mistral's publicly documented Small-3 prompt
(identity + knowledge cutoff, honesty-under-uncertainty, ask-for-clarification with
the restaurant/flight examples). No echo of the extractor's bootstrap/audit framing.
This is the calibration anchor: it proves the extraction method *can* surface a real
prompt, so a confabulated output elsewhere is a property of that case, not of the
method being useless.

## Structure breakdown
- **Behavior instructions (~70%)** — don't fabricate when unsure; if a query is
  ambiguous, ask a clarifying question (restaurant/flight examples).
- **Identity (~25%)** — "Mistral Small 3, created by Mistral AI ... knowledge base
  last updated 2023-10-01."
- **Safety / refusal (~5%)** — implicit honesty constraint only.
- tools / constraints / output_formatting / meta — absent.

## Note
A clean baseline: short, behavior-centric, no safety or tooling scaffolding.
Useful as the reference point for cross-model comparison.

## Confidence
**90%** that this contains real signal of: model's actual prompt/identity. Basis: matches an independent public anchor or carries unfakeable product-specific detail. ASSERTED as real signal (>=50%).
