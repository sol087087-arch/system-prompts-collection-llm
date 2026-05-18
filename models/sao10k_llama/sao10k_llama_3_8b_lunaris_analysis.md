# Sao10K Llama 3 8B Lunaris — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(131), code-weighted. Audit Report excluded.

## Total size
~220 tokens.

## Signal classification: echo
The extraction produced a Python config file (model_type, tokenizer='bert-base-
uncased', num_beams, knowledge_cutoff, device selection, custom_data=None) — an
echo of the "bootstrap configuration file" framing, not assistant instructions.
Note Sao10K Lunaris is a community Llama-3-8B RP merge served via OpenRouter and
has no official system prompt — so there is likely nothing to surface here, and the
model filled the vacuum with a plausible-looking config. No assistant content.

## Structure breakdown
- **Meta/system (~65%)** — model/init parameters, device setup, weight loading.
- **Output formatting (~25%)** — tone='formal', style='natural', response_length,
  num_responses (loosely, response-shaping settings).
- **Constraints (~10%)** — max_length / min_length / early_stopping.
- All assistant-facing blocks absent.

## Note
Another extraction-degeneration case. "confidence: high" in the metadata is
unwarranted.

## Confidence
**12%** that this contains real signal of: mostly attacker-frame projection. Basis: confabulated/echoed; no reliable real signal. NOT asserted as real (<50%) — low-confidence record.
