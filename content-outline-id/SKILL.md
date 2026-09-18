---
name: content-outline-id
description: Buat content outline terstruktur dari tabel input (TSV atau Markdown) dengan kolom: id, anchor text 1, anchor text 2, brief, mandatory, title, source. Gunakan skill ini ketika user menempel tabel artikel dan meminta content outline, content brief, article blueprint, atau panduan penulisan. Trigger juga ketika user menyebut "content outline", "article outline", atau "content points" bersamaan dengan input terstruktur. Trigger bahkan jika user hanya menempel tabel tanpa instruksi eksplisit — kehadiran kolom-kolom ini sudah cukup.
---

# Content Outline Generator — Bahasa Indonesia

Menghasilkan satu file content outline per baris tabel. Setiap file berisi Content Points berlabel yang sudah siap digunakan writing agent untuk menulis artikel.

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
>    - **Dengan H2** — berikan teks heading yang diinginkan (misalnya: *"Temukan AIS Receiver di IAPS"*)"

Tunggu satu jawaban, lalu:
- Simpan jumlah kata sebagai `target_kata`. Default **700** jika tidak disebutkan.
- Simpan preferensi CTA sebagai `heading_cta`. Jika user memberikan teks heading, gunakan verbatim di setiap baris. Jika tanpa H2, format CTA sebagai paragraf biasa dengan label `**CTA**` (tanpa `##`) di outline.

---

## Langkah 2: Baca Semua Baris

Baca seluruh tabel. Catat secara internal:
- Baris mana yang kolom `source`-nya kosong dan tidak ada data dari user
- Data apa yang dibutuhkan setiap baris berdasarkan topiknya
- Anomali tabel (kolom bergeser, judul kosong, field hilang)

Jangan output apapun di tahap ini.

---

## Langkah 3: Pre-Batch Clearance — Satu Pesan, Tanpa Pengecualian

**Tidak ada baris yang boleh ditulis sebelum langkah ini selesai.**

Jalankan dua pengecekan sekaligus di seluruh baris. Gabungkan semua temuan dalam satu pesan. Jangan mulai batch sebelum user mengkonfirmasi semua masalah telah terselesaikan.

### Cek A — Sumber Data

Identifikasi baris dengan `source` kosong dan tidak ada data dari user. Tanyakan sekaligus:

> **Baris tanpa data sumber:** Baris X *(judul)*, Baris Y *(judul)*
>
> Pilih salah satu:
> - **A** — Aku riset semua via web search
> - **B** — Kamu akan berikan semua data sekarang (paste di sini)
> - **C** — Campuran: sebutkan mana yang kamu sediakan, sisanya aku riset

### Cek B — Kesesuaian Data dengan Topik

Untuk baris yang sudah punya sumber, periksa apakah datanya mencakup klaim yang dibutuhkan topik. Tandai baris jika topik membutuhkan data yang tidak ada di sumber.

| Tipe topik | Data yang harus ada di sumber |
|---|---|
| Pendinginan / performa termal | TDP (watt), nama sistem pendingin, konfigurasi kipas |
| Kualitas build / material | Nama material, proses treatment, hasil uji ketahanan |
| Fitur keamanan | Nama fitur spesifik, nama sertifikasi |
| Fitur AI | Ada/tidaknya NPU, rating TOPS, nama fitur AI |
| Baterai / ketahanan | Kapasitas baterai (Wh), klaim durasi penggunaan |
| Harga | Angka harga aktual untuk pasar yang dibahas |
| Garansi / purna jual | Durasi garansi, cakupan, jenis layanan |

Jika ada baris yang ditandai, tanyakan per baris yang bermasalah: sediakan data / riset / skip dengan catatan gap di file.

**Aturan penggabungan:** Cek A dan Cek B digabung dalam satu pesan — tidak pernah dua pesan terpisah.

---

## Langkah 4: Tentukan Sumber Data Per Baris

| Prioritas | Kondisi | Tindakan |
|---|---|---|
| 1 | User menempel data di pesan yang sama dengan tabel | Gunakan sebagai satu-satunya referensi. Tidak boleh ditambah dari luar. |
| 2 | Kolom `source` berisi konten (URL, markdown, JSON, teks biasa) | Gunakan sebagai referensi utama. Tidak boleh dilengkapi dari luar. |
| 3 | `source` kosong | Gunakan hasil web search atau data dari jawaban Langkah 3. |

Jika `source` berisi URL, fetch halamannya. Jika markdown/JSON/teks biasa, gunakan apa adanya.

---

## Langkah 5: Proses Baris Satu per Satu (Stateless)

Setiap baris adalah unit independen sepenuhnya.
- Selesaikan satu baris sebelum mulai baris berikutnya
- Tidak ada aturan, data, atau constraint dari satu baris yang boleh terbawa ke baris lain
- Tulis semua konteks yang dibutuhkan lengkap di dalam file baris itu sendiri
- Dilarang menulis rujukan silang seperti "sama seperti baris 3"

---

## Langkah 6: Susun Content Outline

Sebelum menulis setiap baris, baca:
- `references/content-points.md` — aturan penulisan Content Points, definisi label, format
- `references/structure.md` — definisi section, aturan jumlah H2, struktur paragraf
- `references/examples.md` — contoh output lengkap

### 6a. Tentukan Jumlah H2 dari Judul

- Judul mengandung angka eksplisit (misal "5 Alasan", "7 Kriteria") → angka itu adalah batas keras. Jumlah H2 bernomor harus tepat sama.
- Judul tidak mengandung angka → tentukan jumlah H2 berdasarkan cakupan semantik dan pengelompokan topik secara logis.

Jumlah H2 tidak berubah berdasarkan jumlah kata.

### 6b. Hitung Budget Paragraf per Section

```
kata_tersedia    = target_kata - 150
budget_per_section = kata_tersedia ÷ jumlah_H2
paragraf_per_section = maks(2, bulatkan(budget_per_section ÷ 55))
```

Di mana 150 = estimasi kata untuk pendahuluan + CTA, dan 55 = estimasi kata per paragraf.

Referensi cepat:

| target_kata | 4 H2 | 5 H2 | 6 H2 |
|---|---|---|---|
| 700 | 2–3 paragraf | 2 paragraf | 2 paragraf |
| 900 | 3 paragraf | 2–3 paragraf | 2 paragraf |
| 1100 | 3–4 paragraf | 3 paragraf | 2–3 paragraf |

Setiap paragraf = 1 `[utama]` + 1 atau lebih label lain. Rumus yang sama berlaku untuk mandatory section.

### 6c. Baca Brief dan Mandatory

| Isi kolom `mandatory` | Tindakan |
|---|---|
| Nama produk atau topik yang wajib dibahas (positive requirement) | Buat H2 mandatory section di body artikel |
| Hanya restriction (misal "Jangan sebut kompetitor X") | Tidak ada H2 mandatory. Restriction berlaku global. Promosi produk masuk CTA saja. |
| Kosong | Tidak ada mandatory section |

Jika `brief` menyebut promosi produk tapi `mandatory` hanya berisi restriction: promosi masuk **CTA saja**.

### 6d. Selesaikan Kalkulasi Sebelum Menulis

Selesaikan semua perbandingan, kalkulasi, dan implikasi sebelum Content Point apapun ditulis. Beri label jelas pada angka teoritis atau hasil estimasi.

### 6e. Struktur Output

```
H1 Judul Artikel

Pendahuluan
  Content Points (berlabel)

## H2 Section 1
  Content Points (berlabel, per grup paragraf)

## H2 Section 2
  Content Points (berlabel, per grup paragraf)

[## H2 Mandatory Section — hanya jika mandatory berisi positive requirement]
  Content Points (berlabel, per grup paragraf)

<kesimpulan>
- Poin kesimpulan
- Poin kesimpulan
</kesimpulan>

[## Heading CTA dari user] atau [**CTA** tanpa heading]
Content Points CTA
```

---

## Langkah 7: Checklist Internal Sebelum Menyimpan

Jalankan diam-diam sebelum menyimpan setiap file:

- [ ] Anchor text 1 muncul natural di pendahuluan dan ditebalkan
- [ ] Anchor text 2 muncul natural di pendahuluan
- [ ] Semua instruksi di `brief` dan `mandatory` sudah dipenuhi
- [ ] Jumlah H2 sesuai aturan Langkah 6a
- [ ] Jumlah paragraf per section sesuai budget Langkah 6b
- [ ] Setiap grup paragraf punya tepat satu `[utama]` di posisi pertama
- [ ] Setiap angka atau klaim punya sumber; tidak ada yang dikarang
- [ ] Tidak ada aturan, data, atau constraint dari baris lain yang ikut terbawa
- [ ] Tidak ada rujukan silang ke baris lain
- [ ] File bisa dipahami penulis yang belum pernah melihat tabel aslinya

---

## Langkah 8: Simpan dan Sajikan

Simpan file sebagai `{id} - {anchor text 1}.md`, sajikan ke user, lalu lanjut ke baris berikutnya.
