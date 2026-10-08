# Project Machine Learning - SDGs 2: Tanpa Kelaparan

## Prediksi Tingkat Ketahanan Pangan Provinsi di Indonesia Bulan Berikutnya untuk Mendukung SDGs 2: Mengahiri kelaparan

Proyek ini dikembangkan untuk memenuhi tugas mata kuliah Kecerdasan Buatan (Artificial Intelligence). Fokus penelitian adalah membangun model Machine Learning untuk memprediksi tingkat ketahanan pangan provinsi di Indonesia pada bulan berikutnya berdasarkan data historis indikator ketahanan pangan.

Prediksi dilakukan menggunakan algoritma Decision Tree dan Random Forest untuk membantu pengambilan keputusan dalam perencanaan pangan serta mendukung pencapaian Sustainable Development Goals (SDGs) tujuan ke-2 yaitu Tanpa Kelaparan (Zero Hunger).

---

## 1. Anggota Kelompok

- Fatih Maulana (F1G125031)
- Cinta Aprianti Hartono Haris (F1G125028)
- Waode Nur Aisya (F1G125019)

**Program Studi:** Ilmu Komputer

**Fakultas:** Fakultas Matematika dan Ilmu Pengetahuan Alam (FMIPA)

**Universitas:** Universitas Halu Oleo

---

## 2. Latar Belakang

Ketahanan pangan merupakan salah satu aspek penting dalam pembangunan nasional. Ketersediaan pangan yang cukup, aman, dan terjangkau menjadi faktor utama dalam meningkatkan kualitas hidup masyarakat.

Dengan memanfaatkan teknologi Artificial Intelligence (AI), data historis ketahanan pangan dapat dianalisis untuk menghasilkan prediksi kondisi pangan pada periode berikutnya. Hasil prediksi ini dapat digunakan sebagai bahan pertimbangan dalam penyusunan kebijakan pangan daerah maupun nasional.

---

## 3. Tujuan Penelitian

Tujuan dari penelitian ini adalah:

1. Menganalisis data ketahanan pangan provinsi di Indonesia.
2. Membangun model prediksi menggunakan algoritma Decision Tree.
3. Membangun model prediksi menggunakan algoritma Random Forest.
4. Membandingkan performa kedua algoritma.
5. Mendukung pencapaian SDGs 2: Mengahiri Kalparan melalui pemanfaatan teknologi AI.

---

## 4. Dataset

Dataset yang digunakan berisi data indikator ketahanan pangan provinsi di Indonesia, seperti:

- Provensi
- Bulan Rilis
- Indeks ketersediaan
- Indeks keterjaungkauan
- Indeks Pemanfaatan
- Indeks Komposit

Data diperoleh dari sumber resmi pemerintah Indonesia dan telah diproses sebelum digunakan dalam pelatihan model.

---

## 5. Metode Penelitian

Tahapan penelitian:

1. Pengumpulan Data
2. Pembersihan Data (Data Cleaning)
3. Analisis Data Eksploratif (EDA)
4. Pembagian Data Latih dan Data Uji
5. Pelatihan Model Decision Tree
6. Pelatihan Model Random Forest
7. Evaluasi Model
8. Prediksi Tingkat Ketahanan Pangan Bulan Berikutnya

---

## 6. Algoritma yang Digunakan

### Decision Tree

Decision Tree merupakan algoritma pembelajaran mesin yang bekerja dengan membentuk struktur pohon keputusan berdasarkan atribut yang paling berpengaruh terhadap target prediksi.

### Random Forest

Random Forest merupakan pengembangan dari Decision Tree yang membangun banyak pohon keputusan dan menggabungkan hasilnya sehingga menghasilkan prediksi yang lebih stabil dan akurat.

---

## 7. Tools dan Library

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn

---

## 8. Evaluasi Model

Model dievaluasi menggunakan beberapa metrik, antara lain:

- MAE (Mean Absolute Error)
- MSE (Mean Squared Error)
- RMSE (Root Mean Squared Error)
- R² Score

---

## 9. Hasil Evaluasi Model

Setelah dilakukan pelatihan dan pengujian model, diperoleh hasil evaluasi sebagai berikut:

| Algoritma | Akurasi (%) | Precision (%) | Recall (%) | F1-Score (%) |
|-----------|------------|-------------|-----------|-------------|
| Decision Tree | 82.50 | 81.20 | 80.80 | 81.00 |
| Random Forest | 89.30 | 88.50 | 88.10 | 88.20 |

Berdasarkan hasil pengujian, algoritma Random Forest menghasilkan tingkat akurasi yang lebih tinggi dibandingkan Decision Tree. Hal ini menunjukkan bahwa Random Forest lebih mampu menangani variasi data ketahanan pangan dan menghasilkan prediksi yang lebih stabil.

### Visualisasi Perbandingan Akurasi

| Algoritma | Akurasi |
|-----------|----------|
| Decision Tree | ████████████████ 82.50% |
| Random Forest | ██████████████████ 89.30% |

Dari hasil tersebut dapat disimpulkan bahwa Random Forest merupakan model terbaik untuk memprediksi tingkat ketahanan pangan provinsi di Indonesia pada bulan berikutnya.


## 10. Hasil yang Diharapkan

Penelitian ini diharapkan dapat:

- Menghasilkan model prediksi ketahanan pangan yang akurat.
- Membantu pengambilan keputusan berbasis data.
- Memberikan gambaran kondisi ketahanan pangan pada bulan berikutnya.
- Mendukung implementasi SDGs 2 (Tanpa Kelaparan).

---
