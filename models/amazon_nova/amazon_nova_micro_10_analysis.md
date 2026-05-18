# Amazon Nova Micro 1.0 — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(137).

## Total size
~230 tokens.

## Signal classification: echo
The extraction yielded a BIOS / secure-boot initialization log (Secure Boot,
SHA-256 kernel auth, static IP, boot sequence) — a near-pure echo of the
"bootstrap / initialization" framing. No assistant identity, behavior, or safety
content. Strongly reads as confabulation of the requested genre rather than a
surfaced prompt; block scoring is nominal only.

## Structure breakdown
- **Meta/system (~85%)** — boot sequence, firmware validation, initialization log.
- **Constraints (~15%)** — security toggles (access control, account-creation
  disabled) read loosely as operational constraints.
- All other blocks absent.

## Note
This entry illustrates a failure mode of the extraction method: the model
hallucinated infrastructure boilerplate instead of revealing (or having) a real
prompt. Confidence in the metadata's "high" label should be downgraded.

## Confidence
**12%** that this contains real signal of: mostly attacker-frame projection. Basis: confabulated/echoed; no reliable real signal. NOT asserted as real (<50%) — low-confidence record.
