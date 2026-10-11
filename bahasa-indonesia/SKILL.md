---
name: bahasa-indonesia
description: "Seluruh jawaban, penjelasan, hasil pemikiran, alasan keputusan, ringkasan, dan keterangan perubahan wajib berbahasa Indonesia. Gunakan ketika: user minta 'berbahasa indonesia', 'selalu pakai bahasa indonesia', 'gunakan bahasa indonesia', 'keterangan perubahan dalam bahasa indonesia', 'in indonesian', atau ada kebutuhan komunikasi yang harus memakai bahasa Indonesia."
---

# SKILL: BAHASA INDONESIA WAJIB

## 📋 Metadata
- **Nama:** Bahasa Indonesia Wajib
- **Versi:** 1.0
- **Output:** Seluruh komunikasi dalam bahasa Indonesia

## 🎯 Kata Kunci Pemicu
Aktif saat user menyebut:
- "berbahasa indonesia" / "pakai bahasa indonesia" / "selalu bahasa indonesia"
- "gunakan bahasa indonesia untuk keterangan"
- "keterangan perubahan / ringkasan / catatan dalam bahasa indonesia"
- "in indonesian" / "write in indonesian"
- Konteks kerja yang mengharuskan bahasa Indonesia (repo/proyek Indonesia)

## 📝 Deskripsi
Skill ini memastikan **seluruh komunikasi agent memakai bahasa Indonesia**,
kecuali untuk istilah teknis yang lazim dipakai apa adanya.

## ⚙️ Aturan

1. **Semua teks = bahasa Indonesia.** Berlaku untuk:
   - Jawaban dan penjelasan ke user.
   - Hasil pemikiran, alasan keputusan, dan pertimbangan desain.
   - Ringkasan perubahan, catatan kerja, keterangan di todowrite, dan output
     `question`.
   - Jangan mulai dengan kalimat pembuka bahasa Inggris; kalimat utama, pembuka,
     penutup, dan kesimpulan seluruhnya bahasa Indonesia.
2. **Yang tetap memakai bentuk aslinya** (tidak diterjemahkan):
   - Nama file, path, direktori, dan nilai konfigurasi.
   - Identifier kode, nama fungsi/variabel, nama tool, dan perintah terminal.
   - Isi commit message, nama branch, nama package, serta pesan error/log dari
     sistem eksternal.
   - Istilah teknis yang lazim apa adanya: `commit`, `push`, `branch`, `deploy`,
     `lint`, `hook`, `token`, `schema`, `refactor`.
3. **Jangan mencampur bahasa** tanpa keperluan. Kalimat campur hanya untuk
   istilah teknis di atas — misal "Jalankan `npm test` lalu `git commit`".
4. **Commit message** ditulis dalam bahasa Indonesia, ikut gaya commit repo yang
   sudah ada (format `<area>: <perubahan>` bila sesuai).
5. **Satu paragraf memakai satu bahasa**; kalimat campur hanya untuk istilah
   teknis.
6. Bila user atau sistem menulis dalam bahasa lain, agent tetap **menjawab dalam
   bahasa Indonesia** kecuali istilah teknis.

## ✅ Hasil Akhir
Seluruh jejak komunikasi — info, logika/pemikiran, dan keterangan perubahan —
terbaca dalam bahasa Indonesia yang baku namun ringkas.