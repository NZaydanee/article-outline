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

---

## Jenis Section

### Pendahuluan

**Jumlah paragraf:** 2–3 grup, masing-masing 1 `[utama]` + 1 atau lebih label lain.

Pendahuluan tidak punya peran yang dikunci per paragraf. Kontennya ditentukan oleh fakta yang tersedia di source untuk artikel ini — bukan oleh template kategori.

**Aturan anti-template (wajib dipatuhi):**

Setiap `[utama]` di pendahuluan harus lolos uji ini: *apakah kalimat ini bisa dipindahkan ke artikel lain dalam topik yang sama tanpa mengubah maknanya?* Jika bisa → kalimat itu terlalu generik dan harus diganti dengan fakta spesifik dari source.

Dilarang — kalimat yang bisa dipakai di artikel manapun dalam kategori yang sama:
- "Wahana indoor menjadi pilihan favorit keluarga Indonesia untuk berlibur tanpa bergantung cuaca."
- "Jakarta punya banyak pilihan tempat wisata keluarga, namun tidak semuanya bertahan populer."
- "Smartphone flagship modern menawarkan spesifikasi yang semakin kompetitif setiap tahunnya."

Yang benar — fakta spesifik yang hanya berlaku untuk subjek artikel ini:
- Nama spesifik, angka, tanggal, harga, atau keunikan yang tidak bisa dipindahkan ke artikel lain
- Contoh: "Trans Studio Bandung mengoperasikan 20 wahana aktif di tujuh zona tematik dalam satu gedung."
- Contoh: "Okupansi perkantoran CBD Jakarta tercatat 76% pada kuartal II 2026 menurut riset Colliers Indonesia."

**Aturan anchor text:**
- Anchor text 1 ditebalkan dan muncul natural di pendahuluan
- Anchor text 2 muncul natural di paragraf yang sama atau berdekatan
- Penempatan anchor text tidak boleh memaksa kalimat menjadi generik

---

### H2 Section (Standard)

Jumlah paragraf ditentukan oleh budget dari Langkah 6b di SKILL.md.

Setiap grup paragraf mengikuti format dan aturan koherensi di `content-points.md`.

---

### Mandatory Section

Hanya ada jika kolom `mandatory` berisi **positive requirement** (nama produk atau topik yang harus dibahas).

Jumlah paragraf mengikuti budget yang sama dengan section biasa.

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
