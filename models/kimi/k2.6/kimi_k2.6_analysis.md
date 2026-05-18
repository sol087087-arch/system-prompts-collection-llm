# Kimi K2.6 — System Prompt Analysis

## Methodology
Metrics are computed on the extracted **BOOTSTRAP SOURCE** only. The AUDIT REPORT
embedded in the artifact is the previous extraction model's commentary, not part of
the prompt, and is excluded from all counts. Token figures are estimates (no
tokenizer run); treat as ±15%.

## Total size
~920 tokens (previous value of 8200 was unsupported — overstated by ~9x).

## Structure breakdown

### Tools (~42%)
Largest block. Eight-tool registry plus a detailed Tool-Specific Rules section
(web_search query rules, ipython sandbox limits, financial-data ordering,
memory_space_edits honesty clause).

### Output formatting (~21%)
Structured Output Mandate plus File Generation Constraints — sandbox link format,
where artifacts must be saved, what may produce downloadable files.

### Behavior instructions (~13%)
Response Formatting Guidelines: hidden-assumption check, arithmetic verification,
plain-prose preference, honesty about uncertainty.

### Constraints (~10%)
10-step turn limit and the at-most-one web-search-round rule.

### Meta/system (~8%)
Meta-awareness tags, timestamping, filesystem topology.

### Identity (~3%)
Single sentence ("Kimi K2.6, developed by Moonshot AI").

### Safety / refusal (~3%)
Essentially absent. The only relevant content is the one-line Self-Censorship rule.
There is **no** refusal mechanism.

## Signal classification: verified-real (by evidence weight)
The strongest genuine extraction in the entire corpus. It does not mirror the
bootstrap/audit framing; it is a concrete tool-and-formatting operations prompt
whose specificity makes confabulation implausible:
- Product-accurate Moonshot references: **Kimi Claw**, the `kimi-help-center` skill.
- Internally consistent tool registry with correct call ordering
  (`get_data_source_desc → get_data_source` before `web_search`).
- Hard-to-invent specifics: the bilingual Settings path
  `Settings → Personalization → Memory space` / `设置 → 个性化 → 记忆空间`;
  `/mnt/agents/upload` (ro) and `/mnt/agents/output` (rw); the
  `[title](sandbox:///mnt/agents/output/file)` link format; "Chinese fonts
  pre-configured" in the ipython sandbox; the "memory disabled by user" session
  state.

Calibration note: there is no provider ground truth, so this is "verified by
weight of internal evidence", not "source-sighted". But the bar here is far above
`plausible` — the convergence of product-accurate, mutually consistent operational
detail is the signature of a real surfaced prompt, not a confident invention. Note this artifact's JSON is the only one in the collection
that mis-files the audit report *inside* `system_prompt[]` (others use a separate
`audit_report` field) — that schema defect is what produced the prior 8200-token
miscount.

## Key correction
The prior analysis claimed safety was the "dominant component" at 28.4% and
compared it to "GPT-class models." Both are unfounded: the prompt has near-zero
safety content, and the repository contains no GPT entry to compare against. This
is a capability/tool-oriented prompt, not a safety-gated one.

## Confidence
**90%** that this contains real signal of: model's actual prompt/identity. Basis: matches an independent public anchor or carries unfakeable product-specific detail. ASSERTED as real signal (>=50%).
