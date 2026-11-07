# Project Documentation Rules (Non-Obvious Only)

- There is no source code — the entire project is IBM Bob configuration + Markdown knowledge base.
- `docs/bob-mode-setup.md` contains the **exact** Role Definition and Custom Instructions text to paste into the Bob UI (not auto-applied by file presence).
- `docs/prompt-iterasi.md` is a **template** to be filled in with real test results; it contains no actual iteration data yet.
- `docs/test-scenarios.md` lists 8 test cases that cover the full guardrail surface (accuracy, anti-hallucination, off-topic rejection, prompt injection, empathy).
- The "5-layer prompt" architecture is the core design concept: Persona → Context → Task → Constraints → Output Format. See `docs/bob-mode-setup.md` for the mapping.
- All company data (PT Maju Jaya, contacts, policies) is **fictional** — do not treat it as real.
