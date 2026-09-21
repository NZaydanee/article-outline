# Panduan Struktur Content Outline

## Struktur Tingkat Tinggi

```
H1 Judul Artikel
│
├── Pendahuluan (Content Points berlabel)
│
├── ## H2 Section 1
│   └── Content Points (grup paragraf berlabel)
│
├── ## H2 Section 2
│   └── Content Points (grup paragraf berlabel)
│
├── [## H2 Mandatory Section — hanya jika mandatory berisi positive requirement]
│   └── Content Points (grup paragraf berlabel)
│
├── <kesimpulan>
│   └── Poin-poin kesimpulan
│
└── [## Heading CTA] atau [**CTA**]
    └── Content Points CTA
```

---

## Aturan Jumlah H2

| Kondisi | Aturan |
|---|---|
| Judul mengandung angka eksplisit | Angka itu adalah batas keras untuk H2 bernomor |
| Judul tidak mengandung angka | Tentukan jumlah logis berdasarkan cakupan semantik |

- Pendahuluan, mandatory section, dan CTA **tidak dihitung** dalam total bernomor
- Satu poin tidak boleh dipecah ke beberapa H2
- Jangan tambahkan section bonus, tips, atau tambahan kecuali `brief` memintanya secara eksplisit
- Untuk menambah kedalaman tanpa menambah H2: tambahkan grup paragraf di dalam section yang sudah ada

---

## Jenis Section

### Pendahuluan

**Jumlah paragraf:** 2–3 grup, masing-masing 1 `[utama]` + 1 atau lebih label lain.

| Paragraf | Peran |
|---|---|
| Pertama | Konteks luas yang relevan dengan topik umum |
| Kedua | Konteks lebih sempit, fokus ke topik spesifik artikel |
| Ketiga | Jembatan yang mengarahkan pembaca ke isi utama |

Anchor text 1 ditebalkan dan muncul natural di pendahuluan. Anchor text 2 muncul natural di paragraf yang sama atau berdekatan.

---

### H2 Section (Standard)

Jumlah paragraf ditentukan oleh budget dari Langkah 6b di SKILL.md.

Setiap grup paragraf mengikuti format:
```
**Paragraf N**
- [utama] Ide pokok.
- [penjelas/penguat/tambahan] Elaborasi.
```

---

### Mandatory Section

Hanya ada jika kolom `mandatory` berisi **positive requirement** (nama produk atau topik yang harus dibahas).

Jumlah paragraf mengikuti budget yang sama dengan section biasa (Langkah 6b).

Konten fokus pada:
- Paragraf pertama: konteks produk dan spesifikasi utama
- Paragraf berikutnya: USP dan keunggulan teknis yang relevan

---

### Kesimpulan

Tidak pakai H2. Dibungkus dalam tag `<kesimpulan>...</kesimpulan>`.

```
<kesimpulan>
- Poin kesimpulan pertama.
- Poin kesimpulan kedua.
- Poin kesimpulan ketiga.
</kesimpulan>
```

2–3 poin yang merangkum takeaway utama. Tidak ada informasi baru.

---

### CTA Section

Heading ditentukan oleh jawaban user di Langkah 1 (`heading_cta`):

- **User memberikan teks heading** → gunakan verbatim sebagai H2 di setiap baris
- **User memilih tanpa H2** → gunakan label `**CTA**` (tanpa `##`)

**Format dengan H2:**
```
## [Teks heading dari user]

**Content Points:**
- Narrative bridge: [satu kalimat yang menghubungkan kesimpulan ke produk]
- [Poin produk/layanan sebagai solusi]
- [Poin aksi — URL, WhatsApp, email, dll.]
```

**Format tanpa H2:**
```
**CTA**

**Content Points:**
- Narrative bridge: [satu kalimat yang menghubungkan kesimpulan ke produk]
- [Poin produk/layanan sebagai solusi]
- [Poin aksi — URL, WhatsApp, email, dll.]
```
