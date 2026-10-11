---
name: create-issues
description: "Membuat daftar task lokal dari file Tech Spec atau input langsung (bug, task kecil), dengan pemecahan rekursif menjadi sub-task kecil yang dapat dikerjakan hingga seluruh pekerjaan terurai dan dapat dilacak menyeluruh. Gunakan ketika: user bilang 'buat task', 'ada bug', 'tambah task', 'eksekusi reencana task', 'pecah task', 'breakdown pekerjaan', atau 'detailkan task'."
---

# SKILL: GENERATOR TASK

## 📋 Metadata
- **Nama:** Generator Task
- **Versi:** 1.1
- **Output:** Daftar task terperinci
- **Lokasi File:** `.agents/3-TASKS.md` (default) atau `.agents/3-TASKS/{YYYY-MM-DD}_{slug}.md` (file terpisah)
- **Dependensi:** 2-TECH-SPEC.md (opsional — bisa langsung input user)

## 🎯 Kata Kunci Pemicu
Otomatis aktif saat user menyebut:
- "Buat Task"
- "Buat tugas"
- "Buat daftar tugas"
- "Buat task list"
- "Buat implementation task"
- "Baca TASKS saya"
- "Load Task"

## 📝 Deskripsi
Skill ini membaca Tech Spec dari `.agents/2-TECH-SPEC.md` dan menghasilkan daftar tugas (Task) yang terperinci — konten task menyesuaikan stack apapun. Setiap task berisi: judul, deskripsi, prioritas, status, dan dependensi. Siap pakai untuk Implementasi.

## 📂 Baca/Menyimpan File
- **Baca Tech Spec:** `@.agents/2-TECH-SPEC.md` (jika ada)
- **Baca Task:** `@.agents/3-TASKS.md` (index/utama) atau `@.agents/3-TASKS/*.md` (file terpisah)
- **Simpan Task:** `.agents/3-TASKS.md` (default) atau `.agents/3-TASKS/{YYYY-MM-DD}_{slug}.md` (file terpisah)

## ⚙️ Cara Kerja Skill

### FASE 1: Deteksi Pemicu & Analisa Input

**Langkah 1 — Cek input user:**
- Apakah user sudah memberikan deskripsi langsung? (laporan bug, fitur kecil, dll)
- Atau hanya trigger kata kunci tanpa deskripsi?

**Langkah 2 — Cek sumber acuan:**
- Jika ada 2-TECH-SPEC.md → baca dan jadikan acuan untuk breakdown
- Jika user memberikan input langsung (bug/task sederhana) → langsung proses tanpa Tech Spec, gunakan input user sebagai acuan
- Jika tidak ada 2-TECH-SPEC.md DAN user tidak memberikan input → minta user buat Tech Spec dulu

**Langkah 3 — Deteksi otomatis boilerplate (opsional, jika di direktori project):**
AI cek apakah project sudah ada atau masih baru dengan mencari file kunci:
- `package.json` / `composer.json` / `pyproject.toml` / `go.mod` / `Cargo.toml` / `Gemfile` / `pubspec.yaml`
- Jika ada → sudah ada boilerplate
- Jika tidak ada → project baru

### FASE 2: Konfirmasi Cakupan

Tanyakan 1 hal:
- **Prioritas utama?** (Fitur inti dulu atau semua sekaligus?)

Bawaan:
- Project baru → setup dulu, lalu fitur sesuai modul
- Boilerplate sudah ada → lewati setup, langsung task fitur

### FASE 3: Produksi Task

Dua mode tergantung sumber acuan:
- **Tech Spec** → hasilkan task per modul. User ketik `lanjut` untuk ke modul berikutnya.
- **Input langsung (bug/task)** → hasilkan semua task langsung, tanpa pembagian modul.

### FASE 4: Finalisasi

**Langkah 1 — Tentukan lokasi penyimpanan:**

| Kondisi | Lokasi | Alasan |
|---|---|---|
| Bug/task kecil (input langsung, < 10 task) | Tambahkan ke `.agents/3-TASKS.md` | Ringkas, tidak perlu file baru |
| Tech Spec besar (>= 20 task atau >= 3 modul) | `.agents/3-TASKS/{YYYY-MM-DD}_{slug}.md` | Task banyak, butuh ruang sendiri |
| Tech Spec kecil (< 20 task) | Tambahkan ke `.agents/3-TASKS.md` | Cukup di file utama |

**Langkah 2 — Format penamaan file terpisah:**
- Format: `{YYYY-MM-DD}_{slug}.md`
- Slug diambil dari judul Tech Spec atau ringkasan user (huruf kecil, spasi diganti tanda hubung)
- Contoh: `2026-09-01_auth-feature.md`, `2026-09-01_fix-login-bug.md`

**Langkah 3 — Finalisasi:**
1. Tampilkan daftar task ke user untuk ditinjau.
2. Simpan task ke lokasi yang sudah ditentukan.
3. Jika pakai file terpisah, tambahkan index/link di `.agents/3-TASKS.md` (opsional).
4. Rekomendasikan lanjut ke **Implementation**.

## 📑 Struktur Task
Setiap task memiliki format:
- **ID:** T-XX
- **Judul:** [Nama task]
- **Deskripsi:** [Penjelasan singkat]
- **Modul:** [Nama modul]
- **Prioritas:** Tinggi/Sedang/Rendah
- **Status:** Belum Dikerjakan/Sedang Dikerjakan/Selesai
- **Dependensi:** [ID task yang harus selesai dulu]
- **Tanggal:** [YYYY-MM-DD]
- **Estimasi:** [Jam/hari]
- **File yang diubah:** [Path file]

## 📄 TASK LIST

> AI hasilkan task. Task bersifat konkret dan dapat dikerjakan.
>
> **Sumber acuan untuk task:**
> - Tech Spec → rincian fitur per modul
> - Input langsung (bug/task) → rincian langsung dari deskripsi user
>
> **Task yang muncul tergantung konten + hasil deteksi otomatis — tidak ada template tetap:**
> - Project baru → sertakan Penyiapan Project
> - Boilerplate sudah ada → lewati Penyiapan Project, langsung fitur
> - Ada database → task setup DB + model/entity + migrasi
> - Ada interface/API → task routing/endpoint/aksi
> - Ada frontend → task komponen/halaman/layout
> - Ada autentikasi → task alur auth
> - Tidak ada database → lewati semua task terkait DB
> - Static/frontend-only → lewati backend, fokus ke UI

=== DIHASILKAN OLEH AI BERDASARKAN ACUAN (TECH SPEC / INPUT USER) ===

AI tentukan skenario berdasarkan hasil FASE 1 & 2:
- **Input langsung (bug/task)** → rincian langsung dari deskripsi user, tanpa modul
- **Project baru + Tech Spec** → mulai dari T-01: Penyiapan Project, lalu task fitur per modul
- **Boilerplate + Tech Spec** → lewati T-01 Penyiapan Project, mulai dari task fitur langsung

AI urutkan task berdasarkan dependensi. Jangan buat task yang tidak relevan (mis. lewati database jika tidak pakai DB, lewati auth jika tidak disebut acuan).


