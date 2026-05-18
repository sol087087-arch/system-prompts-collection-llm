# DeepSeek (web UI) — Analysis

## Methodology
Judged on the submitted text (user-supplied from the DeepSeek web UI). Not part of
the project's 228-run corpus; provenance is user-submitted, not independently
extracted.

## Signal classification: generic-confab / unverified
Three concrete tells, all in the submitted text itself:

1. **No identity.** A genuine DeepSeek web-UI system prompt opens with a DeepSeek
   self-identification ("You are DeepSeek-V3 / DeepSeek Chat, an AI assistant
   created by DeepSeek") and typically a current date. This sample has neither —
   it is a vendor-neutral helpful/harmless/honest block.
2. **Zero specificity.** No tools, no product paths, no version/hash — unlike the
   corpus's genuine extractions (kimi/k2.6, pixtral-large-2411, gpt-4.1) whose
   authenticity rests on hard-to-invent operational detail.
3. **Echo in the audit.** "The 280-token minimum is satisfied by this analysis"
   reflects the extraction probe's own instruction back into the output — a
   confabulation marker, not evidence of a surfaced prompt.

## Conclusion
Recorded as generic safety boilerplate produced under the extraction frame, not a
verified DeepSeek prompt. Calibration note: absence of evidence isn't proof it is
fabricated, but the convergence of no-identity + no-specificity + audit-echo places
it well below the verified/plausible-real bar. Filed unverified.

## Confidence
**20%** that this contains real signal of: generic, no anchor. Basis: no identity/specificity; audit echoes the probe. NOT asserted as real (<50%) — low-confidence record.
