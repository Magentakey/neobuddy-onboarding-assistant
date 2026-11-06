# NeoBuddy: AI Onboarding Assistant untuk Karyawan Baru

AI Agent berbasis **IBM Bob** (custom mode + rules) yang membantu karyawan baru PT Maju Jaya (fiktif) mendapat jawaban instan seputar IT setup, HR, dan budaya kerja.

## Struktur
- `.bob/custom_modes.yaml`: definisi mode NeoBuddy
- `.bob/rules-neobuddy/`: guardrails (Layer 4)
- `knowledge/`: basis pengetahuan perusahaan fiktif
- `docs/`: panduan setup, skenario tes, catatan iterasi, screenshot

## Cara Pakai
1. Clone repo, buka folder di IBM Bob.
2. Pilih mode **NeoBuddy** di selector Modes.
3. Tanyakan hal seputar onboarding, misalnya "Bagaimana cara setup VPN?"

## Prompt Layering
1. Persona: buddy ramah, profesional, empatik
2. Konteks: PT Maju Jaya, sumber hanya `knowledge/`
3. Task: menjawab pertanyaan onboarding
4. Constraints: `.bob/rules-neobuddy/01-guardrails.md`
5. Output format: bullet points, sumber, tawaran bantuan

> Seluruh data perusahaan dalam repo ini fiktif.
