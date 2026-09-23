# Panduan Content Points

Content Points adalah daftar informasi yang **wajib disampaikan** dalam satu section artikel. Ini adalah beban semantik outline — bukan instruksi untuk penulis.

Penulis yang menerima Content Points hanya melakukan *surface realization*: mengubah poin menjadi prosa yang natural. Penulis tidak mencari informasi, menentukan angle, menambahkan contoh, atau mengembangkan topik baru.

---

## Label Content Point

Setiap Content Point harus diberi label yang menunjukkan **hubungannya dengan poin sebelumnya dalam satu paragraf**:

| Label | Pertanyaan yang dijawab | Posisi |
|---|---|---|
| `[utama]` | Apa faktanya? Apa yang terjadi? | Selalu pertama |
| `[penjelas]` | Bagaimana cara kerjanya? Mengapa demikian? | Setelah `[utama]` |
| `[penguat]` | Seberapa besar? Apa buktinya? Apa contoh konkretnya? | Setelah `[utama]` atau `[penjelas]` |
| `[tambahan]` | Apa lagi yang relevan? (tanpa menjelaskan mekanisme atau memberi bukti) | Terakhir dalam grup |

**Cara membedakan keempat label — contoh satu paragraf lengkap:**

```
- [utama]    Trans Studio Bandung memiliki 20 wahana aktif di tujuh zona tematik.
- [penjelas] Setiap zona dirancang dengan tema visual berbeda sehingga pengunjung
             merasakan suasana yang berganti setiap kali berpindah area.
- [penguat]  Zona Hollywood dan Cartoon Network mencatat antrean rata-rata terpanjang
             berdasarkan data operasional 2024.
- [tambahan] Beberapa wahana memiliki batasan tinggi badan minimal untuk alasan keselamatan.
```

Penjelasan pilihan label:
- `[penjelas]` menjelaskan **mekanisme** (tema berbeda = suasana berbeda)
- `[penguat]` memberikan **data konkret** (nama zona + data antrean)
- `[tambahan]` menambahkan fakta terkait **tanpa** menjelaskan mekanisme atau membuktikan klaim utama

**Aturan label:**
- Setiap grup paragraf harus memiliki **tepat satu** `[utama]`
- `[utama]` selalu menjadi poin pertama dalam grup
- Tidak harus menggunakan keempat label — pilih yang paling tepat untuk informasi yang ada

---

## Aturan Koherensi Antar Poin (Wajib)

Setiap poin non-`[utama]` harus ditulis dengan kesadaran penuh terhadap poin sebelumnya — seolah poin sebelumnya sudah ada di layar dan poin ini melanjutkannya. Bukan menambahkan fakta baru yang berdiri sendiri, melainkan **meneruskan benang narasi** yang sudah dimulai.

**Cara menulis setiap label dengan benar:**

`[penjelas]` — tulis seolah kalimat `[utama]` baru saja dibaca. Kalimat ini menguraikan *mengapa* atau *bagaimana* klaim utama bekerja. Boleh pakai kata rujukan eksplisit ("Hal ini...", "Sistem ini...", "Kondisi tersebut...") atau urutan logis yang natural tanpa kata rujukan.

`[penguat]` — tulis seolah klaim atau penjelasan sebelumnya sudah ada. Kalimat ini memberikan angka, nama, atau bukti konkret. Jangan mengulang informasi dari `[utama]` — langsung ke buktinya.

`[tambahan]` — tulis seolah pembaca sudah tahu semua poin sebelumnya dalam grup ini. Kalimat ini melengkapi gambaran, bukan menjelaskan mekanisme atau memberikan bukti. Hindari memulai dengan fakta yang tidak terhubung ke poin-poin di atasnya.

**Contoh koherensi yang benar:**

```
- [utama]    Konsultan menyimpan database gedung yang jauh lebih luas
             daripada hasil pencarian mandiri lewat portal umum.
- [penguat]  SewaKantorCBD mencatat lebih dari 500 gedung, termasuk 225 gedung
             di CBD Jakarta dengan total ruang tersedia 7,8 juta m².
- [penjelas] Angka ini jauh melampaui apa yang muncul dari pencarian umum,
             dan datanya dikelompokkan per subarea sehingga perbandingan awal
             bisa dilakukan sebelum survei.
```

**Contoh koherensi yang salah (poin berdiri sendiri):**

```
- [utama]    Konsultan menyimpan database gedung yang lebih luas dari portal umum.
- [penguat]  SewaKantorCBD mencatat lebih dari 500 gedung di databasenya.
- [penjelas] Data gedung dikelompokkan berdasarkan subarea di Jakarta.
```

Poin kedua dan ketiga di contoh salah bisa dipindahkan atau dihapus tanpa merusak alur — tanda bahwa keduanya belum terhubung.

**Uji koherensi sebelum menyimpan grup:**
Baca seluruh grup dari atas ke bawah sebagai satu paragraf. Jika setiap poin bisa dipindahkan atau dihapus tanpa merusak alur bacaan poin-poin lainnya, poin tersebut belum cukup terhubung dan perlu ditulis ulang.

---

## Cara Menulis Poin Non-[utama]: Aware dengan Poin Sebelumnya

Setiap poin non-`[utama]` harus ditulis seolah-olah poin `[utama]` di atasnya sudah ada di layar. Poin berikutnya bukan fakta baru yang berdiri sendiri — melainkan kelanjutan dari apa yang baru saja diklaim.

**Dua cara koneksi yang valid:**

Koneksi eksplisit — pakai kata atau frasa rujukan yang langsung menunjuk ke poin sebelumnya: "Angka ini...", "Kondisi tersebut...", "Fitur ini...", "Hal itu...", "Dibandingkan dengan..."

Koneksi implisit — urutan fakta yang secara logis natural mengikuti poin sebelumnya. Valid selama pembaca secara instinktif tahu kedua kalimat membicarakan hal yang sama.

**Uji koherensi sebelum menyimpan:** Ambil dua poin berurutan. Bisa kah keduanya dipisah dan dipakai di paragraf berbeda tanpa kehilangan makna? Jika bisa — poin kedua terlalu mandiri dan harus ditulis ulang agar "melihat ke atas."

Salah — poin kedua berdiri sendiri:
```
**Paragraf 1**
- [utama] SewaKantorCBD mencatat lebih dari 500 gedung perkantoran di Jakarta.
- [penjelas] Data gedung dikelompokkan berdasarkan grade, harga, dan subarea.
```

Benar — poin kedua melanjutkan poin pertama:
```
**Paragraf 1**
- [utama] SewaKantorCBD mencatat lebih dari 500 gedung perkantoran di Jakarta.
- [penjelas] Data tersebut dikelompokkan berdasarkan grade, harga, dan subarea, sehingga perbandingan antargedung bisa dilakukan sebelum survei fisik.
```

---

## 6 Aturan Utama

### 1. Setiap Content Point Harus Konkret

Tulis sebagai informasi yang akan ditampilkan, bukan sebagai tugas untuk penulis.

**Dilarang:** jelaskan, bahas, uraikan, sebutkan, bandingkan, soroti.

| Salah | Benar |
|---|---|
| Jelaskan tinggi jok. | `[utama]` Tinggi jok 750 mm memudahkan kaki menjangkau tanah saat berhenti. |

### 2. Fakta Harus Disertai Maknanya

Jangan sajikan data mentah tanpa konteks.

| Salah | Benar |
|---|---|
| Tinggi jok: 750 mm | `[utama]` Tinggi jok 750 mm memudahkan kaki menjangkau tanah saat berhenti. |

### 3. Satu Makna Semantik per Poin

Pisahkan informasi kompleks ke poin yang berbeda.

**Kasus khusus — daftar item (fitur, opsi, langkah):**

Jika section berisi beberapa item bernama, jangan masukkan semuanya dalam satu poin. Sebagai gantinya:
1. Gunakan poin setelah `[utama]` untuk **menyebut dan memperkenalkan** kelompok item
2. Gunakan paragraf berikutnya untuk menjelaskan tiap item — satu grup per item atau per kluster logis

**Salah:**
```
**Paragraf 2**
- [utama]    Tiga fitur booster memperpendek jalur menyelesaikan puzzle.
- [penjelas] Invite Teman aktif saat pengguna baru selesaikan satu transfer;
             Oper Puzzle konversi kepingan duplikat jadi spin; Kejar Puzzle
             beri kepingan setelah lima transfer di hari Jumat.
```

**Benar:**
```
**Paragraf 2**
- [utama]    Tiga fitur booster memperpendek jalur: Invite Teman, Oper Puzzle,
             dan Kejar Puzzle.
- [tambahan] Masing-masing menarget perilaku transfer berbeda sehingga bisa
             dipakai sendiri atau dikombinasikan dalam satu minggu.

**Paragraf 3**
- [utama]    Invite Teman aktif saat pengguna yang diajak menyelesaikan
             setidaknya satu transfer; Oper Puzzle mengonversi kepingan
             duplikat menjadi spin melalui teman di level yang sama.
- [penguat]  Kejar Puzzle memberi kepingan tambahan setelah melakukan transfer
             ke lima pengguna berbeda di hari Jumat.
```

### 4. Selesaikan Analisis Sebelum Menulis

Selesaikan perbandingan, kalkulasi, dan implikasi sebelum menulis Content Point. Hanya sertakan perbandingan jika data dasarnya sudah terverifikasi.

### 5. Tidak Boleh Ada Informasi yang Dikarang

Content Points harus berdasarkan data yang diberikan atau riset yang telah dilakukan. Jika tidak bisa diverifikasi, jangan ditulis.

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
- [penjelas/penguat/tambahan] Melanjutkan dari poin di atas.

**Paragraf 2**
- [utama] Ide pokok paragraf kedua.
- [penjelas/penguat/tambahan] Melanjutkan dari poin di atas.
```
