# 🚀 Panduan Instalasi Skill Opencode

Jika Anda ingin menggunakan skill opencode ini, ikuti langkah-langkah berikut:

### Langkah 1: Mengambil Skill dari GitHub
Buka terminal dan jalankan perintah berikut:

```bash
git clone https://github.com/dirumahrafif/my-opencode-skills.git
```

### Langkah 2: Menyalin Folder Skill

**Untuk Pengguna Windows:**
1. Buka folder hasil clone melalui **File Explorer**.
2. Salin folder skill yang ingin dipasang.
3. Tekan `Windows + R`, ketik `%USERPROFILE%\.agents\skills\`, lalu tekan `Enter`.
4. Tempel (Paste) folder tersebut di sana.

**Untuk Pengguna Mac & Linux:**
1. Buka terminal dan masuk ke folder hasil clone.
2. Salin folder skill ke direktori konfigurasi opencode:
   ```bash
   cp -r my-opencode-skills/* ~/.agents/skills/
   ```

### Langkah 3: Mendaftarkan Skill di `opencode.json`
1. Buka file konfigurasi:
   - **Windows:** `%APPDATA%\opencode\opencode.json`
   - **Mac/Linux:** `~/.config/opencode/opencode.json`
2. Tambahkan path skill ke dalam `skills.paths`:
    ```json
    {
      "skills": {
        "paths": [
          "~/.agents/skills"
        ]
      }
    }
    ```

---
**Selesai!** Sekarang skill siap digunakan dengan memanggil *trigger keywords* yang ada di dalam `SKILL.md`.

