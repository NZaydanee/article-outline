# Content Outline Skill

Skill untuk menghasilkan content outline.
## Dua Varian

| Folder | Bahasa Output | Dipakai dengan |
|---|---|---|
| `content-outline-id/` | Bahasa Indonesia | Writing agent berbahasa Indonesia |
| `content-outline-en/` | English | Writing agent berbahasa Inggris |

Kedua varian menggunakan logika workflow yang sama. Perbedaannya hanya pada bahasa output Content Points, label paragraf, dan judul section.

## Struktur

```
content-outline-id/
├── SKILL.md
└── references/
    ├── content-points.md
    ├── structure.md
    └── examples.md

content-outline-en/
├── SKILL.md
└── references/
    ├── content-points.md
    ├── structure.md
    └── examples.md
```

## Input

Tabel dengan kolom: `id`, `anchor text 1`, `anchor text 2`, `brief`, `mandatory`, `title`, `source`

## Output

Satu file `.md` per baris. 
