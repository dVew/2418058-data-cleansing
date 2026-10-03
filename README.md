# Data Cleansing dan Data Enrichment: Dataset Lagu

Tugas Studi Kasus Mata Kuliah Data Mining (Pertemuan 4)

Nama: David Andrew Gregorius Tingang Liah
NIM: 2418058
Kelas: A

## Deskripsi Project

Project ini membersihkan (data cleansing) dan memperkaya (data enrichment) dataset lagu populer yang berisi 35 baris. Dataset disusun sendiri dalam bentuk CSV, jadi nilai jumlah putar, popularitas, durasi, dan tanggal rilis adalah data contoh untuk latihan, bukan angka resmi dari platform musik. Datanya sengaja dibuat berisi masalah kualitas data supaya berbagai teknik cleansing bisa dipraktikkan.

Seluruh proses dikerjakan dengan Python (pandas, numpy, matplotlib) di Google Colab.

## Isi Repository

| File | Keterangan |
|---|---|
| `2418058DataCleansing.ipynb` | Notebook lengkap: pemahaman data, identifikasi masalah, cleansing, enrichment, perbandingan sebelum dan sesudah |
| `dataset_musik_mentah.csv` | Dataset asli sebelum dibersihkan (35 baris, 9 kolom) |
| `dataset_musik_bersih.csv` | Dataset hasil cleansing dan enrichment (33 baris, 18 kolom) |
| `README.md` | Dokumentasi project ini |

## Kolom Dataset Mentah

| Kolom | Keterangan |
|---|---|
| id_lagu | nomor identitas lagu |
| judul | judul lagu |
| artis | nama artis atau band |
| genre | genre lagu |
| tahun_rilis | tahun rilis |
| tanggal_rilis | tanggal rilis |
| durasi | lama lagu (menit:detik atau detik) |
| jumlah_putar | jumlah pemutaran (streaming) |
| popularitas | skor popularitas (0 sampai 100) |

## Masalah Kualitas Data yang Ditemukan

| Jenis masalah | Detail |
|---|---|
| Missing value | 6 sel kosong (genre, tahun_rilis, tanggal_rilis, jumlah_putar, popularitas) |
| Data duplikat | 2 baris (1 persis sama, 1 beda huruf besar/kecil dan spasi) |
| Inkonsistensi format | genre ditulis 14 cara untuk 8 genre; durasi campur menit:detik dan detik; tanggal memakai 3 format |
| Inkonsistensi teks | judul dan artis ada yang huruf besar semua atau kecil semua, ada spasi berlebih |
| Kesalahan tipe data | jumlah_putar, durasi, dan tanggal_rilis terbaca sebagai teks |
| Data tidak valid | popularitas -5 dan 150, tahun rilis 2035, jumlah putar negatif, durasi 0:00, tanggal 31/02 |
| Outlier | durasi 58:20 dan jumlah putar 95 miliar |

## Teknik Data Cleansing

1. Standardisasi teks: hapus spasi berlebih, rapikan huruf kapital, samakan genre dengan kamus.
2. Perbaikan tipe data: jumlah putar menjadi angka, durasi menjadi detik, tanggal menjadi datetime (parsing 3 format).
3. Nilai tidak valid dijadikan kosong (NaN) lalu ditangani bersama missing value.
4. Penghapusan duplikat berdasarkan judul dan artis.
5. Penanganan outlier: dideteksi dengan IQR lalu dicek manual, hanya nilai yang tidak masuk akal yang diperbaiki.
6. Pengisian missing value: tahun dari kolom tanggal, genre diberi label `Tidak Diketahui`, kolom numerik diisi median.

## Teknik Data Enrichment

1. Tabel referensi artis, ditambahkan kolom `negara_artis` dan `benua` lewat merge.
2. Kolom turunan: `dekade`, `usia_lagu`, `durasi_menit`, `kategori_durasi`, `kategori_popularitas`, `asal_lagu` (lokal atau internasional), dan `putar_per_tahun`.

## Perbandingan Sebelum dan Sesudah

| Aspek | Sebelum | Sesudah |
|---|---|---|
| Jumlah baris | 35 | 33 |
| Jumlah kolom | 9 | 18 |
| Total missing value | 6 | 2 |
| Baris duplikat | 2 | 0 |
| Variasi penulisan genre | 14 | 9 |
| Nilai tidak valid | 6 | 0 |
| Outlier | 2 | 0 |
| Kolom dengan tipe data keliru | 3 | 0 |

Dua sel kosong yang tersisa ada di `tanggal_rilis` dan sengaja tidak diisi karena tahunnya sudah tersedia di kolom `tahun_rilis`.

## Insight Utama

- Genre Pop paling banyak (16 dari 33 lagu) dengan rata-rata popularitas 83,1.
- Lagu internasional rata-rata lebih populer (83,1) dibanding lagu lokal (73,8), dengan jumlah putar jauh lebih besar.
- Dekade 2010-an paling banyak lagunya (15 lagu).

## Cara Menjalankan

1. Buka `2418058DataCleansing.ipynb` di Google Colab (File, lalu Upload notebook, atau lewat Open in Colab dari GitHub).
2. Klik Runtime, lalu Run all. Data mentah sudah ada di dalam notebook, jadi tidak perlu upload file.

## Library

pandas, numpy, matplotlib
