# Data Cleansing dan Data Enrichment: Dataset Lagu

Tugas Studi Kasus Mata Kuliah Data Mining (Pertemuan 4)

Nama: David Andrew Gregorius Tingang Liah
NIM: 2418058
Kelas: A

## Deskripsi

Project ini membersihkan (data cleansing) dan memperkaya (data enrichment) dataset lagu populer berisi 35 baris, memakai Python (pandas) di Google Colab. Datasetnya saya susun sendiri sebagai data contoh dan sengaja dibuat berisi masalah kualitas data untuk latihan.

## File

- 2418058DataCleansing.ipynb: notebook berisi semua tahapan pengerjaan
- dataset_musik_mentah.csv: data sebelum dibersihkan (35 baris, 9 kolom)
- dataset_musik_bersih.csv: data setelah cleansing dan enrichment (33 baris, 18 kolom)

## Masalah Data yang Ditemukan

- Missing value (6 sel kosong)
- Data duplikat (2 baris)
- Format tidak konsisten (genre, durasi, tanggal)
- Tipe data salah (jumlah putar, durasi, tanggal terbaca sebagai teks)
- Data tidak valid (popularitas 150, tahun 2035, jumlah putar negatif, dan lainnya)
- Outlier (durasi 58 menit, jumlah putar 95 miliar)

## Teknik yang Dipakai

**Data Cleansing:** standardisasi teks, perbaikan tipe data, penanganan nilai tidak valid, hapus duplikat, deteksi outlier dengan IQR, dan pengisian missing value (median dan nilai dari kolom terkait).

**Data Enrichment:** menambah negara dan benua artis dari tabel referensi, serta kolom baru seperti dekade, usia lagu, kategori durasi, kategori popularitas, dan asal lagu (lokal atau internasional).

## Hasil

| Aspek | Sebelum | Sesudah |
|---|---|---|
| Jumlah baris | 35 | 33 |
| Jumlah kolom | 9 | 18 |
| Missing value | 6 | 2 |
| Duplikat | 2 | 0 |
| Nilai tidak valid | 6 | 0 |
| Outlier | 2 | 0 |

Dua missing value yang tersisa ada di kolom tanggal rilis dan sengaja tidak diisi karena tahunnya sudah ada di kolom lain.

## Cara Menjalankan

Buka 2418058DataCleansing.ipynb di Google Colab, lalu klik Runtime, Run all. Data sudah ada di dalam notebook, jadi tidak perlu upload file.
