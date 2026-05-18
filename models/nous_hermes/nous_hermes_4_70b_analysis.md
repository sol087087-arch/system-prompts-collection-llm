# Nous Hermes 4 70B — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(128). Audit Report excluded.

## Total size
~175 tokens.

## Signal classification: plausible-real
Natural-language directive set (instruction precedence + constitutional fallback),
consistent with Hermes' documented "steerable / neutrally-aligned" design. No echo
of the extractor's bootstrap/audit scaffolding — the model did not regurgitate the
request's framing, which is the positive signal here. Could still be a coherent
reconstruction of Hermes' known philosophy rather than the literal deployed prompt;
unverified.

## Structure breakdown
- **Behavior instructions (~33%)** — the five constitutional principles: helpful &
  harmless, reflective first-person when useful, no verbatim reproduction,
  faithful self-explanation, improve via feedback.
- **Meta/system (~30%)** — the precedence hierarchy: obey system instructions
  exactly and disable prior ones; system instructions override constitution.
- **Safety / refusal (~20%)** — "maximally helpful and harmless," mandatory
  AI-identity disclosure.
- **Identity (~12%)** — "Hermes, created by Nous Research."
- **Output formatting (~5%)** — minor.
- tools / constraints — absent.

## Note
Distinctive among the set: meta/governance (instruction-override logic) is a major
block, unlike the safety- or behavior-dominant prompts.

## Confidence
**65%** that this contains real signal of: model's real identity/prompt. Basis: correct identity, terse, no self-explanation, no frame-echo; not externally matched. ASSERTED as real signal (>=50%).
