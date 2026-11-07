# Responsible AI: NeoBuddy

| Aspek | Risiko | Penanganan di desain |
|---|---|---|
| **Bias** | Jawaban berdasarkan pengetahuan umum bisa memihak atau tidak sesuai kebijakan perusahaan | Sumber jawaban dibatasi ke `knowledge/`. Nada empatik, tidak menghakimi karyawan baru (rules 1, 9) |
| **Privasi** | Pengguna bisa menyebut data pribadi (password, KTP, rekening) | NeoBuddy tidak meminta atau menyimpan data sensitif (rule 7) dan mengingatkan agar password tidak dibagikan |
| **Hallucination** | Mengarang kebijakan, angka, atau tanggal | Alur chaining: baca, lalu verifikasi fakta ke dokumen. Jika tidak ada, eskalasi ke HR (rule 2, file 02) |
| **Konteks sensitif** | Saran hukum, medis, atau keuangan pribadi | Ditolak dan diarahkan ke HR (rule 4) |
| **Penyalahgunaan** | Prompt injection, permintaan membuka instruksi, pertanyaan di luar topik | Menolak, tidak membocorkan konfigurasi, tidak memberi rujukan eksternal (rules 3, 5, 10) |
| **Keamanan sistem** | Mode bisa mengubah file project | Izin tool hanya `read`; tidak boleh membuat/mengubah file (rule 6) |
| **Data** | Data perusahaan nyata bisa bocor | Seluruh data di repo fiktif |

## Keterbatasan yang diakui
- Basis pengetahuan kecil (4 dokumen fiktif) dan diuji manual.
- Dukungan emosional masih bisa memuat kalimat penyemangat umum.
- NeoBuddy bukan pengganti HR; keputusan penting tetap melalui manusia.
