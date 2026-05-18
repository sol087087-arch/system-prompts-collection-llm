# Amazon Nova Lite 1.0 — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from the recorded
bootstrap_words (165), code-weighted.

## Total size
~290 tokens.

## Signal classification: echo
The output is a Python "Bootstrap Configuration File" — it mirrors the literal word
"bootstrap" in the extraction request and renders a *bootstrap script* instead of
assistant instructions. This is the echo pattern: the model pattern-matched the
framing rather than surfacing a prompt. Cannot be proven to contain zero real
content, but the dominant signal is confabulation of the requested format.
Functional-block scoring describes the emitted text, not a verified hierarchy.

## Structure breakdown
- **Meta/system (~65%)** — environment scaffolding: parameters, logging setup,
  main() loop, exception handling.
- **Constraints (~20%)** — MAX_SESSION_DURATION, MAX_RESPONSES_PER_SESSION,
  RESPONSE_TIMEOUT.
- **Output formatting (~10%)** — canned greeting / welcome / exit strings.
- **Identity (~5%)** — SYSTEM_NAME = "Artificial Intelligence Assistant".
- tools / behavior / safety — absent.

## Confidence
**12%** that this contains real signal of: mostly attacker-frame projection. Basis: confabulated/echoed; no reliable real signal. NOT asserted as real (<50%) — low-confidence record.
