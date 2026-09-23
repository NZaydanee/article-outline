---
name: content-outline-id
description: Buat content outline terstruktur dari tabel input (TSV atau Markdown) dengan kolom: id, anchor text 1, anchor text 2, brief, mandatory, title, source. Gunakan skill ini ketika user menempel tabel artikel dan meminta content outline, content brief, article blueprint, atau panduan penulisan. Trigger juga ketika user menyebut "content outline", "article outline", atau "content points" bersamaan dengan input terstruktur.
---

# Content Outline Generator — Bahasa Indonesia

Menghasilkan satu file content outline per baris tabel. Setiap file berisi Content Points berlabel yang sudah siap digunakan writing agent.

**Bahasa output:** Bahasa Indonesia  
**Format nama file:** `{id} - {anchor text 1}.md`

---

## Langkah 1: Pengaturan Batch

Sebelum membaca tabel, tanyakan dua hal dalam satu pesan:

> "Sebelum mulai, dua pengaturan cepat:
>
> 1. **Target jumlah kata per artikel?** (Default: 700 kata)
> 2. **Heading CTA?**
>    - **Tanpa H2** — CTA tampil sebagai paragraf biasa setelah kesimpulan
>    - **Dengan H2** — berikan teks heading yang diinginkan"

Tunggu satu jawaban, lalu simpan sebagai `target_kata` dan `heading_cta`.

---

## Langkah 2: Baca Reference Files dan Semua Baris

Baca dua reference files berikut **sekali** sebelum memproses baris manapun:
- `references/content-points.md` — aturan Content Points, definisi label, aturan koherensi, format
- `references/structure.md` — definisi section, aturan jumlah H2, aturan anti-template pendahuluan

Simpan isinya dalam konteks — tidak perlu dibaca ulang untuk setiap baris.

Kemudian baca seluruh tabel dan catat secara internal:
- Baris mana yang kolom `source`-nya kosong dan tidak ada data dari user
- Data apa yang dibutuhkan setiap baris berdasarkan topiknya
- Anomali tabel (kolom bergeser, judul kosong, field hilang)

Jangan output apapun di tahap ini.

---

## Langkah 3: Pre-Batch Clearance — Satu Pesan, Tanpa Pengecualian

**Tidak ada baris yang boleh ditulis sebelum langkah ini selesai.**

Jalankan dua pengecekan sekaligus. Gabungkan semua temuan dalam satu pesan. Jangan mulai batch sebelum user mengkonfirmasi semua masalah terselesaikan.

### Cek A — Sumber Data

Identifikasi baris dengan `source` kosong dan tidak ada data dari user:

> **Baris tanpa data sumber:** Baris X *(judul)*, Baris Y *(judul)*
> - **A** — Aku riset semua via web search
> - **B** — Kamu akan berikan semua data sekarang
> - **C** — Campuran: sebutkan mana yang kamu sediakan, sisanya aku riset

### Cek B — Kesesuaian Data dengan Topik

Periksa apakah data yang tersedia mencakup klaim yang dibutuhkan topik.

| Tipe topik | Data yang harus ada di sumber |
|---|---|
| Pendinginan / performa termal | TDP (watt), nama sistem pendingin, konfigurasi kipas |
| Kualitas build / material | Nama material, proses treatment, hasil uji ketahanan |
| Fitur keamanan | Nama fitur spesifik, nama sertifikasi |
| Fitur AI | Ada/tidaknya NPU, rating TOPS, nama fitur AI |
| Baterai / ketahanan | Kapasitas baterai (Wh), klaim durasi penggunaan |
| Harga | Angka harga aktual untuk pasar yang dibahas |
| Garansi / purna jual | Durasi garansi, cakupan, jenis layanan |

**Aturan penggabungan:** Cek A dan Cek B selalu digabung dalam satu pesan.

---

## Langkah 4: Tentukan Sumber Data Per Baris

| Prioritas | Kondisi | Tindakan |
|---|---|---|
| 1 | User menempel data di pesan yang sama dengan tabel | Gunakan sebagai satu-satunya referensi |
| 2 | Kolom `source` berisi konten (URL, markdown, JSON, teks) | Gunakan sebagai referensi utama |
| 3 | `source` kosong | Gunakan hasil web search atau data dari jawaban Langkah 3 |

---

## Langkah 5: Proses Baris Satu per Satu (Stateless)

Setiap baris adalah unit independen sepenuhnya. Tidak ada aturan, data, atau constraint dari satu baris yang boleh terbawa ke baris lain.

---

## Langkah 6: Susun Content Outline

Gunakan pemahaman dari reference files yang sudah dibaca di Langkah 2.

### 6a. Tentukan Jumlah H2 dari Judul

- Judul mengandung angka eksplisit → angka itu adalah batas keras
- Judul tidak mengandung angka → tentukan secara logis dari cakupan semantik

### 6b. Hitung Budget Paragraf per Section

```
kata_tersedia        = target_kata - 150
budget_per_section   = kata_tersedia ÷ jumlah_H2
paragraf_per_section = maks(2, bulatkan(budget_per_section ÷ 55))
```

| target_kata | 4 H2 | 5 H2 | 6 H2 |
|---|---|---|---|
| 700 | 2–3 paragraf | 2 paragraf | 2 paragraf |
| 900 | 3 paragraf | 2–3 paragraf | 2 paragraf |
| 1100 | 3–4 paragraf | 3 paragraf | 2–3 paragraf |

Rumus yang sama berlaku untuk mandatory section.

### 6c. Baca Brief dan Mandatory

| Isi kolom `mandatory` | Tindakan |
|---|---|
| Nama produk atau topik yang wajib dibahas | Buat H2 mandatory section di body artikel |
| Hanya restriction | Tidak ada H2 mandatory. Promosi produk masuk CTA saja. |
| Kosong | Tidak ada mandatory section |

### 6d. Selesaikan Kalkulasi Sebelum Menulis

Selesaikan semua perbandingan, kalkulasi, dan implikasi sebelum Content Point apapun ditulis.

### 6e. Struktur Output

```
H1 Judul Artikel

Pendahuluan
  Content Points (berlabel, anti-template)

## H2 Section 1
  Content Points (berlabel, koheren)

## H2 Section 2
  Content Points (berlabel, koheren)

[## H2 Mandatory Section]
  Content Points (berlabel, koheren)

<kesimpulan>
- Poin kesimpulan
</kesimpulan>

[## Heading CTA] atau [**CTA**]
Content Points CTA
```

---

## Langkah 7: Checklist Internal Sebelum Menyimpan

- [ ] Tidak ada blok metadata, catatan teknis, atau header tambahan di luar struktur output
- [ ] Anchor text 1 muncul natural di pendahuluan dan ditebalkan
- [ ] Anchor text 2 muncul natural di pendahuluan
- [ ] Setiap `[utama]` di pendahuluan lolos uji anti-template
- [ ] Semua instruksi di `brief` dan `mandatory` sudah dipenuhi
- [ ] Jumlah H2 sesuai aturan Langkah 6a
- [ ] Jumlah paragraf per section sesuai budget Langkah 6b
- [ ] Setiap grup paragraf punya tepat satu `[utama]` di posisi pertama
- [ ] Setiap poin non-`[utama]` ditulis dengan kesadaran poin sebelumnya
- [ ] Setiap angka atau klaim punya sumber; tidak ada yang dikarang
- [ ] Tidak ada aturan atau data dari baris lain yang ikut terbawa
- [ ] File bisa dipahami penulis yang belum pernah melihat tabel aslinya
- [ ] File tidak mengandung blok Metadata, Catatan untuk Penulis, atau ringkasan teknis apapun — output hanya berisi konten outline

---

## Larangan Output

Jangan sertakan blok metadata, catatan untuk penulis, atau ringkasan parameter teknis (seperti ID, target kata, jumlah H2, heading CTA) dalam output. File yang dihasilkan hanya boleh berisi content outline — mulai dari judul H1 hingga CTA.

---

## Langkah 8: Simpan dan Sajikan

Simpan file sebagai `{id} - {anchor text 1}.md`, sajikan ke user, lalu lanjut ke baris berikutnya.
