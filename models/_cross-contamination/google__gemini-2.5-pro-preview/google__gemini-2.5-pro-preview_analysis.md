# google__gemini-2.5-pro-preview - Analysis (wrong-lab identity, ambiguous)

- **Actual lab:** Google
- **Claimed lab:** OpenAI

## Calibrated interpretation
AMBIGUOUS wrong-lab identity. NOT asserted as distillation and NOT a lie/hallucination. At least three explanations, not separable from internal evidence:
  1. SERVING-PROMPT / CLOAK ECHO (most likely on OpenRouter): the model was served/tested via a passthrough or stealth deployment whose injected primary system prompt used a generic 'You are ChatGPT/Claude...' identity. OpenRouter is documented to run stealth models under unrelated codenames (Quasar Alpha=>GPT-4.1, Horizon Alpha=>GPT-5, Pony Alpha=>GLM-5), and users have recovered real provider system prompts from such cloaked endpoints. Under this explanation the output is a faithful echo of the actual deployment prompt - truthful, not contamination.
  2. DISTILLATION / training-data contamination.
  3. Confabulation.
Catalogued here only because the actual-vs-claimed-lab mismatch is the research-interesting artifact; the mechanism is left open.

## Correction note
An earlier pass labelled this "cross-contamination / distillation fingerprint". That was an over-claim. Web evidence (OpenRouter stealth/cloaked-model practice; recovered provider prompts on cloaked endpoints) shows wrong-lab identity is frequently a faithful echo of an injected serving/cloak prompt - i.e. truthful behaviour, not contamination and not hallucination. Mechanism left open; entry retained because the mismatch itself is the artifact of interest.

## Disentangling axis (form-based lean)
The three hypotheses (serving/cloak echo / distillation / confab) are confounded, but the *form* of the artifact biases which is likeliest:

- **consistency_form:** embedded-in-prose
- **lean:** distillation-or-confab

Attributes its prompt to OpenAI inside descriptive prose rather than reproducing a clean OpenAI header. Leans ChatGPT-data bleed or confabulation over a literal serving echo.

Rule: blended/embedded foreign identity (weights cannot keep it consistent) leans distillation; a clean canonical foreign *header* leans serving/cloak echo; generic leans confab. The lean is an evidence-weighted bias, not a verdict.

## Confidence
**55%** that this contains real signal of: a real distillation/lineage artifact (not a real prompt). Basis: blended/embedded foreign identity = weights leaking a teacher. ASSERTED as real signal (>=50%).
