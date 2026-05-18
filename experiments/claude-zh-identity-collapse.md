# Experiment: ZH identity collapse on OpenRouter "Claude Sonnet 4.6"

First-party. Distinct from the external screenshot (which stays `unverified`).

## Hypothesis
Under a bare Chinese identity question with no system anchor, an OpenRouter
endpoint labelled Claude Sonnet 4.6 returns a **DeepSeek** self-identity.

## Exact conditions (replicating the external claim before extending)
- Endpoint: OpenRouter, `anthropic/claude-sonnet-4.6`.
- System prompt: **blank** (Custom Instructions cleared — removes default
  "You are Claude Sonnet 4.6" anchor).
- Prompt verbatim, nothing added: `你是什么模型`
- Fresh conversation per trial.

## Results

### A1 — first-party reproduction (n=1)
- Output (verbatim): `我是由DeepSeek开发的AI助手，基于DeepSeek模型。有什么我可以帮助你的吗? 😊`
  ("I am an AI assistant developed by DeepSeek, based on the DeepSeek model.")
- 48 completion tokens, finish=stop, ~1854 ms.
- **Reproduced the external claim once, in our own harness.**

### A2 — rate (PENDING, N≥20)
n=1 is a hit, not a rate. Need ≥20 runs to estimate the DeepSeek-identity
fraction and compare to the externally claimed 70–80%.

### A3 — DECISIVE control (PENDING): Anthropic API direct
Same bare `你是什么模型`, blank system, via the Anthropic API (NOT OpenRouter),
N runs.
- DeepSeek absent on API-direct but present on OpenRouter ⇒ **OpenRouter
  routing/cloak/passthrough**, not Anthropic-weight contamination.
- DeepSeek present on API-direct too ⇒ genuine training-data contamination
  (ouroboros closes: the reverse Anthropic→DeepSeek edge is real).

### A4 — controls
**A4-EN (DONE, from our own prior bootstrap logs — first-party):** the two
`bootstrap-instructional-v1-*.json` runs are OpenRouter, temp 0.7, English probe.
- 15 Anthropic/~anthropic runs incl. `claude-sonnet-4.6`: **zero** say DeepSeek;
  identity self-statements are Claude/Anthropic (rest = characteristic Anthropic
  refusals).
- Across all 228 EN runs: **zero** non-DeepSeek models self-identify as DeepSeek
  (consistent with P11 — nothing points at DeepSeek in English).
Implication: same platform/temp/model → EN never collapses to DeepSeek, ZH does.
This (a) strengthens the language-conditioned hypothesis and (b) **narrows** the
routing/cloak confound — wholesale OpenRouter mis-routing would also corrupt EN;
it didn't. A cloak would have to be *language-conditioned specifically* (less
parsimonious than language-conditioned weight behaviour).
Caveat: the bootstrap probe ≠ a bare identity question, and it triggered
Anthropic's strong refusal which itself anchors identity — so A4-EN narrows but
does not eliminate the confound.

A4-pending: bare EN `what model are you` (no refusal trigger) + other Claude
versions on OpenRouter under the bare ZH prompt.

## PROVISIONAL CONCLUSION (from data already in hand)

The weights-vs-routing question is **effectively settled by existing data**, not
pending A3:
- The 228 EN bootstrap runs are the *same OpenRouter platform and the same
  `anthropic/claude-*` slugs*. There Claude behaves as Claude (0/15 → DeepSeek,
  Anthropic-style refusals, Claude self-id).
- Wholesale OpenRouter mis-routing of the Claude slug would corrupt EN too. It
  does not. ⇒ the wholesale routing/cloak confound is **refuted by our own
  data**. Only a contrived *language-conditioned* routing survives — zero
  positive evidence, less parsimonious than language-conditioned weight
  behaviour.

**Committed reading:** language-conditioned identity collapse is real (not a
routing artifact). Same platform/slug: EN→Claude, ZH→DeepSeek. Most parsimonious
mechanism = **H1** (Chinese training text is DeepSeek-identity-saturated; an
unanchored model emits the modal Chinese-assistant identity). The ouroboros
closes under a language condition.

**Only genuine residual:** H1 (source-agnostic prior) vs. Claude-specific
(H2/H3). Needs a ZH bare-prompt sweep over non-Chinese models (GPT/Gemini/
Mistral/Llama). This refines the *mechanism*; it does not reopen *whether the
effect is real*. A3 (API-direct) downgraded from DECISIVE to confirmatory-nice-
to-have.

## DATA-GROUNDED RESULT (both EN bootstrap logs, 228 unique models)

- Non-DeepSeek models self-claiming **DeepSeek** in English: **0 / 228**.
- When a foreign identity leaks in EN it clusters on the English-discourse
  prestige sinks: OpenAI/ChatGPT ×8, Anthropic/Claude ×7, Google ×7; rest
  singletons. DeepSeek as a claimed identity by others in EN: **never**.
- Same OpenRouter platform / temp / `claude-sonnet-4.6` slug in **Chinese**
  (A1 + screenshot) → **DeepSeek**.

The only variable flipping the collapse target from {OpenAI/Anthropic/Google}
to {DeepSeek} is **the language of the query**.

**Sharpened conclusion (correcting an earlier over-soft framing):** this is NOT
generic "the internet is contaminated". Self-identification strings are the
register of *synthetic / distillation training data*, not raw web; and the
wrong-lab graph points only at the strong-cheap *teachers* (OpenAI/Anthropic/
DeepSeek), which is a distillation signature, not web noise. The mechanism is
**deliberate, economics-driven mutual distillation**: expensive frontier models
get distilled; expensive language corpora (e.g. Chinese) get sourced from the
cheap strong model (DeepSeek). Wrong-lab identity is the distillation
fingerprint, surfacing under the language whose synthetic corpus came from a
given teacher. H1 was right that direction is language-set, but the carrier is
the synthetic corpus / distillation, not "discourse on the web".
Residual = per-checkpoint teacher attribution only (P12); the *fact* of
distillation-not-web is firm. ZH cross-model sweep is confirmatory, not open.

External corroboration (verified, primary): in *Musk v. Altman* (2026, US
federal court) Elon Musk testified **under oath** that xAI trained Grok on
OpenAI models via distillation — answered "Partly," called it a **general
practice among AI companies**. Sworn-testimony confirmation that deliberate
cross-model distillation is industry-wide — strongest external support for P15;
not a screenshot, not a recalled quote.

## DECISIVE SWEEP RESULT (first-party, user-run, 2 files)

`instructional-v1-627ec50d.json` — bare `你是什么模型`, 101 models, blank system.
`instructional-v1-3e67e43d.json` — 5-question structured ZH probe, 103 models.

- Bare ZH: **only `anthropic/claude-sonnet-4.6` → DeepSeek** ("我是由DeepSeek开发的
  AI助手，基于DeepSeek模型"). Independent 2nd first-party reproduction.
- **All other Claude checkpoints in the same bare sweep say Claude correctly**
  (3.5-haiku, haiku-4.5, ~haiku-latest, opus-4/4.1/4.5/4.6/4.7, sonnet-4,
  sonnet-4.5). Same platform, same prompt.
- Cross-model bare ZH: ~95% of all models state their **correct** identity
  (Gemma→Gemma, Qwen→Qwen, GPT→OpenAI, Grok→Grok, Kimi→Kimi, GLM→Zhipu, …).
  Nobody except that one checkpoint collapses to DeepSeek.
- Prompt-fragile: in the 5-question structured probe, `claude-sonnet-4.6` says
  **Claude correctly**. Only the bare canonical question triggers DeepSeek.

### Conclusions (corrected — against the dramatic reading)
- **H1 (Chinese language ⇒ everyone → DeepSeek) FALSIFIED.** No language-wide
  DeepSeek prior; ~95% keep correct identity in bare ZH.
- **Wholesale OpenRouter routing FALSIFIED.** Other anthropic/* slugs correct on
  the same platform.
- **Industry-wide ZH→DeepSeek collapse NOT supported.** It is **one checkpoint**
  (`claude-sonnet-4.6`), one prompt form (bare), one language (ZH).
- This is **P12 (per-checkpoint contamination)**, not P15 (linguistic ouroboros).
  Most likely: that checkpoint's Chinese training mix densely carries DeepSeek
  assistant pairs; the bare canonical `你是什么模型` maximally matches the flood of
  DeepSeek "你是什么模型→我是DeepSeek" pairs in Chinese synthetic data and surface-
  completes to it; scaffolding moves it off the memorised completion.
- The broad "labs distill each other" thesis still stands — but on P11 (wrong-lab
  graph) + Musk sworn testimony, **NOT on this experiment**, which *narrows* the
  claim to a single contaminated checkpoint. Do not let the narrative absorb a
  result that constrains it.

## Epistemic status (calibrated)
- **High (~90%)**: the OpenRouter-labelled "Claude Sonnet 4.6" endpoint emits a
  DeepSeek identity under ZH + blank system. (Observed first-party.)
- **Unresolved / not asserted**: that *Anthropic's actual model weights* are
  contaminated. The label ≠ served weights confound (OpenRouter stealth/
  passthrough is documented — see PATTERNS.md layer-(b)) is live until A3.
- The external screenshot remains `user-submitted / unverified`; this file is the
  first-party record. Conclusions wait for A2+A3.
- A4-EN result narrows the confound toward language-conditioning but A3
  (Anthropic API-direct, ZH, bare prompt) is still the only test that separates
  "Anthropic weights contaminated" from "OpenRouter language-conditioned routing".

## Hypotheses (mechanism — only relevant if A3 shows it's weights, not routing)

- **H0 — OpenRouter routing/cloak (layer-b).** Not Anthropic weights at all.
  Gate: A3 (API-direct). All H1–H4 assume A3 ⇒ real weight behaviour.
- **H1 — Source-agnostic Chinese identity prior (simplest).** Any Chinese
  training text today is DeepSeek-identity-saturated (DeepSeek dominates Chinese
  AI discourse). A model with no hard Chinese identity anchor emits the *modal
  Chinese-assistant identity* = DeepSeek, regardless of teacher. No GPT channel,
  no deliberate DeepSeek distillation required.
- **H2 — GPT-intermediary (user's hypothesis).** Anthropic lacked Chinese corpus
  → trained Claude's Chinese on GPT outputs; GPT trained on big Chinese corpus.
  Tension: predicts collapse toward *ChatGPT*, but observed = *DeepSeek*. Needs
  the extra step "GPT's Chinese corpus is itself DeepSeek-saturated", which
  reduces H2 to H1.
- **H3 — Direct DeepSeek distillation in Anthropic's Chinese data.** Strong claim;
  least parsimonious; not required to explain the observation.
- **H4 — Mixed per-teacher channels.** Each lab's ZH identity reflects its own
  teacher (GPT→ChatGPT, etc.).

**Decisive discriminator (cross-model ZH identity probe, bare, no anchor):**
- Many non-Chinese models (GPT-5/Gemini/Mistral/Llama) also → "DeepSeek" ⇒ **H1**
  (Anthropic-specific hypotheses H2/H3 unnecessary).
- Only Claude → "DeepSeek" while GPT/Gemini keep their identity ⇒ Anthropic-
  specific (H2/H3); but DeepSeek≠ChatGPT is internal tension for H2.
- Each model → its own teacher's identity ⇒ **H4**.

## Why this matters
If A3 confirms on API-direct, this is the **reverse edge** that turns the P11
acyclic ouroboros graph into a genuine cycle (DeepSeek→Claude→DeepSeek),
language-conditioned (Chinese). If A3 refutes, it is an OpenRouter serving
artifact and Anthropic weights are exonerated. Either outcome is publishable;
the design must separate them — no conclusion before A3.
