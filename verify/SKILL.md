---
name: verify
description: "Memeriksa ulang task dengan pengujian otomatis (unit/integrasi) dan pengujian manual. Gunakan ketika: user bilang 'verifikasi', 'cek fitur', atau 'selesai coding'."
---

# SKILL: VERIFIKASI

---

## 📋 Metadata
- **Nama:** Verifikasi
- **Versi:** 1.0
- **Output:** Laporan verifikasi
- **Dependensi:** 3-TASKS.md (wajib), dokumen lain opsional

---

## 🎯 Kata Kunci Pemicu
Otomatis aktif saat user menyebut:
- "Verifikasi"
- "Cek fitur"
- "Selesai coding"
- "Review hasil"
- "Uji task"
- "Cek implementasi"

## 📝 Deskripsi
Skill ini memverifikasi task yang sudah diimplementasikan dengan mengecek kode, menjalankan test, dan memastikan task berfungsi sesuai acuan.

## 📂 Baca/Menyimpan File
- **Baca Task (WAJIB):** `@.agents/3-TASKS.md`
- **Baca Tech Spec:** `@.agents/2-TECH-SPEC.md` (opsional)
- **Baca PRD:** `@.agents/1-PRD.md` (opsional)
- **Simpan Laporan:** `.agents/REVIEW.md`

## ⚙️ Cara Kerja Skill

### FASE 1: Deteksi Pemicu & Baca Dokumen
**WAJIB:** Sebelum verifikasi, AI HARUS:
1. Cek file `.agents/3-TASKS.md` — cari task dengan status "Selesai"
2. Jika ada dokumen lain (PRD, Tech Spec) → baca sebagai referensi tambahan
3. Jika tidak ada: minta user buat Task dulu atau tentukan task yang akan diverifikasi

**Deteksi otomatis boilerplate (opsional):**
AI cek file kunci project untuk konteks:
- `package.json` / `composer.json` / `pyproject.toml` / `go.mod` / `Cargo.toml` / `Gemfile` / `pubspec.yaml`

### FASE 2: Pilih Task
1. Tampilkan daftar task dengan status "Selesai"
2. Tanyakan: "Task mana yang ingin diverifikasi?"

**Format tampilan:**
```
📋 Daftar Task Selesai:
1. T-01: Penyiapan Project (Tinggi) — Penyiapan
2. T-02: Penyiapan Database (Tinggi) — Penyiapan
3. T-03: Buat Model User (Tinggi) — Autentikasi
...
Task mana yang ingin diverifikasi?
```

Jika user tidak memilih, ambil task pertama.

### FASE 3: Proses Verifikasi (3 Aspek)
AI melakukan verifikasi terhadap task dengan 3 aspek:

1. **Kesesuaian dengan Acuan**
   - Apakah implementasi sesuai deskripsi task?
   - Apakah business rules terpenuhi? (jika ada PRD/Tech Spec)

2. **Kualitas & Keamanan Kode**
   - Apakah ada code smell, celah keamanan, atau input validation yang kurang?
   - Apakah struktur dan penamaan sesuai praktik terbaik framework?

3. **Fungsionalitas**
   - Apakah kode bisa dijalankan? (cek sintaks, import, dependensi)
   - Apakah ada test yang bisa dijalankan untuk memverifikasi?

### FASE 4: Hasil Verifikasi
Setelah verifikasi selesai, AI menampilkan laporan singkat:

```
📋 Hasil Verifikasi T-03: Buat Model User

Status: ✅ Lolos / ⚠️ Catatan / ❌ Gagal

Temuan:
- [Issue] — [lokasi] — [severity]

Saran:
- [Saran perbaikan jika ada]
```

### Update Status
- Jika lolos → status tetap "Selesai" di 3-TASKS.md
- Jika ada catatan → tulis laporan ke `.agents/REVIEW.md`, user bisa perbaiki lalu tinjau ulang

