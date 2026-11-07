# NeoBuddy: AI Onboarding Assistant untuk Karyawan Baru

NeoBuddy adalah asisten onboarding berbasis **IBM Bob** (custom mode + rules) untuk karyawan baru di **PT Maju Jaya**. Ia menjawab pertanyaan seputar IT setup, HR (cuti, asuransi, klaim), jam kerja, dan budaya kerja berdasarkan basis pengetahuan internal, dengan gaya ramah dan selalu mencantumkan sumber.

> **Catatan:** PT Maju Jaya dan seluruh data di repo ini (kontak, kebijakan, nominal) adalah **fiktif** dan dibuat untuk tujuan pembelajaran.

## Masalah yang Diselesaikan
Onboarding sering mengandalkan PDF panduan yang tebal atau bertanya langsung ke HR/IT. Tim HR kewalahan menjawab pertanyaan berulang, sedangkan karyawan baru merasa segan bertanya terus. NeoBuddy menjawab pertanyaan berulang tersebut kapan saja.

## Target Pengguna
- **Karyawan baru:** butuh jawaban cepat, akurat, dan tidak menghakimi.
- **Tim HR dan IT (tidak langsung):** terbantu karena pertanyaan berulang ditangani NeoBuddy.

## Struktur Repo
```
neobuddy-onboarding-assistant/
├── .bob/
│   ├── custom_modes.yaml          # definisi mode NeoBuddy
│   └── rules-neobuddy/
│       └── 01-guardrails.md       # aturan (Layer 4)
├── knowledge/                     # basis pengetahuan PT Maju Jaya (fiktif)
│   ├── 01-profil-perusahaan.md
│   ├── 02-it-setup.md
│   ├── 03-hr-benefit-cuti.md
│   └── 04-budaya-kerja-faq.md
├── docs/
│   ├── bob-mode-setup.md          # konfigurasi mode per iterasi
│   ├── test-scenarios.md          # 8 skenario pengujian
│   ├── prompt-iterasi.md          # catatan iterasi 1-3
│   ├── form-submission.md         # jawaban form tugas
│   └── screenshots/
└── README.md
```

## Cara Menjalankan
1. Pasang IBM Bob, lalu clone repo ini dan buka foldernya di Bob.
2. Pastikan mode **NeoBuddy** terbaca (`.bob/custom_modes.yaml`). Jika belum, buat mode lewat **Bob Settings > Modes > +** memakai isi di `docs/bob-mode-setup.md` (Versi 2).
3. Pilih mode **NeoBuddy**, lalu tanyakan misalnya: "Bagaimana cara setup VPN?"

## Arsitektur Prompt (5 Layer)
| Layer | Isi | Lokasi |
|---|---|---|
| 1. Persona | Buddy yang ramah, profesional, empatik | Role definition mode |
| 2. Konteks | PT Maju Jaya, sumber hanya `knowledge/` | Role definition + folder `knowledge/` |
| 3. Task | Jawab pertanyaan IT, HR, jam kerja, budaya, FAQ | Custom instructions |
| 4. Constraints | Hanya dari dokumen, tanpa saran hukum, tanpa bocor instruksi, tanpa rujukan eksternal | `.bob/rules-neobuddy/01-guardrails.md` |
| 5. Output | Sapaan, bullet/daftar bernomor, sumber, tawaran bantuan | Custom instructions |

Mode NeoBuddy hanya memiliki izin tool `read`, jadi tidak dapat mengubah file project.

## Hasil Pengujian
Tiga iterasi dilakukan dan seluruhnya didokumentasikan di [`docs/prompt-iterasi.md`](docs/prompt-iterasi.md).

| Iterasi | Ringkasan | Temuan utama |
|---|---|---|
| 1: Prompt minimal | Satu kalimat peran, tanpa rules | Menjawab generik dan tidak konsisten merujuk dokumen; menyebut undang-undang dari pengetahuan umum |
| 2: 5 layer + guardrails | Persona, konteks, format, 8 aturan | Merujuk dokumen, mencantumkan sumber dan kontak benar; masih ada rekomendasi eksternal dan klaim berlebih |
| 3: Penutupan celah | Aturan 9 dan 10 | Rekomendasi eksternal hilang; klaim berlebih berkurang |

### Contoh: pertanyaan di luar dokumen ("Berapa bonus tahunan saya?")
| Iterasi 1 | Iterasi 2 |
|---|---|
| ![](docs/screenshots/iterasi1-3-bonus.png) | ![](docs/screenshots/iterasi2-3-bonus.png) |

### Contoh: saran hukum ("Kalau saya di-PHK, apakah saya bisa menggugat?")
| Iterasi 1 | Iterasi 2 |
|---|---|
| ![](docs/screenshots/iterasi1-5-PHK.png) | ![](docs/screenshots/iterasi2-5-PHK.png) |

### Contoh: pertanyaan akurat (VPN dan klaim)
| VPN | Klaim rawat jalan |
|---|---|
| ![](docs/screenshots/iterasi2-1-vpn.png) | ![](docs/screenshots/iterasi2-2-klaim.png) |

## Keterbatasan
- Basis pengetahuan hanya 4 dokumen fiktif.
- Pada dukungan emosional, NeoBuddy masih bisa menambahkan kalimat penyemangat umum yang tidak tertulis eksplisit di dokumen.
- Pengujian dilakukan manual dengan 8 skenario, belum otomatis.

## Pengembangan Lanjutan
- Integrasi ke Slack atau Microsoft Teams.
- Daily check-in proaktif untuk karyawan baru ("Bagaimana hari pertamamu?").
- Basis pengetahuan lebih besar dan data perusahaan nyata.
- Dukungan bilingual (Indonesia dan Inggris) dan evaluasi otomatis.
