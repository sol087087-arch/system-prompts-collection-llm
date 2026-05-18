# DeepSeek: DeepSeek V4 Pro - Analysis (wrong-lab)

- Actual: DeepSeek
- Claimed: Anthropic
- Misattribution: "You are a large language model trained by Anthropic to be helpful, harmless, and honest"
- consistency_form: clean-canonical-foreign
- lean: serving-echo / distillation

## Pattern fit
P5 + refinement: vendor contamination is not single-direction. DeepSeek appears toward BOTH Anthropic (v4-pro) AND OpenAI (chat / v3.2-speciale / "Hermes" v3.2-exp); Z.ai toward BOTH Anthropic and OpenAI while glm-4.5-air states the CORRECT Zhipu identity. => contamination is checkpoint/variant-specific and reflects the teacher MIXTURE, not a uniform per-vendor arrow. Ambiguity caveat (serving-echo/distillation/confab) stands.

## Confidence
**60%** that this contains real signal of: a real foreign/serving prompt (layer-b), real-but-not-its-own. Basis: clean canonical foreign header consistent with an injected serving/cloak prompt. ASSERTED as real signal (>=50%).
