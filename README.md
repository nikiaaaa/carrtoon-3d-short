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

```bash
# 1. Skill
git clone https://github.com/nikiaaaa/carrtoon-3d-short ~/.claude/skills/cartoon-3d-short

# 2. Template dan referensi dari proyek aslinya, taruh di folder skill yang sama
git clone https://github.com/mromidev/claude-animated-shorts /tmp/claude-animated-shorts
cp -r /tmp/claude-animated-shorts/templates /tmp/claude-animated-shorts/references ~/.claude/skills/cartoon-3d-short/
```

Kebutuhan: Node, Remotion dengan `@remotion/three`, Python 3, ffmpeg, dan drive besar untuk folder sementara (tiap bundle Remotion menyalin `public/` sekitar 1,3 GB).

Panggil dengan `/cartoon-3d-short` di Claude Code.

## Catatan

- Video referensi yang dipelajari bersifat privat. Jangan diunggah atau dipublikasikan, dan jangan menyalin naskah, karakter, atau shot-nya.
- Cerita, karakter, dan suara harus orisinal.

## Lisensi

Isi repo ini diturunkan dari proyek berlisensi **MIT**. Lihat [NOTICE.md](NOTICE.md) untuk atribusi dan ketentuan lengkapnya.
