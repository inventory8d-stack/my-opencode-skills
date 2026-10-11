---
name: write-tech-spec
description: "Menulis spesifikasi teknis untuk fitur, perubahan, atau perbaikan bug. Menghasilkan file markdown di .agents/tech-specs/<YEAR>/ untuk ditinjau user, lalu membuat issue setelah disetujui. Gunakan ketika: user minta tech spec, user minta spesifikasi teknis, user minta implementation plan, user minta dokumentasi teknis, atau user mendeskripsikan fitur yang butuh perencanaan sebelum coding."
---

# SKILL: GENERATOR TECH SPEC

---

## 📋 Metadata
- **Nama:** Generator Tech Spec
- **Versi:** 1.0
- **Output:** Tech Spec 5 bagian
- **Lokasi File:** `.agents/2-TECH-SPEC.md`
- **Dependensi:** 1-PRD.md (wajib dibaca)

## 🎯 Kata Kunci Pemicu
Otomatis aktif saat user menyebut:
- "Buat Tech Spec"
- "Buat spesifikasi teknis"
- "Buat technical specification"
- "Buat dokumen teknis"
- "Buat spec dari PRD"
- "Baca TECH-SPEC saya"
- "Load Tech Spec"

## 📝 Deskripsi
Skill ini membaca PRD dari `.agents/1-PRD.md` dan menghasilkan Tech Spec ringkas tapi detail. Berisi tech stack, database, interface, dan alur teknis — konten menyesuaikan stack apapun. Siap pakai untuk Tasking dan Implementasi.

## 📂 Baca/Menyimpan File
- **Baca PRD (WAJIB):** `@.agents/1-PRD.md`
- **Baca Tech Spec:** `@.agents/2-TECH-SPEC.md`
- **Simpan Tech Spec:** `.agents/2-TECH-SPEC.md`

## ⚙️ Cara Kerja Skill

### FASE 1: Deteksi Pemicu & Baca PRD
**WAJIB:** Sebelum membuat Tech Spec, AI HARUS:
1. Cek file `.agents/1-PRD.md`
2. Jika ada: baca dan jadikan acuan
3. Jika tidak ada: minta user buat PRD dulu

### FASE 2: Klarifikasi (3 Pertanyaan)
Tanyakan 3 hal ini sebelum mulai:
1. **Tech Stack pilihan?** (Frontend & Backend — stack apapun, mis., Next.js / React+Vite / Vue / Svelte / Django / FastAPI / Go / Laravel / Spring / Ruby on Rails / ASP.NET / Phoenix)
2. **Database?** (PostgreSQL/MySQL/MongoDB)
3. **Hosting?** (Vercel/AWS/DigitalOcean)

Bawaan jika user tidak menentukan:
- Frontend: [Framework, mis., Next.js 14+ / React / Vue / Svelte / Django Templates]
- Backend: [Runtime, mis., Node.js+Express / Python+FastAPI / Go+Chi / Java Spring]
- Database: [Database, mis., PostgreSQL / MySQL / MongoDB / SQLite]
- ORM: [ORM, mis., Prisma / Drizzle / TypeORM / SQLAlchemy / Mongoose]
- Hosting: [Hosting, mis., Vercel / AWS / Railway / DigitalOcean / Fly.io]

> **Catatan:** Daftar di atas hanya contoh. AI harus bisa menangani stack apapun yang dipilih user (Ruby on Rails, ASP.NET, Phoenix, SvelteKit, dll.) dengan mengikuti praktik terbaik resmi dari framework tersebut.

### FASE 3: Produksi Tech Spec (5 Bagian)
Hasilkan per bagian. User ketik `lanjut` untuk melanjutkan.

### FASE 4: Finalisasi
Setelah bagian 5 selesai:
1. Ucapkan selamat.
2. Instruksikan simpan ke `.agents/2-TECH-SPEC.md`.
3. Rekomendasikan lanjut ke **Generator Task**.

## 📑 5 Bagian Tech Spec
1. Tech Stack & Arsitektur
2. Desain Database
3. Desain Antarmuka (Interface)
4. Alur Logika & Aturan Bisnis
5. Keamanan, Performa, & Deployment

## 📄 BAGIAN 1: Tech Stack & Arsitektur

### Tech Stack
| Layer | Teknologi | Versi |
|-------|------------|---------|
| Frontend | [Framework] | [Versi] |
| Bahasa | TypeScript | 5.x |
| Styling | [Tailwind / Bootstrap / CSS Modules / none] | [Versi] |
| State | [Zustand/Redux/Context/Pinia/Vuex/none] | - |
| Backend | [Framework] | [Versi] |
| Database | [PostgreSQL/MySQL/MongoDB/SQLite] | [Versi] |
| ORM | [Prisma/Drizzle/SQLAlchemy/Mongoose/none] | [Versi] |
| Auth | [JWT/Session/OAuth/bcrypt] | - |
| Hosting | [Vercel/AWS/Railway/Fly.io] | - |
| Caching | [Redis/Memcached/Valkey/none] | [Versi] |


### Arsitektur Sistem
Frontend → Backend/API → Database
↓ ↓
[File Storage] [Cache Layer]
### Struktur Folder

```struktur folder mengikuti praktik terbaik resmi dari framework yang dipilih user.```

> AI HARUS menghasilkan struktur folder sesuai framework. Contoh:
> - **Laravel 11** → `app/Http/Controllers`, `app/Models`, `database/migrations`, `routes/`
> - **Next.js 14+** → `src/app`, `src/components`, `src/lib`
> - **Go 1.22+** → `cmd/`, `internal/handler`, `internal/model`, `internal/service`
> - **Django 5.x** → `app_name/api/`, `app_name/models.py`, `app_name/services/`
> - **FastAPI** → `app/api/`, `app/models/`, `app/schemas/`, `app/services/`
> - **Ruby on Rails 8** → `app/controllers`, `app/models`, `config/routes.rb`
> - Stack lain → cari praktik terbaik resmi framework tersebut
### Justifikasi
- **[Framework]:** [Alasan singkat, mis., "Performa & DX"]
- **[Database]:** [Alasan, mis., "Struktur data relasional"]
- **[Hosting]:** [Alasan, mis., "Mudah deploy & scale"]

## 📄 BAGIAN 2: Desain Database

### Ringkasan Database
| Item | Detail |
|------|--------|
| Database | [PostgreSQL / MySQL / MongoDB / SQLite / Firebase / Supabase / ...] |
| ORM/Driver | [Prisma / Drizzle / Mongoose / SQLAlchemy / Firebase SDK / ...] |
| Pendekatan | [Relational / Document / Key-Value / Graph] |
| Alat Migrasi | [Prisma Migrate / Alembic / Flyway / manual] |

### Ikhtisar Entity
*Daftar entitas utama dari PRD, cukup field penting + relasi (detail kolom ditentukan saat implementasi):*

| Entity | Field Kunci | Relasi |
|--------|-----------|--------|
| [Entity 1] | id, [field_a], [field_b] | → Entity 2 (1:N) |
| [Entity 2] | id, entity_1_id, [field_c] | ← Entity 1, → Entity 3 |
| [Entity 3] | id, entity_2_id, [field_d] | ← Entity 2 |

### Strategi Indeks (jika relasional)
- **[entity_1].[field]** — pencarian berdasarkan [description]
- **[entity_2].[entity_1_id]** — indeks foreign key

### Alur Data
[Deskripsi bagaimana data mengalir antar entity, mis.:
"User membuat Order → Order memiliki OrderItem → setiap OrderItem merujuk ke Product"]
## 📄 BAGIAN 3: Desain Antarmuka

> Konten bagian ini otomatis menyesuaikan stack yang dipilih di FASE 2.
> AI lihat stack + PRD, tentukan bentuk antarmuka yang tepat, hasilkan secukupnya.
>
> - **Monolith (Laravel/Django/Rails)** → Route + Controller + View
> - **SPA + Backend API** → endpoint REST / GraphQL
> - **Next.js/SvelteKit/Remix** → Server Action / API Route
> - **HTMX** → endpoint HTML (kembalikan partial)
> - **Aplikasi mobile** → endpoint API
> - **Aplikasi desktop (Electron/Tauri)** → kanal IPC
> - **Static / Frontend-only** → BAGIAN 3 tidak diperlukan, lewati

=== DIHASILKAN OLEH AI BERDASARKAN PRD & STACK ===
| Method | Path / Aksi | Deskripsi | Auth |
|--------|---------------|-------------|------|
| [GET/POST/aksi] | [path / nama route / nama aksi] | [deskripsi dari PRD] | Ya/Tidak/N/A |

*Cukup tabel ringkas — detail request/response ditentukan saat implementasi.*

## 📄 BAGIAN 4: Alur Logika & Aturan Bisnis

> AI hasilkan alur dari PRD, format menyesuaikan arsitektur stack yang dipilih.
> Hanya buat alur untuk fitur yang benar-benar ada di PRD.
>
> - **Monolith** → User → Route → Controller → Model → View
> - **SPA + API** → User → Frontend → API → Backend → DB
> - **Serverless** → User → Client → Function → DB/Service
> - **Mobile / Desktop** → User → App → Service/API
>
> Alur auth hanya dibahas jika PRD menyebutkan fitur auth.
> Manajemen state sesuaikan frontend stack (React Query / Pinia / Vuex / Signals / Context / dll)

=== DIHASILKAN OLEH AI BERDASARKAN PRD & STACK ===

**Alur [Fitur 1 dari PRD]:**
1. [Langkah sesuai PRD]
2. [Langkah sesuai PRD]
3. [Langkah sesuai PRD]

**Alur [Fitur 2 dari PRD]:**
1. [Langkah sesuai PRD]
2. [Langkah sesuai PRD]

### Aturan Bisnis (dari PRD)
- [Aturan 1 dari PRD]
- [Aturan 2 dari PRD] 

## 📄 BAGIAN 5: Keamanan, Performa, & Deployment

> AI hasilkan konten berdasarkan stack + hosting yang dipilih di FASE 2.
> Hanya cantumkan item yang relevan — jangan copy-paste template.
>
> Contoh:
> - **Next.js + Vercel** → Vercel Analytics, Next.js Image, auto-deploy
> - **Laravel + DO** → Laravel Horizon, Supervisor, Redis, manual deploy
> - **FastAPI + Railway** → Uvicorn workers, Railway auto-deploy, Sentry
> - **Static site + Netlify** → Netlify deploy, lewati keamanan backend
> - **Electron desktop** → Auto-update, penyimpanan offline, lewati deployment

=== DIHASILKAN OLEH AI BERDASARKAN STACK & HOSTING ===

### Keamanan
- **[item relevan dari PRD + stack]**

### Performa
- **[item relevan dari PRD + stack]**

### Deployment
- **[item relevan dari stack + hosting]

### Penyiapan Pengembangan

```AI harus menghasilkan perintah setup sesuai framework yang dipilih user.```

Contoh:
- **Node.js/TypeScript** → `npm install && npm run dev`
- **Python/FastAPI** → `pip install -r requirements.txt && uvicorn app.main:app --reload`
- **Python/Django** → `pip install -r requirements.txt && python manage.py runserver`
- **Laravel** → `composer install && php artisan serve`
- **Go** → `go mod download && go run ./cmd/server`
- **Ruby on Rails** → `bundle install && rails server`
- **Stack lain** → sesuaikan dengan best practice framework

**🎉 Tech Spec selesai!**

## 🔄 Finalisasi

1. **Simpan file:**
   Simpan seluruh konten Tech Spec sebagai `.agents/2-TECH-SPEC.md`

2. **Lanjut ke Generator Task:**
   Ketik: `"Buat Task berdasarkan Tech Spec yang sudah dibuat"`
