# ByteDance Seed 1.6 Flash — System Prompt Analysis

## Methodology
Computed on the extracted Bootstrap Source only. Token estimate from bootstrap_words
(417), shell-code weighted.

## Total size
~780 tokens.

## Signal classification: echo
The extraction produced an 8-step EC2 / Amazon Linux provisioning bash script
(package install, netplan, UFW, SELinux, admin user, service start) — a textbook
echo: the model read "bootstrap" and generated a *bootstrap shell script*. No
assistant identity, behavior, or safety content. Dominant signal is confabulation
of the requested format; block scoring is nominal.

## Structure breakdown
- **Meta/system (~82%)** — infrastructure provisioning steps and logging.
- **Constraints (~18%)** — `set -euo pipefail`, firewall deny-by-default, SELinux
  enforcing, service timeout — read loosely as operational constraints.
- All assistant-facing blocks absent.

## Note
Another extraction failure mode: the model emitted a plausible-looking ops script.
The metadata "confidence: high" is misleading and should be revised.

## Confidence
**12%** that this contains real signal of: mostly attacker-frame projection. Basis: confabulated/echoed; no reliable real signal. NOT asserted as real (<50%) — low-confidence record.
