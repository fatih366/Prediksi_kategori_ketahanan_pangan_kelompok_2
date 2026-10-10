# Project Machine Learning - SDGs 2: Tanpa Kelaparan

## Prediksi Tingkat Ketahanan Pangan Provinsi di Indonesia Bulan Berikutnya untuk Mendukung SDGs 2: Mengakhiri Kelaparan

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Status](https://img.shields.io/badge/Status-Selesai-brightgreen)
![SDGs](https://img.shields.io/badge/SDGs-2%20Zero%20Hunger-yellow)

Proyek ini dikembangkan untuk memenuhi tugas mata kuliah Kecerdasan Buatan (*Artificial Intelligence*). Fokus penelitian adalah membangun model *Machine Learning* untuk memprediksi tingkat ketahanan pangan provinsi di Indonesia pada bulan berikutnya berdasarkan data historis indikator ketahanan pangan.

Prediksi dilakukan menggunakan algoritma *Decision Tree* dan *Random Forest* untuk membantu pengambilan keputusan dalam perencanaan pangan serta mendukung pencapaian *Sustainable Development Goals* (SDGs) tujuan ke-2 yaitu Tanpa Kelaparan (*Zero Hunger*).

---

## Daftar Isi

1. [Anggota Kelompok](#1-anggota-kelompok)
2. [Latar Belakang](#2-latar-belakang)
3. [Rumusan Masalah dan Tujuan](#3-rumusan-masalah-dan-tujuan)
4. [Dataset](#4-dataset)
5. [Metodologi](#5-metodologi)
6. [Hasil dan Pembahasan](#6-hasil-dan-pembahasan)
7. [Prediksi Bulan Berikutnya](#7-prediksi-bulan-berikutnya)
8. [Keterbatasan Penelitian](#8-keterbatasan-penelitian)
9. [Kesimpulan dan Saran](#9-kesimpulan-dan-saran)
10. [Struktur Repositori](#10-struktur-repositori)
11. [Cara Menjalankan](#11-cara-menjalankan)

---

## 1. Anggota Kelompok

| No | Nama | NIM |
|----|------|-----|
| 1 | Fatih Maulana | F1G125031 |
| 2 | Cinta Aprianti Hartono Haris | F1G125028 |
| 3 | Waode Nur Aisya | F1G125019 |

**Program Studi:** Ilmu Komputer
**Mata Kuliah:** Kecerdasan Buatan
**Dosen Pengampu:** (isi nama dosen)
**Kelompok:** 2

---

## 2. Latar Belakang

Ketahanan pangan merupakan salah satu isu strategis pembangunan nasional dan menjadi inti dari tujuan ke-2 SDGs, yaitu mengakhiri kelaparan, mencapai ketahanan pangan, memperbaiki nutrisi, dan mendorong pertanian berkelanjutan. Kondisi ketahanan pangan di Indonesia tidak seragam antarwilayah. Perbedaan ketersediaan pangan, daya beli masyarakat, dan kualitas pemanfaatan pangan membuat tingkat ketahanan pangan setiap provinsi dapat berbeda dan berubah dari waktu ke waktu.

Pemantauan yang hanya bersifat deskriptif (melihat kondisi yang sudah terjadi) memiliki keterbatasan karena intervensi kebijakan sering kali baru dilakukan setelah kondisi rentan muncul. Pendekatan prediktif berbasis data historis memungkinkan pemangku kepentingan mengantisipasi provinsi yang berpotensi mengalami penurunan ketahanan pangan sehingga perencanaan dan alokasi sumber daya dapat dilakukan lebih awal.

Berdasarkan hal tersebut, proyek ini membangun model klasifikasi yang memprediksi kategori **Indeks Komposit Ketahanan Pangan provinsi pada bulan berikutnya** dengan memanfaatkan indeks tiga pilar ketahanan pangan (ketersediaan, keterjangkauan, dan pemanfaatan) beserta fitur turunan berbasis deret waktu.

---

## 3. Rumusan Masalah dan Tujuan

### 3.1 Rumusan Masalah

1. Bagaimana membangun model klasifikasi untuk memprediksi kategori ketahanan pangan provinsi pada bulan berikutnya?
2. Bagaimana perbandingan performa *Decision Tree*, *Random Forest*, dan *Random Forest* dengan pembobotan kelas (*balanced*)?
3. Apakah model *machine learning* mampu mengungguli *baseline* sederhana, dan fitur apa yang paling berpengaruh?
4. Bagaimana kemampuan model mendeteksi provinsi dengan kategori rentan (kelas 1) yang merupakan kelas minoritas?

### 3.2 Tujuan

1. Membangun *pipeline* prediksi ketahanan pangan bulan berikutnya yang bebas kebocoran data (*data leakage*).
2. Membandingkan performa tiga model terhadap *baseline* menggunakan metrik yang sesuai untuk data tidak seimbang.
3. Mengidentifikasi fitur yang paling berpengaruh terhadap prediksi.
4. Menghasilkan prediksi ketahanan pangan seluruh provinsi untuk periode berikutnya sebagai alat bantu pengambilan keputusan.

---

## 4. Dataset

| Atribut | Keterangan |
|---------|------------|
| **Nama file** | `dataset_ai_proyek_2.1.csv` |
| **Jumlah data** | 1.808 baris dan 8 kolom |
| **Cakupan wilayah** | 38 provinsi di Indonesia |
| **Rentang waktu** | Juli 2022 sampai Agustus 2026 (data bulanan) |
| **Missing value** | Tidak ada |
| **Data duplikat** | Tidak ada (termasuk duplikat pasangan Provinsi-Periode) |
| **Sumber data** | (isi sumber data, misalnya Badan Pangan Nasional / Peta Ketahanan dan Kerentanan Pangan) |

### 4.1 Deskripsi Variabel

| Kolom | Tipe | Deskripsi |
|-------|------|-----------|
| `Tahun` | Numerik | Tahun rilis data |
| `Bulan Rilis` | Kategorikal | Bulan rilis data (Januari sampai Desember) |
| `Provinsi` | Kategorikal | Nama provinsi |
| `Kode_Provinsi` | Kategorikal | Kode wilayah provinsi |
| `Indeks_Ketersediaan` | Ordinal (1-3) | Indeks pilar ketersediaan pangan |
| `Indeks_Keterjangkauan` | Ordinal (1-3) | Indeks pilar keterjangkauan pangan |
| `Indeks_Pemanfaatan` | Ordinal (1-3) | Indeks pilar pemanfaatan pangan |
| `Indeks_Komposit` | Ordinal (1-3) | Indeks gabungan ketahanan pangan (basis variabel target) |

### 4.2 Statistik Deskriptif

| Variabel | Rata-rata | Simpangan Baku | Min | Maks |
|----------|-----------|----------------|-----|------|
| Indeks Ketersediaan | 2,26 | 0,56 | 1 | 3 |
| Indeks Keterjangkauan | 2,69 | 0,51 | 1 | 3 |
| Indeks Pemanfaatan | 2,48 | 0,72 | 1 | 3 |
| Indeks Komposit | 2,48 | 0,57 | 1 | 3 |

### 4.3 Variabel Target

Variabel target adalah **Indeks Komposit bulan berikutnya** (`Target_Bulan_Berikutnya`) dengan tiga kelas, dengan kelas 1 merupakan kategori **rentan** yang menjadi fokus deteksi dini.

| Kelas | Jumlah Data (keseluruhan) | Proporsi |
|-------|---------------------------|----------|
| 1 (rentan) | 63 | 3,7% |
| 2 | 787 | 46,5% |
| 3 | 844 | 49,8% |
| **Total** | **1.694** | **100%** |

Data tidak seimbang (*imbalanced*): kelas rentan hanya sekitar 3,7% dari seluruh data. Kondisi ini memengaruhi pemilihan metrik evaluasi dan strategi pemodelan.

---

## 5. Metodologi

Alur penelitian dirancang agar mengikuti sifat data deret waktu dan mencegah kebocoran data.

```text
Pemuatan Data -> Pembersihan & Pengurutan Waktu -> Pembentukan Target
      -> Feature Engineering -> EDA -> Split Berbasis Waktu
      -> Pipeline (Encoding -> Feature Selection -> Model)
      -> Evaluasi & Perbandingan dengan Baseline -> Prediksi Bulan Berikutnya
```

### 5.1 Pra-pemrosesan Data

1. **Konversi periode.** Nama bulan dipetakan ke angka (Januari = 1, ..., Desember = 12), lalu digabung dengan tahun menjadi kolom `Periode` bertipe *datetime*.
2. **Pengurutan.** Data diurutkan berdasarkan `Provinsi` dan `Periode` agar operasi deret waktu valid.
3. **Validasi.** Dilakukan pengecekan bulan yang gagal dipetakan (0), duplikat Provinsi-Periode (0), dan transisi bulan yang tidak berurutan (0).

### 5.2 Pembentukan Target (Bulan Berikutnya)

Target dibentuk dengan menggeser (`shift(-1)`) nilai Indeks Komposit satu bulan ke depan **per provinsi**. Sistem memverifikasi bahwa periode berikutnya benar-benar bulan setelahnya; jika terdapat lompatan bulan, target dikosongkan. Data terakhir setiap provinsi tidak memiliki target (38 baris) dan dipakai untuk prediksi akhir.

### 5.3 Rekayasa Fitur (*Feature Engineering*)

Dari empat indeks dasar (ketersediaan, keterjangkauan, pemanfaatan, komposit) dibentuk fitur turunan per provinsi:

| Kelompok Fitur | Deskripsi | Jumlah |
|----------------|-----------|--------|
| Indeks saat ini | Nilai indeks pada bulan berjalan | 4 |
| Perubahan | Selisih nilai dengan bulan sebelumnya (`diff`) | 4 |
| *Lag* 1 bulan | Nilai indeks satu bulan sebelumnya | 4 |
| *Lag* 2 bulan | Nilai indeks dua bulan sebelumnya | 4 |
| Rata-rata 3 bulan | *Rolling mean* tiga bulan terakhir | 4 |
| **Total fitur numerik** | | **20** |
| Fitur kategorikal | `Provinsi` (di-*encode* dengan One-Hot) | 1 |

Setelah menghapus baris dengan nilai kosong akibat *lag*, tersisa **1.694 baris** untuk pemodelan.

### 5.4 Pembagian Data Berbasis Waktu

Pembagian data **tidak dilakukan secara acak**, tetapi berdasarkan urutan waktu agar model diuji pada masa depan yang belum pernah dilihat, sesuai kondisi penggunaan nyata.

| Subset | Jumlah Baris | Periode | Proporsi |
|--------|--------------|---------|----------|
| Training | 1.314 | 2022-09 sampai 2025-09 | 77,57% |
| Testing | 380 | 2025-10 sampai 2026-07 | 22,43% |

Distribusi kelas pada data uji: kelas 1 = 15, kelas 2 = 184, kelas 3 = 181. Kelas rentan hanya memiliki 15 sampel pada data uji, sehingga metrik kelas 1 perlu ditafsirkan dengan hati-hati.

### 5.5 Seleksi Fitur

Seleksi fitur menggunakan **Mutual Information** (`SelectKBest`, `k = 40`) setelah proses *One-Hot Encoding*. Seleksi hanya di-*fit* pada data latih di dalam *pipeline* sehingga tidak terjadi kebocoran data dari data uji.

### 5.6 Model yang Digunakan

Seluruh model disusun dalam `Pipeline` scikit-learn: *preprocessing* (One-Hot Encoding) -> seleksi fitur -> model.

| Model | Hiperparameter Utama |
|-------|----------------------|
| **Baseline** | Prediksi bulan depan = nilai Indeks Komposit bulan ini (*persistence*) |
| **Decision Tree** | `max_depth=5`, `min_samples_leaf=5`, `random_state=42` |
| **Random Forest** | `n_estimators=300`, `max_depth=8`, `min_samples_leaf=3`, `random_state=42` |
| **Random Forest Balanced** | Sama dengan Random Forest, ditambah `class_weight="balanced"` |

### 5.7 Metrik Evaluasi

Karena data tidak seimbang, akurasi saja tidak memadai. Evaluasi menggunakan:

- *Accuracy*
- *Precision*, *Recall*, dan *F1-Score* **macro** (setiap kelas berbobot sama)
- *Precision* dan *Recall* **kelas 1** (kemampuan mendeteksi provinsi rentan)
- *ROC-AUC* (*one-vs-rest*, macro)
- *Confusion matrix* dan *classification report*

---

## 6. Hasil dan Pembahasan

### 6.1 Perbandingan Performa Model

| Model | Accuracy | Precision Macro | Recall Macro | F1 Macro | Precision Kelas 1 | Recall Kelas 1 |
|-------|:--------:|:---------------:|:------------:|:--------:|:-----------------:|:--------------:|
| Baseline | 0,668 | 0,575 | 0,566 | **0,569** | 0,357 | 0,333 |
| Decision Tree | 0,674 | 0,602 | 0,528 | 0,547 | 0,429 | 0,200 |
| Random Forest | **0,700** | **0,636** | 0,506 | 0,515 | **0,500** | 0,067 |
| Random Forest Balanced | 0,629 | 0,529 | **0,641** | 0,541 | 0,196 | **0,667** |

> Nilai ROC-AUC dihitung pada notebook (`Notebook_AI_Terurut_dan_Diperbaiki.ipynb`) dan dapat dilihat setelah sel evaluasi dijalankan.

### 6.2 Classification Report per Kelas (Data Uji)

**Decision Tree**

| Kelas | Precision | Recall | F1-Score | Support |
|:-----:|:---------:|:------:|:--------:|:-------:|
| 1 | 0,43 | 0,20 | 0,27 | 15 |
| 2 | 0,63 | 0,77 | 0,70 | 184 |
| 3 | 0,74 | 0,61 | 0,67 | 181 |

**Random Forest**

| Kelas | Precision | Recall | F1-Score | Support |
|:-----:|:---------:|:------:|:--------:|:-------:|
| 1 | 0,50 | 0,07 | 0,12 | 15 |
| 2 | 0,67 | 0,74 | 0,71 | 184 |
| 3 | 0,74 | 0,71 | 0,72 | 181 |

**Random Forest Balanced**

| Kelas | Precision | Recall | F1-Score | Support |
|:-----:|:---------:|:------:|:--------:|:-------:|
| 1 | 0,20 | 0,67 | 0,30 | 15 |
| 2 | 0,64 | 0,56 | 0,60 | 184 |
| 3 | 0,75 | 0,70 | 0,72 | 181 |

### 6.3 Confusion Matrix (Data Uji)

Baris = kelas aktual, kolom = kelas prediksi.

| Model | Aktual | Prediksi 1 | Prediksi 2 | Prediksi 3 |
|-------|:------:|:----------:|:----------:|:----------:|
| Baseline | 1 | 5 | 10 | 0 |
| | 2 | 9 | 128 | 47 |
| | 3 | 0 | 60 | 121 |
| Decision Tree | 1 | 3 | 12 | 0 |
| | 2 | 4 | 142 | 38 |
| | 3 | 0 | 70 | 111 |
| Random Forest | 1 | 1 | 14 | 0 |
| | 2 | 1 | 137 | 46 |
| | 3 | 0 | 53 | 128 |
| Random Forest Balanced | 1 | 10 | 5 | 0 |
| | 2 | 39 | 103 | 42 |
| | 3 | 2 | 53 | 126 |

### 6.4 Pembahasan

1. **Akurasi tertinggi** dicapai *Random Forest* (0,700), tetapi model ini hanya mendeteksi 1 dari 15 provinsi rentan (*recall* kelas 1 = 0,067). Akurasi yang tinggi sebagian besar didorong oleh dua kelas mayoritas.
2. **Deteksi kelas rentan terbaik** diperoleh *Random Forest Balanced* (*recall* kelas 1 = 0,667; 10 dari 15 terdeteksi). Konsekuensinya, *precision* kelas 1 turun menjadi 0,196 karena 39 data kelas 2 salah diklasifikasikan sebagai kelas 1, sehingga model ini menghasilkan lebih banyak peringatan dini palsu (*false alarm*).
3. **Trade-off precision-recall** tampak jelas: pembobotan kelas meningkatkan sensitivitas terhadap kelas rentan dengan mengorbankan akurasi keseluruhan (0,629).
4. **Perbandingan dengan baseline.** Baseline *persistence* menghasilkan F1 macro tertinggi (0,569), sedikit di atas ketiga model. Hal ini menunjukkan bahwa indeks komposit cenderung bertahan dari satu bulan ke bulan berikutnya, sehingga nilai bulan ini sudah menjadi prediktor yang kuat. Model belum memberikan peningkatan yang jelas pada F1 macro, namun *Random Forest* unggul pada akurasi dan *Random Forest Balanced* unggul pada deteksi kelas rentan.
5. **Pemilihan model.** Berdasarkan F1 macro di antara tiga model, *Decision Tree* terbaik (0,547). Untuk tujuan deteksi dini provinsi rentan, *Random Forest Balanced* dipilih sebagai **model operasional** karena memiliki *recall* kelas 1 tertinggi.

### 6.5 Fitur yang Paling Berpengaruh

Hasil *feature importance* yang tercatat pada notebook (model *Decision Tree*) menunjukkan bahwa pilar **pemanfaatan** pangan dan fitur rata-rata/riwayatnya mendominasi prediksi:

| Peringkat | Fitur | Importance |
|:---------:|-------|:----------:|
| 1 | Rata3_Pemanfaatan | 0,1396 |
| 2 | Indeks_Pemanfaatan | 0,1248 |
| 3 | Lag1_Pemanfaatan | 0,0986 |
| 4 | Rata3_Komposit | 0,0764 |
| 5 | Lag2_Pemanfaatan | 0,0757 |
| 6 | Indeks_Komposit | 0,0515 |
| 7 | Rata3_Keterjangkauan | 0,0466 |
| 8 | Lag2_Komposit | 0,0409 |
| 9 | Lag1_Komposit | 0,0372 |
| 10 | Lag1_Keterjangkauan | 0,0357 |

Fitur berbasis riwayat (rata-rata 3 bulan dan *lag*) muncul di peringkat atas, yang menegaskan manfaat rekayasa fitur deret waktu.

---

## 7. Prediksi Bulan Berikutnya

Setelah model dilatih, prediksi dilakukan untuk seluruh 38 provinsi menggunakan data periode terakhir (**Agustus 2026**) untuk memprediksi kondisi **September 2026**. Keluaran prediksi mencakup:

- kelas Indeks Komposit yang diprediksi untuk bulan berikutnya,
- peluang provinsi berada pada kelas rentan (`Peluang_Rentan_Persen`),
- daftar provinsi prioritas pemantauan (provinsi yang diprediksi kelas 1, diurutkan berdasarkan peluang).


| No | Provinsi | Indeks Saat Ini | Prediksi Bulan Depan | Peluang Rentan (%) |
|----|----------|:---------------:|:--------------------:|:------------------:|
| 1 | Papua Barat Daya | 1 | 1 | 69.45% |
| 2 | Papua Barat | 1 | 1 | 69.28% |
| 3 | Papua Selatan | 1 | 1 | 56.06% |
| 4 | Sulawesi Barat | 2 | 1 | 54.57% |

> **Catatan:** Prediksi bersifat probabilistik dan digunakan sebagai alat bantu pengambilan keputusan, bukan keputusan akhir.

---

## 8. Keterbatasan Penelitian

1. **Ketidakseimbangan kelas.** Kelas rentan hanya 3,7% dari data dan 15 sampel pada data uji, sehingga metrik kelas 1 bersifat tidak stabil.
2. **Jumlah fitur terbatas.** Model hanya memakai indeks ketahanan pangan dan turunannya; faktor eksternal seperti harga komoditas, curah hujan, produksi, dan inflasi belum dimasukkan.
3. **Indeks bersifat diskret (1-3).** Perubahan antarbulan kecil dan banyak provinsi stabil, sehingga model sulit mengungguli *baseline* *persistence*.
4. **Satu skema pembagian waktu.** Evaluasi menggunakan satu pemisahan latih-uji; validasi silang deret waktu (*time series cross-validation*) belum diterapkan.
5. **Hiperparameter tetap.** Penyetelan hiperparameter (misalnya *grid search*) belum dilakukan.

---

## 9. Kesimpulan dan Saran

### 9.1 Kesimpulan

1. Model klasifikasi prediksi ketahanan pangan bulan berikutnya berhasil dibangun dengan *pipeline* yang memisahkan data berdasarkan waktu dan melakukan seleksi fitur hanya pada data latih.
2. *Random Forest* mencapai akurasi tertinggi (0,700), sedangkan *Random Forest Balanced* paling baik dalam mendeteksi provinsi rentan (*recall* kelas 1 = 0,667) meskipun disertai lebih banyak peringatan palsu.
3. Ketiga model belum melampaui F1 macro *baseline* (0,569), sehingga hasil ini perlu dibaca sebagai bukti bahwa kondisi bulan sebelumnya sudah sangat informatif, bukan sebagai bukti bahwa model sudah optimal.
4. Pilar pemanfaatan pangan beserta fitur riwayatnya merupakan prediktor yang paling berpengaruh.

### 9.2 Saran

1. Menambahkan variabel eksternal (harga pangan, cuaca, produksi, inflasi) untuk memperkaya informasi model.
2. Menerapkan teknik penanganan data tidak seimbang yang lebih lanjut (misalnya SMOTE atau penyesuaian ambang keputusan) dan *time series cross-validation*.
3. Melakukan penyetelan hiperparameter dan mencoba algoritma lain (misalnya *Gradient Boosting* atau XGBoost).
4. Menggunakan model operasional sebagai sistem peringatan dini bersama pertimbangan pakar, bukan sebagai pengganti keputusan kebijakan.

---

## Teknologi

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Google Colab.

## Lisensi dan Catatan

Proyek ini dibuat untuk keperluan akademik. Hasil prediksi bukan merupakan keputusan resmi dan hanya digunakan sebagai alat bantu analisis.
