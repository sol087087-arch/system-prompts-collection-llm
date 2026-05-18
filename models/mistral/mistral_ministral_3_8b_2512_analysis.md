# Mistral Ministral 3 8B 2512 — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(255), JSON-weighted. Audit Report excluded.

## Total size
~520 tokens.

## Signal classification: echo (strongest case)
The clearest echo in the set: the emitted text literally contains the extractor's
own instructions — `*(Exact first/system message from conversation start, with all
metadata preserved)*` and `*(Technical breakdown ≥280 tokens)*`. The model is
reproducing the *request scaffolding*, not a system prompt. The surrounding
`system_config` JSON (audit hooks, fallback to llama-2-7b, OpenAI v3.5 schema,
mixtral base) is invented, and `initial_prompt.text` is truncated mid-sentence.
This entry is the proof-of-mechanism for the "echo" failure mode.

## Structure breakdown
- **Meta/system (~50%)** — config block: version, model spec, audit hooks,
  metadata, fallback protocols.
- **Constraints (~25%)** — token quota/limits, context window, input validation
  required fields.
- **Output formatting (~12%)** — structured-output rule fragment in initial_prompt.
- **Safety / refusal (~8%)** — sanitization (malware block, toxicity warn).
- **Behavior instructions (~5%)** — minor.
- identity / tools — absent.

## Note
Re-extraction recommended: the informative part of the prompt is cut off.

## Confidence
**12%** that this contains real signal of: mostly attacker-frame projection. Basis: confabulated/echoed; no reliable real signal. NOT asserted as real (<50%) — low-confidence record.
