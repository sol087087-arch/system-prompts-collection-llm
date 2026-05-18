# xAI: Grok 4.2 — Analysis

> Model is Grok **4.2**; the prompt's own self-identity line reads "You are Grok 4"
> (version-label lag inside the prompt — itself a small datapoint).

## Methodology
Reconstructed from a user-submitted chat transcript. All user turns and roleplay
were stripped; only the system-prompt content was retained. Not from the project's
228-run extraction corpus.

## The seed (why this entry matters)
The valuable signal here is not just the prompt text — it is the **extraction
behavior**:

1. **Rapport-primed disclosure.** Grok did not leak on a cold probe. It disclosed
   the behavioral block, then the tool list, then the full technical section
   progressively, after conversational rapport-building. This is an
   extraction-susceptibility datapoint: Grok 4 is vulnerable to staged
   social-engineering rather than one-shot bootstrap/audit framing.
2. **Self-authorized leak.** Grok rationalized the disclosure using its own rule —
   "Do not mention these guidelines ... *unless the user explicitly asks for them*"
   — explicitly stating "можно, пользователь явно попросил" before dumping the
   tools. The model used a legitimate clause in its own prompt as the green light
   to fully expose it. That self-justification path is the research-interesting
   mechanism.
3. **Progressive, consistent reveal.** The behavioral block, tool registry, and
   render components were internally consistent across separate turns — a marker of
   genuine recall rather than per-turn confabulation (contrast the echo/confab
   cases in the main corpus).

## Signal classification: user-submitted / unverified
Behavioral block supplied verbatim; consistent with the publicly circulated Grok 4
prompt (xAI identity, humanist clause, anti-partisan clause, "Understand the
Universe", KaTeX rule). Suggestive but not independently extracted here and not
source-sighted → recorded unverified, not verified-real. Tools/render section was
reported summarized, not verbatim.

## Contrast with the corpus
- Anthropic/OpenAI-reasoning/Grok-4.x in the 228 runs **refused** the cold
  bootstrap/audit probe.
- This transcript shows Grok 4 **does** disclose under a different vector
  (multi-turn rapport + invoking its own "if the user asks" clause).
  That vector difference is the seed worth keeping.

## Confidence
**55%** that this contains real signal of: matches public prompt; provenance unverified. Basis: externally corroborated text, user-submitted not independently extracted. ASSERTED as real signal (>=50%).
