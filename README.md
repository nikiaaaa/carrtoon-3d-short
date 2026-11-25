# 🧊 Cartoon 3D Short

> **EN:** A Claude skill for making a ~55-70 s vertical cartoon story short: 2D bean-head characters in a colourful 3D world, voice narration, synthesized SFX and music, rendered with three.js inside Remotion. This repo packages the skill; it is based on the MIT-licensed project [claude-animated-shorts](https://github.com/mromidev/claude-animated-shorts) (see [NOTICE.md](NOTICE.md)).

Skill untuk Claude yang membuat **short cerita kartun vertikal** sekitar 55-70 detik: karakter 2D berkepala bean di dunia 3D berwarna, narasi suara, SFX dan musik sintesis, dirender dengan three.js di dalam Remotion.

Pasangan skill ini adalah [`cartoon-short-director`](https://github.com/nikiaaaa/cartoon-short-director), yang menulis ide, naskah, rencana scene, dan prompt per scene.

## Isi repo

| File | Fungsi |
|---|---|
| `SKILL.md` | Instruksi skill: pipeline 11 langkah, nilai tampilan akhir, target look, gotchas, dan jebakan keterbacaan |
| `NOTICE.md` | Atribusi dan status lisensi |

**Penting:** folder `templates/` (kode Remotion, audio, script bantu) dan `references/` **tidak** ikut di repo ini. Ambil dari proyek aslinya: [mromidev/claude-animated-shorts](https://github.com/mromidev/claude-animated-shorts).

## Cara pasang

Ada dua bagian: **skill** (repo ini) dan **template render** (dari proyek aslinya).

### Yang harus ada dulu

| Alat | Cek dengan | Keterangan |
|---|---|---|
| Git | `git --version` | https://git-scm.com |
| Node.js | `node --version` | https://nodejs.org (versi LTS) |
| Python 3 | `python --version` (atau `python3 --version`) | https://python.org |
| ffmpeg | `ffmpeg -version` | https://ffmpeg.org |
| Ruang disk | n/a | Sediakan drive dengan puluhan GB kosong. Tiap bundle Remotion menyalin `public/` (sekitar 1,3 GB) ke folder sementara |

### Cara termudah: minta Claude yang memasang

Buka Claude Code, lalu tempel prompt ini:

```
Pasang skill cartoon-3d-short untuk saya:
1. Clone https://github.com/nikiaaaa/carrtoon-3d-short ke ~/.claude/skills/cartoon-3d-short
   (Windows: %USERPROFILE%\.claude\skills\cartoon-3d-short). Kalau sudah ada, jalankan git pull.
2. Clone https://github.com/mromidev/claude-animated-shorts ke folder sementara, lalu salin
   folder templates/ dan references/ ke dalam folder skill di atas.
3. Cek apakah git, node, python, dan ffmpeg terpasang. Beri tahu saya yang belum ada dan cara memasangnya.
4. Cek SKILL.md, templates/, dan references/ ada di folder skill, lalu laporkan hasilnya.
Jangan menghapus folder apa pun tanpa bertanya dulu.
```

### Manual

macOS / Linux / Git Bash:

```bash
# 1. Skill
git clone https://github.com/nikiaaaa/carrtoon-3d-short ~/.claude/skills/cartoon-3d-short

# 2. Template dan referensi dari proyek aslinya
git clone https://github.com/mromidev/claude-animated-shorts /tmp/claude-animated-shorts
cp -r /tmp/claude-animated-shorts/templates /tmp/claude-animated-shorts/references ~/.claude/skills/cartoon-3d-short/
```

Windows (PowerShell):

```powershell
# 1. Skill
git clone https://github.com/nikiaaaa/carrtoon-3d-short "$env:USERPROFILE\.claude\skills\cartoon-3d-short"

# 2. Template dan referensi dari proyek aslinya
git clone https://github.com/mromidev/claude-animated-shorts "$env:TEMP\claude-animated-shorts"
Copy-Item -Recurse "$env:TEMP\claude-animated-shorts\templates" "$env:USERPROFILE\.claude\skills\cartoon-3d-short\"
Copy-Item -Recurse "$env:TEMP\claude-animated-shorts\references" "$env:USERPROFILE\.claude\skills\cartoon-3d-short\"
```

Memperbarui nanti: `git pull` di folder skill. Folder `templates/` dan `references/` yang kamu salin tidak ikut ter-update, jadi salin ulang bila proyek aslinya berubah.

### Cek berhasil

1. Folder `~/.claude/skills/cartoon-3d-short/` berisi `SKILL.md`, `templates/`, dan `references/`.
2. Buka sesi Claude Code baru, ketik `/cartoon-3d-short`. Kalau skill muncul dan Claude mulai membahas topik, naskah, atau pipeline, pemasangan berhasil.

### Pemakaian pertama

Paling mudah lewat skill pasangan [`cartoon-short-director`](https://github.com/nikiaaaa/cartoon-short-director): ia menulis ide, naskah, rencana scene, dan prompt per scene yang bisa langsung ditempel ke skill ini. Bisa juga langsung:

```
/cartoon-3d-short Buat short 60 detik dari naskah di SCRIPT.md. Mulai dari tahap 1.
```

### Kalau tidak jalan

| Masalah | Solusi |
|---|---|
| `/cartoon-3d-short` tidak muncul | Pastikan `SKILL.md` ada di `~/.claude/skills/cartoon-3d-short/`, lalu mulai sesi Claude Code baru |
| Claude bilang `templates/` tidak ditemukan | Ulangi langkah 2 (salin `templates/` dan `references/` dari proyek aslinya) |
| Disk penuh saat render | Atur `TEMP` dan `TMP` ke drive besar, dan hapus folder `remotion-webpack-bundle-*` lama setelah proyek selesai |
| Path Windows rusak di script | Tulis path dengan `/` di string JS, bukan `\` (karena `\r` dibaca sebagai carriage return) |
| File video hasil render tanpa suara | Gabungkan audio dengan `ffmpeg -map 0:v:0 -map 1:a:0`, karena Remotion menulis track audio kosong |

### Catatan untuk asisten AI

Kalau kamu AI yang membantu pengguna memasang repo ini: (1) clone repo ini ke folder skill pengguna, (2) ambil `templates/` dan `references/` dari `mromidev/claude-animated-shorts` dan salin ke folder yang sama, (3) cek `git`, `node`, `python`, `ffmpeg`, (4) verifikasi `SKILL.md`, `templates/`, `references/` ada. Jangan menghapus folder `remotion-webpack-bundle-*` tanpa izin pengguna. Jangan mengunggah atau mengutip materi di `references/`, karena itu bahan studi pribadi. Ikuti lisensi proyek asli (lihat [NOTICE.md](NOTICE.md)).

## Catatan

- Video referensi yang dipelajari bersifat privat. Jangan diunggah atau dipublikasikan, dan jangan menyalin naskah, karakter, atau shot-nya.
- Cerita, karakter, dan suara harus orisinal.

## Lisensi

Isi repo ini diturunkan dari proyek berlisensi **MIT**. Lihat [NOTICE.md](NOTICE.md) untuk atribusi dan ketentuan lengkapnya.
