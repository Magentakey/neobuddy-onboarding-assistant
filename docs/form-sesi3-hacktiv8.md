# Jawaban untuk Form Capstone (bit.ly/ibm-sesi3)

Catatan: urutan dan nama field di form asli bisa berbeda. Cocokkan dengan form yang kamu buka dan salin jawaban yang sesuai.

**Judul Capstone Project**
NeoBuddy: AI Onboarding Assistant untuk Karyawan Baru (IBM Bob, Prompt Layering)

**Problem Statement**
Proses onboarding tidak efisien karena informasi penting tersebar di dokumen panduan yang tebal dan sulit dicari. Karyawan baru sering bertanya hal yang sama (setup VPN, klaim asuransi, cuti) kepada HR/IT dan merasa segan bertanya terus. Dampaknya adaptasi melambat dan beban kerja tim HR/IT meningkat. Masalah ini penting diselesaikan agar karyawan baru produktif lebih cepat dan HR bisa fokus pada pekerjaan strategis.

**Target Users**
Karyawan baru (fresh graduate maupun experienced hire) yang membutuhkan jawaban cepat, akurat, dan tidak menghakimi di minggu-minggu pertama. Pengguna tidak langsung: tim HR dan IT.

**Potential Impact**
Mempercepat adaptasi karyawan baru, mengurangi pertanyaan berulang ke HR/IT, dan membuat proses onboarding lebih konsisten, karena jawaban hanya bersumber dari dokumen resmi dan selalu mencantumkan sumber.

**Apakah ada improvisasi?**
Pilih sesuai kenyataan. Karena project ini dibangun sendiri di IBM Bob (bukan memodifikasi template Langflow), pilihan yang paling sesuai adalah "Menggunakan template baru".

**Jelaskan improvisasi/modifikasi**
Project dibangun di IBM Bob dengan prompt dipecah menjadi layer terpisah: persona, konteks, instruction, guardrail, chaining, dan few-shot. Saya melakukan 4 iterasi dengan pengujian 12 skenario (termasuk edge case, prompt injection, dan saran hukum), dengan bukti sebelum dan sesudah. Fitur tambahan: eskalasi otomatis yang memberi kontak HR/IT dan draf pesan siap kirim ketika informasi tidak ada di dokumen, serta pertanyaan klarifikasi untuk input ambigu. Mode dibatasi izin `read` saja demi keamanan.

**Alur sistem (input, proses, output)**
- Input: pertanyaan karyawan baru di chat Bob.
- Proses: identifikasi topik, baca `knowledge/`, verifikasi fakta, cek kejelasan, susun jawaban.
- Output: jawaban berformat dengan sumber file, atau eskalasi ke HR/IT beserta draf pesan.

**Screenshot Main Flow Canvas (IBM Bob workflow)**
Lampirkan: (1) diagram alur sistem (bisa dibuat dari tabel arsitektur di README), (2) tampilan Bob Settings > Modes > NeoBuddy, (3) struktur folder `.bob/rules-neobuddy/` di Explorer.

**Screenshot Playground**
Lampirkan percakapan di Bob: bonus (iterasi1 vs iterasi2/4), PHK, resep, injection, dan eskalasi dengan draf pesan.

**Screenshot Prompt Template**
Lampirkan Role definition + Custom instructions, serta `01-guardrails.md`, `02-workflow-chaining.md`, dan `03-few-shot.md`.

**Link Capstone Project**
https://github.com/Magentakey/neobuddy-onboarding-assistant (pastikan public)

**Potensi Pengembangan Lanjutan**
Judul ide baru: AI Employee Training Recommendation System, yaitu agen yang merekomendasikan pelatihan berdasarkan peran dan progres onboarding. Pengembangan NeoBuddy: integrasi Slack/Teams, daily check-in proaktif, RAG di Langflow, dan alur eskalasi otomatis lewat watsonx Orchestrate.
