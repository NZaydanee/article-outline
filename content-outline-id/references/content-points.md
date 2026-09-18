# Panduan Content Points

Content Points adalah daftar informasi yang **wajib disampaikan** dalam satu section artikel. Ini adalah beban semantik outline — bukan instruksi untuk penulis.

Penulis yang menerima Content Points hanya melakukan *surface realization*: mengubah poin menjadi prosa yang natural dan mudah dibaca. Penulis tidak mencari informasi, menentukan angle, menambahkan contoh, atau mengembangkan topik baru.

---

## Label Content Point

Setiap Content Point harus diberi label yang menunjukkan fungsinya dalam paragraf:

| Label | Definisi | Posisi dalam paragraf |
|---|---|---|
| `[utama]` | Ide pokok paragraf; menjadi kalimat topik | Selalu pertama |
| `[penjelas]` | Menjelaskan atau menguraikan ide utama | Setelah `[utama]` |
| `[penguat]` | Memperkuat dengan data, angka, atau fakta spesifik | Setelah `[utama]` atau `[penjelas]` |
| `[tambahan]` | Informasi relevan yang melengkapi tanpa mengulang | Terakhir dalam grup |

**Aturan label:**
- Setiap grup paragraf harus memiliki **tepat satu** `[utama]`
- `[utama]` selalu menjadi poin pertama dalam grup
- Satu atau lebih label lain mengikuti setelah `[utama]`
- Urutan setelah `[utama]`: jelaskan dulu → perkuat dengan data → tambahkan konteks

---

## 6 Aturan Utama

### 1. Setiap Content Point Harus Konkret

Tulis sebagai informasi yang akan ditampilkan, bukan sebagai tugas untuk penulis.

**Dilarang:** jelaskan, bahas, uraikan, sebutkan, bandingkan, soroti.

| Salah | Benar |
|---|---|
| Jelaskan tinggi jok. | `[utama]` Tinggi jok 750 mm memudahkan kaki menjangkau tanah saat berhenti. |
| Bahas kenapa tangki 4,2 liter berguna. | `[penjelas]` Tangki 4,2 liter memberikan cadangan bahan bakar lebih besar sebelum harus mengisi ulang. |

### 2. Fakta Harus Disertai Maknanya

Jangan sajikan data mentah tanpa konteks.

| Salah | Benar |
|---|---|
| Tinggi jok: 750 mm | `[utama]` Tinggi jok 750 mm memudahkan kaki menjangkau tanah saat berhenti. |

### 3. Satu Makna Semantik per Poin

Pisahkan informasi kompleks ke poin yang berbeda.

**Salah:** Tinggi jok 750 mm dan bobot 95 kg membuat motor nyaman, mudah dikontrol, ramah pemula, praktis diparkir, dan ideal untuk perkotaan.

**Benar:**
- `[utama]` Tinggi jok 750 mm memudahkan kaki menjangkau tanah saat berhenti.
- `[penjelas]` Bobot 95 kg mendukung pengendalian saat manuver kecepatan rendah.

**Kasus khusus — daftar item (fitur, opsi, langkah):**

Jika section berisi beberapa item bernama, jangan masukkan semuanya dalam satu poin. Sebagai gantinya:
1. Gunakan poin setelah `[utama]` untuk **menyebut dan memperkenalkan** kelompok item.
2. Gunakan paragraf berikutnya untuk menjelaskan tiap item — satu grup paragraf per item atau per kluster logis.

**Salah:**
```
**Paragraf 2**
- [utama] Tiga fitur booster memperpendek jalur menyelesaikan puzzle.
- [penjelas] Invite Teman aktif saat pengguna baru selesaikan satu transfer; Oper Puzzle konversi kepingan duplikat jadi spin; Kejar Puzzle beri kepingan setelah lima transfer di hari Jumat.
```

**Benar:**
```
**Paragraf 2**
- [utama] Tiga fitur booster memperpendek jalur: Invite Teman, Oper Puzzle, dan Kejar Puzzle.
- [tambahan] Masing-masing menarget perilaku transfer berbeda sehingga bisa dipakai sendiri atau dikombinasikan.

**Paragraf 3**
- [utama] Invite Teman aktif saat pengguna yang diajak menyelesaikan setidaknya satu transfer; Oper Puzzle mengonversi kepingan duplikat menjadi spin Putar Roda melalui teman di level yang sama.
- [penguat] Kejar Puzzle memberi kepingan tambahan setelah melakukan transfer ke lima pengguna berbeda di hari Jumat.
```

### 4. Selesaikan Analisis Sebelum Menulis

Selesaikan perbandingan, kalkulasi, dan implikasi sebelum menulis Content Point. Hanya sertakan perbandingan jika data dasarnya sudah terverifikasi.

| Salah | Benar |
|---|---|
| Bandingkan kapasitas tangki dengan kompetitor. | `[penguat]` Tangki 4,2 liter lebih besar dari milik Kompetitor A yang 3,5 liter, memberikan tambahan kapasitas 0,7 liter. |

### 5. Tidak Boleh Ada Informasi yang Dikarang

Content Points harus berdasarkan data yang diberikan atau riset yang telah dilakukan. Jangan menutup celah riset dengan klaim yang terdengar masuk akal. Jika tidak bisa diverifikasi, jangan ditulis.

### 6. Label Angka Teoritis dan Hasil Kalkulasi

Gunakan klausa yang jelas jika angka bersifat teoritis, estimasi, atau hasil hitungan.

| Salah | Benar |
|---|---|
| Menempuh 1.000 km menghabiskan Rp250.000. | `[penguat]` Dengan harga bahan bakar Rp10.000/liter dan konsumsi teoritis 40 km/l, menempuh 1.000 km membutuhkan sekitar 25 liter atau sekitar Rp250.000. |

---

## Format Section (Non-Negotiable)

```
## [JUDUL SECTION]

**Paragraf 1**
- [utama] Ide pokok paragraf ini.
- [penjelas] Detail yang menguraikan ide utama.

**Paragraf 2**
- [utama] Ide pokok paragraf kedua.
- [penguat] Data atau fakta spesifik yang memperkuat.

**Paragraf 3** *(hanya jika budget paragraf memungkinkan)*
- [utama] Ide pokok paragraf ketiga.
- [tambahan] Informasi relevan yang melengkapi.
```
