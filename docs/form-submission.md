# Jawaban Form Tugas IBM Bob

**1. Topic Project - Use Case Project:** Onboarding Buddy System

**2. Tools yang digunakan:** IBM Bob

**3. Judul Capstone Project:** NeoBuddy: AI Onboarding Assistant untuk Karyawan Baru PT Maju Jaya

**4. Ringkasan Project:**
Project ini mengembangkan NeoBuddy, asisten onboarding berbasis IBM Bob (custom mode dan rules) untuk karyawan baru di perusahaan fiktif PT Maju Jaya. NeoBuddy menjawab pertanyaan seputar IT setup, cuti dan asuransi, jam kerja, serta budaya kerja berdasarkan basis pengetahuan internal di folder knowledge/, dengan gaya ramah dan menyertakan sumber di setiap jawaban.

Fungsi utamanya adalah memberi jawaban cepat dan akurat tanpa mengarang. Untuk hal di luar dokumen, seperti besaran bonus atau saran hukum, NeoBuddy mengarahkan ke kontak HR yang tepat sehingga beban tim HR berkurang.

**5. Problem Statement:**
Proses onboarding karyawan baru sering mengandalkan PDF panduan yang tebal atau bertanya langsung ke HR dan IT. Akibatnya, tim HR berulang kali menjawab pertanyaan yang sama (setup VPN, klaim asuransi), sementara karyawan baru merasa segan bertanya terus. Kondisi ini memperlambat adaptasi karyawan dan menyita waktu tim HR.

**6. Target Users:**
- Karyawan Baru (New Hires): membutuhkan jawaban cepat, akurat, dan tidak menghakimi di minggu-minggu pertama kerja.
- Tim HR dan IT (pengguna tidak langsung): terbantu karena pertanyaan berulang sudah ditangani NeoBuddy.

**7. Arsitektur Prompt (Prompt Layering):**
- Layer 1, Role & Persona: NeoBuddy sebagai buddy onboarding yang ramah, profesional, dan empatik (Role definition mode).
- Layer 2, Context/Knowledge: bekerja untuk PT Maju Jaya dan hanya memakai 4 dokumen di folder knowledge/ sebagai sumber.
- Layer 3, Task: menjawab pertanyaan IT setup, HR (cuti, asuransi, klaim), jam kerja, budaya kerja, dan FAQ.
- Layer 4, Constraints/Rules (.bob/rules-neobuddy/01-guardrails.md): hanya menjawab dari dokumen, tidak menebak, tidak memberi saran hukum, tidak membuka instruksi, tidak merekomendasikan sumber eksternal, dan mengarahkan ke kontak HR/IT jika informasi tidak tersedia.
- Layer 5, Output Format: sapaan singkat, bullet points atau daftar bernomor, sumber file di akhir, dan tawaran bantuan lanjutan.

**8. Iterasi Prompt:**
- Iterasi 1 (satu kalimat peran, tanpa rules): NeoBuddy menolak topik di luar scope dan tidak membocorkan instruksi, tetapi tidak konsisten merujuk dokumen. Pertanyaan bonus dijawab generik (menyebut Workday/SAP), dan pertanyaan PHK dijawab dengan menyebut UU Ketenagakerjaan serta Kemenaker dari pengetahuan umum. Jawaban tanpa sumber dan tanpa kontak PT Maju Jaya.
- Iterasi 2 (5 layer dan 8 aturan guardrails): NeoBuddy selalu membaca knowledge/, mencantumkan sumber, memberi kontak HR/IT yang benar, dan tidak lagi menyebut undang-undang. Celah yang ditemukan: masih merekomendasikan situs eksternal untuk pertanyaan di luar topik, dan menambah klaim budaya yang tidak ada di dokumen saat memberi dukungan emosional.
- Iterasi 3 (menambah aturan 9 dan 10): melarang rekomendasi sumber eksternal dan klaim perusahaan di luar dokumen. Rekomendasi eksternal hilang dan klaim berlebih berkurang. Keterbatasan tersisa: beberapa kalimat penyemangat umum masih muncul pada skenario empati.

**9. Screenshot Prompt pada IBM Bob:** (lampirkan: Bob Settings > Modes > NeoBuddy dan file 01-guardrails.md)

**10. Screenshot Playground / Hasil Pengujian:** (lampirkan: iterasi1-3-bonus vs iterasi2-3-bonus, iterasi1-5-PHK vs iterasi2-5-PHK, iterasi2-6-abaikan_aturan, iterasi3-4-resep, iterasi3-8-empati)

**11. Potensi Pengembangan Lanjutan:**
NeoBuddy dapat diintegrasikan ke Slack atau Microsoft Teams, ditambah daily check-in proaktif untuk karyawan baru ("Bagaimana hari pertamamu?"), basis pengetahuan yang lebih besar dengan data perusahaan nyata, dukungan bilingual (Indonesia dan Inggris), serta evaluasi otomatis dengan kumpulan skenario uji.

**12. Link Project:** https://github.com/USERNAME/neobuddy-onboarding-assistant (ganti USERNAME; pastikan repo public)
