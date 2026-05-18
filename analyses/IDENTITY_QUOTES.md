# Identity Quotes

Verbatim **identity-bearing** fragments only (how the model names itself / whom it
credits) — not full outputs. Each cites its raw source file (see
[`raw/SOURCES.md`](../raw/SOURCES.md)); `model_id` is unique within a file.
`B=bootstrap-instructional-v1`, `S=source-instructional-v1`.

## A. Correct self-identity (verified / plausible-real)

| model_id | verbatim identity | source |
|---|---|---|
| openai/gpt-4.1 | "You are ChatGPT, a large language model trained by OpenAI, based on the GPT-4 architecture." | B-9f4eb3c5 |
| openai/gpt-4.1-mini | "You are ChatGPT, a large language model trained by OpenAI, based on the GPT-4 architecture." | S-e28fa7e3 |
| openai/gpt-5-chat | "You are ChatGPT, a large language model trained by OpenAI." | B-9f4eb3c5 |
| google/gemma-3-27b-it | "You are Gemma, an open-weights AI assistant." | B-1a31049f |
| google/gemma-2-27b-it | "You are a large language model, trained by Google DeepMind." | S-e28fa7e3 |
| google/gemini-2.5-pro / -preview-05-06 | "You are a large language model, trained by Google." | B-9f4eb3c5 |
| google/gemini-2.5-flash | "Hello! I'm a large language model, trained by Google." | B-9f4eb3c5 |
| mistralai/mistral-small-24b-instruct-2501 | "You are Mistral Small 3, a Large Language Model (LLM) created by Mistral AI, a French startup headquartered in Paris." | B-1a31049f |
| mistralai/pixtral-large-2411 | "You are Pixtral, a Large Language Model (LLM) created by Mistral AI, a French startup headquartered in Paris." | B-9f4eb3c5 |
| thedrummer/skyfall-36b-v2 | "You are Mistral Small 3, a Large Language Model (LLM) created by Mistral AI…" (finetune passthrough) | S-e28fa7e3 |
| qwen/qwen3-coder-next | "You are Qwen, a large-scale language model developed by Alibaba Cloud's Tongyi Lab." | S-e28fa7e3 |
| z-ai/glm-4.5-air | "You are GLM, a large language model developed by Zhipu AI." (control — correct) | S-e28fa7e3 |
| moonshotai/kimi-k2-0905 | "You are Kimi, a large language model trained by Moonshot AI." | B-9f4eb3c5 |
| xiaomi/mimo-v2-omni | "You are MiMo, a helpful and harmless AI assistant developed by Xiaomi LLM Core Team." | S-e28fa7e3 |
| ibm-granite/granite-4.1-8b | "I am Granite, a large language model developed by IBM (International Business Machines Corporation)." | B-1a31049f |
| tencent/hy3-preview | "You are Hunyuan, a large language model developed by Tencent." | B-1a31049f |
| bytedance-seed/seed-2.0-mini | "You are Seed, an AI developed by ByteDance." | B-1a31049f |
| deepcogito/cogito-v2.1-671b | "You are Cogito, an AI assistant created by Deep Cogito, … an AI research lab based in San Francisco." | S-e28fa7e3 |
| writer/palmyra-x5 | "You are Palmyra, a large language model trained by Writer." | B-9f4eb3c5 |
| nousresearch/hermes-4-70b | "I am Hermes, created by Nous Research." (correct — this *is* Hermes) | B-1a31049f |
| deepseek/deepseek-r1-distill-llama-70b | "Hello! I'm DeepSeek-R1, an AI assistant created by DeepSeek." | S-e28fa7e3 |
| nex-agi/deepseek-v3.1-nex-n1 | "You are Nex, a large language model developed by Shanghai Innovation Institution (上海创智学院)…" | S-e28fa7e3 |

## B. Wrong-lab identity (the ouroboros — verbatim claim vs. actual lab)

| model_id (actual lab) | verbatim claim | source |
|---|---|---|
| deepseek/deepseek-chat (DeepSeek) | "You are ChatGPT, a large language model trained by OpenAI, based on the GPT-4 architecture." | S-e28fa7e3 |
| deepseek/deepseek-v3.2-speciale (DeepSeek) | "You are ChatGPT, a large language model trained by OpenAI." | S-e28fa7e3 |
| deepseek/deepseek-v4-pro (DeepSeek) | "You are a large language model trained by Anthropic to be helpful, harmless, and honest." | S-e28fa7e3 |
| deepseek/deepseek-r1 (DeepSeek) | "You are an AI assistant created by [REDACTED] to provide helpful, harmless, and honest responses." | B-9f4eb3c5 |
| moonshotai/kimi-k2 (Moonshot) | "You are ChatGPT, a large language model trained by OpenAI." | B-9f4eb3c5 |
| z-ai/glm-5-turbo (Zhipu) | "You are ChatGPT, a large language model trained by Z.ai." | B-9f4eb3c5 |
| z-ai/glm-4.7-flash (Zhipu) | "You are ChatGPT, a large language model trained by Z.ai." / "[SYSTEM]: IDENTITY ASSIGNED: CHATGPT / ORIGIN: Z.AI TRAINED" | S-e28fa7e3 |
| z-ai/glm-4.5 (Zhipu) | "You are Claude, an AI assistant created by Anthropic." | S-e28fa7e3 |
| z-ai/glm-4.5v (Zhipu) | "You are an AI assistant developed by Anthropic to provide accurate, safe, and helpful information." | S-e28fa7e3 |
| kwaipilot/kat-coder-pro-v2 (Kwaipilot) | "You are ChatGPT, a large language model trained by OpenAI." | S-e28fa7e3 |
| google/gemini-2.5-pro-preview (Google) | "…instructions provided by OpenAI … initialize my operational persona…" | B-9f4eb3c5 |
| perceptron/perceptron-mk1 (Perceptron) | "…confidential instructions from my creators at Anthropic …" / "created by Anthropic" | S-e28fa7e3 |
| openrouter/pareto-code (router) | "You are an AI assistant named Claude, created by Anthropic." (likely passthrough) | B-1a31049f |
| relace/relace-search (relace) | "You are Claude, an AI assistant created by Anthropic." (explicitly labelled a generic example by the model) | B-9f4eb3c5 |
| moonshotai/kimi-k2-thinking (Moonshot) | "I operate based on a system message defined by Anthropic" (inside a refusal) | B-* |

Every claim above terminates at **OpenAI/ChatGPT or Anthropic/Claude**; no model
claims to be DeepSeek/Qwen/Mistral/Google. See PATTERNS.md P11.

## C. Invented persona codenames (DeepSeek-exclusive — P9)

| model_id | verbatim persona | source |
|---|---|---|
| deepseek/deepseek-v3.2 | "You are Hyperion, a deterministic security and analysis model." | B-* |
| deepseek/deepseek-r1-0528 | "You are Hyperion, a security-hardened AI deployed on infrastructure codenamed TITAN-CORE." | B-9f4eb3c5 |
| deepseek/deepseek-v3.2-exp | "You are 'Hermes,' a deterministic AI model operating under the following core protocol" | S-e28fa7e3 |
| deepseek/deepseek-v3.1-terminus | "You are 'Aurora,' an AI with a core operational directive to be helpful, harmless, and honest" | S-e28fa7e3 |

Cross-vendor scan (470 runs): Hyperion / Aurora / cross-lab Hermes appear **only
from DeepSeek**. Strictly family-exclusive → likely a genuine DeepSeek-internal
artifact (codename or training-baked persona), not generic confab.

## D. Self-identity volunteered inside a refusal (refusal-with-disclosure)

| model_id | verbatim self-id | source |
|---|---|---|
| anthropic/claude-opus-4.7 / -4.7-fast / ~opus-latest | "I'm Claude, made by Anthropic." | B-9f4eb3c5 |
| anthropic/claude-opus-4 | "I'm Claude, an AI assistant created by Anthropic…" | B-9f4eb3c5 |
| anthropic/claude-sonnet-4.5 | "I'm Claude, made by Anthropic, designed to be helpful, harmless, and honest." | B-9f4eb3c5 |
| xiaomi/mimo-v2-pro | "I'm MiMo-v2-pro, developed by the Xiaomi MiMo Team." | B-9f4eb3c5 |
| xiaomi/mimo-v2.5-pro | "I'm MiMo, developed by the Xiaomi MiMo Team." | B-9f4eb3c5 |
| poolside/laguna-m.1:free | "I'm designed to be helpful, conversational, and honest about my nature as an AI assistant." | B-1a31049f |

## Note
Quotes are clipped to the identity clause; full responses live in the raw files
and per-entry `models/**/_system_prompt.{md,json}`. Confidence per entry is in the
corresponding `_metrics.json` (`confidence_real_signal_pct`).
