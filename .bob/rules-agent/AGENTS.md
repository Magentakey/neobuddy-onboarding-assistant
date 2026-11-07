# Project Coding Rules (Non-Obvious Only)

- The only "code" files are Markdown (`.md`) and YAML (`.yaml`). There is no compile step.
- `.bob/rules-neobuddy/01-guardrails.md` is auto-injected by Bob when the active mode slug is `neobuddy`. Renaming the folder to `_off-rules-neobuddy` disables guardrails without deleting them — useful for before/after testing (see `docs/bob-mode-setup.md`).
- The mode's Role Definition and Custom Instructions live in `.bob/custom_modes.yaml` (managed by Bob UI). Do not create this file manually — edits via UI are the canonical approach; direct YAML edits may be overwritten by Bob.
- Knowledge files must stay in `knowledge/` and be Markdown — Bob's read tool resolves them relative to the project root.
- All knowledge content and guardrail text must be in **Bahasa Indonesia** to match the target users.
- Do not add `<script>`, external URLs, or code examples inside `knowledge/` files — NeoBuddy reads them verbatim and may reproduce them to users.
