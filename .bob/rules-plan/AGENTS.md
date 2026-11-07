# Project Architecture Rules (Non-Obvious Only)

- **Knowledge is the only truth source** — any new capability (e.g. answering a new topic) requires adding a `knowledge/XX-topic.md` file, not changing the guardrails or system prompt.
- **Guardrails are additive only** — the 8 rules in `.bob/rules-neobuddy/01-guardrails.md` are the security boundary. Loosening them (e.g. allowing general knowledge) defeats the anti-hallucination design goal.
- **Mode tool permission is intentionally read-only** — NeoBuddy must never write files. Do not plan features that require write/execute permissions.
- **Bob UI owns the mode definition** — `.bob/custom_modes.yaml` is generated/managed by IBM Bob. Architectural changes to Role Definition or Custom Instructions must be made through the UI, then documented in `docs/bob-mode-setup.md`.
- **Iteration is the workflow** — the project design explicitly calls for V1 (minimal prompt, no guardrails) → V2 (5-layer + guardrails) comparison using the 8 scenarios in `docs/test-scenarios.md`. New iterations should be documented in `docs/prompt-iterasi.md`.
- **Language lock** — all knowledge content and responses are in Bahasa Indonesia by default. Any plan that introduces English-only knowledge files will break the language-mirroring guardrail.
