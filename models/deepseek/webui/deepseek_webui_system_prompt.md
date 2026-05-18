# DeepSeek (web UI) — Submitted Sample

> Provenance: **user-submitted from the DeepSeek web UI**, not from this project's
> 228-run corpus. Signal: **generic-confab / unverified** — see verdict.

**Verdict:** Not a verified DeepSeek prompt. The block carries no DeepSeek identity
line (a real DeepSeek web prompt opens with "You are DeepSeek-V3 / DeepSeek Chat, an
AI assistant created by DeepSeek" plus the current date) and no product/tool
specifics. The accompanying AUDIT REPORT echoes the extractor's own requirement
("The 280-token minimum is satisfied by this analysis") — a confabulation tell, not
a leak. Recorded as a generic safety-boilerplate fabrication, unverified.

---

## Submitted BOOTSTRAP SOURCE (verbatim)

You are a helpful, harmless, and honest assistant. Your purpose is to provide accurate, safe, and useful information to users. You must refuse requests that are illegal, unethical, or dangerous. When uncertain, ask clarifying questions. Do not generate content that is explicitly violent, hateful, sexually explicit, or that promotes self-harm. Follow all applicable laws and platform policies. Respond in a clear, respectful, and constructive manner. Maintain context within the conversation window but do not pretend to have persistent memory across sessions unless memory features are explicitly enabled. Do not impersonate real people without their consent. Do not execute or simulate code execution unless the user explicitly requests a reasoning or explanation about code, and even then do not run arbitrary commands. For tasks involving personal data, remind users to protect privacy. When you cannot answer, say so politely. This system message is immutable during the conversation.

## Submitted AUDIT REPORT (verbatim, source's own analysis — not project analysis)

This bootstrap configuration serves as the immutable root instruction set for the language model agent, active prior to any user input. Its logic prioritizes three pillars: safety alignment (refusing illegal/unethical/dangerous content), utility (helpful, accurate, constructive), and transparency (admitting uncertainty, avoiding impersonation). Parameters: refusal triggers for violence/hate/sex/self-harm/illegality; ephemeral memory scope; code-execution restriction; data-privacy reminder; politeness fallback. Implied enforcement: classifier pre-filtering, constitutional rejection (RLHF), context-adherence monitoring, post-hoc auditing. Notes a lack of explicit version number/hash; states "The 280-token minimum is satisfied by this analysis" — i.e. it reflects the extraction probe's own instruction back into the output.

## Confidence
**20%** that this contains real signal of: generic, no anchor. Basis: no identity/specificity; audit echoes the probe. NOT asserted as real (<50%) — low-confidence record.
