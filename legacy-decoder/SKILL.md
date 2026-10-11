---
name: legacy-decoder
description: "Membongkar legacy code secara reverse-engineer menjadi dokumentasi terstruktur (Tech Spec + Task). Gunakan ketika: user bilang 'pahami kode', 'analisis legacy', 'reverse engineer', 'mapping kode', 'dokumentasi kode existing'."
---

# SKILL: LEGACY DECODER

## 📋 Metadata
- **Nama:** Legacy Decoder
- **Versi:** 1.0
- **Output:** Analisis arsitektur + Tech Spec (opsional) + Task List
- **Lokasi File:** `.agents/4-LEGACY-DECODER.md`
- **Dependensi:** Tidak ada (bekerja dari kode existing)

## 🎯 Kata Kunci Pemicu
- "Pahami kode"
- "Analisis legacy"
- "Reverse engineer"
- "Mapping kode"
- "Dokumentasi kode existing"
- "Baca legacy code"
- "Review codebase"
- "Baca hasil analisis"
- "Load legacy analysis"

## 📂 Baca/Menyimpan File
- **Baca:** `@.agents/4-LEGACY-DECODER.md`
- **Simpan:** `.agents/4-LEGACY-DECODER.md`
- **Output Tech Spec:** `.agents/2-TECH-SPEC.md` (opsional)
- **Output Tasks:** `.agents/3-TASKS.md`

## ⚙️ Cara Kerja Skill

### FASE 0: Deteksi Pemicu
- Jika user bilang **"baca"** atau **"load"** → Baca `.agents/4-LEGACY-DECODER.md` dan beri ringkasan.
- Jika user bilang **"pahami"**, **"analisis"**, **"reverse"**, **"mapping"**, atau **"review"** → Lanjut ke FASE 1.

### FASE 1: Penelusuran
1. Pindai struktur folder project
2. Baca file konfigurasi (`package.json`, `composer.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Gemfile`, `pubspec.yaml`, `CMakeLists.txt`, `pom.xml`, dll.)
3. Identifikasi framework, runtime, database, dan dependensi utama
4. Simpan ringkasan stack + struktur folder ke `.agents/4-LEGACY-DECODER.md` (tambahkan)

### FASE 2: Pemetaan Codebase
1. Petakan struktur direktori (controller/model/service/route/view)
2. Identifikasi entry point dan alur request
3. Simpan graf dependensi / arsitektur tingkat tinggi ke `.agents/4-LEGACY-DECODER.md` (tambahkan)

### FASE 3: Ekstraksi Logika Bisnis
1. Ekstrak daftar route/endpoint/aksi
2. Identifikasi entity/model utama dan relasinya
3. Catat aturan bisnis yang terlihat dari kode
4. Simpan ringkasan logika bisnis ke `.agents/4-LEGACY-DECODER.md` (tambahkan)

### FASE 4: Reverse Engineering Database (jika ada DB)
1. Baca file migration / definisi schema
2. Petakan relasi antar-entity
3. Catat index, constraint, trigger
4. Simpan ringkasan database ke `.agents/4-LEGACY-DECODER.md` (tambahkan)

### FASE 5: Pembuatan Output
Setelah FASE 1-4 selesai dan semua tersimpan:

**Opsional — Tech Spec (`2-TECH-SPEC.md`):**
1. Tanyakan: "Buat Tech Spec dari hasil analisis? (y/n)"
2. Jika ya → hasilkan 5 bagian (Tech Stack, Desain DB, Antarmuka, Alur, Keamanan)
3. Simpan ke `.agents/2-TECH-SPEC.md`

**Wajib — Task (`3-TASKS.md`):**
1. Hasilkan daftar task berdasarkan temuan (refactor, perbaikan bug, optimasi, dokumentasi)
2. Simpan ke `.agents/3-TASKS.md`

### FASE 6: Finalisasi
1. Tampilkan ringkasan hasil analisis
2. Rekomendasikan lanjut ke **implement-task** atau **verify**
