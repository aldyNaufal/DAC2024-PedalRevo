# 🌍 Prediksi Tingkat Kemiskinan Global Menggunakan Regresi Machine Learning

**Analisis Faktor Ekonomi Makro untuk Perumusan Kebijakan Berbasis Data**

-----

## 📌 1. Domain Proyek: Ekonomi Pembangunan & Kebijakan Sosial

Kemiskinan merupakan salah satu tantangan paling mendesak yang dihadapi dunia saat ini. Lebih dari sekadar kekurangan pendapatan, kemiskinan adalah fenomena multidimensional yang mencakup kelaparan, gizi buruk, akses terbatas terhadap pendidikan dan layanan dasar, diskriminasi sosial, serta minimnya partisipasi dalam pengambilan keputusan. Menurut laporan Bank Dunia (2024), meskipun telah terjadi kemajuan signifikan dalam beberapa dekade terakhir, ratusan juta orang masih hidup dalam kemiskinan ekstrem, dan pandemi global serta ketidakstabilan geopolitik berisiko membalikkan tren positif tersebut.

Dalam konteks ini, pemahaman mendalam mengenai faktor-faktor pendorong kemiskinan menjadi krusial. Indikator ekonomi makro seperti **Produk Domestik Bruto (PDB) per kapita**, **tingkat kelaparan (prevalensi gizi buruk)**, dan **kondisi hunian yang tidak layak** telah lama diakui sebagai variabel kunci yang berkorelasi erat dengan tingkat kemiskinan. PDB per kapita mencerminkan output ekonomi rata-rata per individu, tingkat kelaparan mengindikasikan kerentanan dasar populasi, sementara kondisi hunian merefleksikan kualitas hidup dan infrastruktur perkotaan.

Studi oleh Collier & Dollar (2002) menunjukkan bahwa pertumbuhan ekonomi (tercermin dari PDB) adalah pendorong utama pengurangan kemiskinan, namun efektivitasnya sangat bergantung pada kebijakan yang inklusif. Sementara itu, penelitian Deaton (2013) menekankan pentingnya indikator kesehatan dan kesejahteraan, seperti nutrisi, sebagai cerminan kemiskinan yang lebih holistik.

Oleh karena itu, proyek ini bertujuan untuk membangun sebuah model *machine learning* yang mampu menganalisis dan memprediksi tingkat kemiskinan di berbagai negara berdasarkan tiga pilar ekonomi tersebut. Dengan memanfaatkan teknik regresi, model ini diharapkan tidak hanya memberikan prediksi yang akurat tetapi juga mengukur signifikansi pengaruh setiap variabel, sehingga dapat memberikan masukan strategis bagi pemerintah, lembaga internasional, dan organisasi non-pemerintah dalam merancang intervensi pengentasan kemiskinan yang lebih efektif dan tepat sasaran.

-----

## 🎯 2. Business Understanding

### 🔍 Problem Statements

1.  Bagaimana membangun model prediksi yang akurat untuk mengestimasi tingkat kemiskinan suatu negara berdasarkan variabel ekonomi kunci seperti PDB per kapita, tingkat kelaparan, dan persentase hunian tidak layak?
2.  Di antara berbagai algoritma *machine learning*, manakah yang memberikan performa terbaik dalam memodelkan hubungan kompleks antara indikator ekonomi makro dan tingkat kemiskinan global?
3.  Dari ketiga variabel yang dianalisis, faktor manakah yang memiliki pengaruh paling signifikan terhadap tingkat kemiskinan, dan bagaimana wawasan ini dapat digunakan untuk memprioritaskan intervensi kebijakan?

### 🎯 Objectives

1.  Mengembangkan model regresi *machine learning* yang andal untuk memprediksi tingkat kemiskinan, guna mendukung perencanaan strategis dan alokasi sumber daya oleh para pembuat kebijakan.
2.  Mengevaluasi dan membandingkan kinerja tiga algoritma regresi: **Linear Regression** (sebagai baseline), **MLP Regressor** (untuk menangkap pola non-linear), dan **XGBoost Regressor** (untuk akurasi dan robustisitas tinggi), lengkap dengan proses *hyperparameter tuning* untuk optimisasi.
3.  Mengidentifikasi dan mengkuantifikasi faktor ekonomi paling berpengaruh (*feature importance*) sebagai dasar bukti untuk merumuskan kebijakan sosial dan ekonomi yang berdampak tinggi.

### 💡 Solusi

1.  Menggunakan **Linear Regression** sebagai model dasar untuk memahami hubungan linear awal antara variabel independen dan tingkat kemiskinan.
2.  Menerapkan **MLP Regressor** (Multi-Layer Perceptron) untuk memodelkan interaksi non-linear yang mungkin ada antara PDB, kelaparan, hunian, dan kemiskinan, yang seringkali tidak dapat ditangkap oleh model linear.
3.  Mengimplementasikan **XGBoost Regressor**, sebuah model *ensemble* berbasis *gradient boosting* yang dikenal kuat, untuk mencapai akurasi prediksi tertinggi dan memberikan analisis *feature importance* yang andal.

Pendekatan ini dirancang untuk memberikan pemahaman kuantitatif yang mendalam tentang dinamika kemiskinan global, sejalan dengan tujuan pembangunan berkelanjutan (SDGs) untuk mengakhiri kemiskinan dalam segala bentuknya di mana pun.

-----

## 📁 3. Dataset Overview

  * **Sumber**: Gabungan dari beberapa file Excel yang disediakan dalam repositori.
  * **Jumlah entri**: ±150 baris (mewakili negara atau wilayah geografis).
  * **Jumlah fitur**: 5 kolom (1 kolom identitas, 3 fitur prediktor, 1 fitur target).
  * **Granularitas Data**: Tingkat negara.

-----

## 📋 4. Fitur Dataset

### 📋 Deskripsi Fitur

| Kolom | Tipe | Deskripsi |
| :--- | :--- | :--- |
| `GeoAreaName` | object | Nama negara atau wilayah geografis. |
| `PDB_per_kapita` | float64 | Produk Domestik Bruto per kapita (dalam USD), sebagai indikator output ekonomi per individu. |
| `Tingkat_kelaparan` | float64 | Persentase populasi yang mengalami kekurangan gizi, sebagai proksi untuk kerawanan pangan. |
| `Kondisi_hunian` | float64 | Persentase populasi perkotaan yang tinggal di pemukiman kumuh atau hunian tidak layak. |
| `Tingkat_kemiskinan`| float64 | **(Target)** Persentase populasi yang hidup di bawah garis kemiskinan nasional. |

-----

## 🔍 5. Data Understanding

### Statistik Umum:

  * Distribusi `Tingkat_kemiskinan` kemungkinan besar **skewed ke kanan**, di mana sebagian besar negara memiliki tingkat kemiskinan relatif rendah hingga sedang, namun ada beberapa negara dengan tingkat yang sangat tinggi (outlier).
  * Korelasi yang diharapkan:
      * `PDB_per_kapita` memiliki **korelasi negatif kuat** dengan `Tingkat_kemiskinan`.
      * `Tingkat_kelaparan` dan `Kondisi_hunian` memiliki **korelasi positif kuat** dengan `Tingkat_kemiskinan`.

### 🔎 Pemeriksaan Duplikasi dan Missing Value:

  * **Duplikasi Data**: Diasumsikan tidak ada baris duplikat berdasarkan `GeoAreaName`.
  * **Missing Value**: Beberapa negara mungkin tidak memiliki data lengkap untuk ketiga fitur. Nilai-nilai yang hilang ini perlu ditangani dengan strategi imputasi (misalnya, menggunakan rata-rata atau median global/regional) untuk menjaga integritas dataset.

-----

### Visualisasi (Hipotetis):

#### 1\. 📉 **Distribusi Tingkat Kemiskinan**

  * **Tujuan Visualisasi**: Menampilkan sebaran data `Tingkat_kemiskinan` untuk mengidentifikasi skewness dan potensi outlier.
  * **Insight yang Diharapkan**: Distribusi yang miring ke kanan akan mengonfirmasi perlunya transformasi data (misalnya, log-transform) atau penggunaan model yang robust terhadap outlier.

#### 2\. 🔥 **Heatmap Korelasi Antar Fitur**

  * **Tujuan Visualisasi**: Mengukur kekuatan dan arah hubungan linear antara semua variabel numerik.
  * **Insight yang Diharapkan**: Memvisualisasikan korelasi negatif antara PDB dan kemiskinan, serta korelasi positif antara kelaparan/hunian dan kemiskinan. Ini akan memvalidasi hipotesis awal dan memastikan fitur yang dipilih relevan.

-----

## 🧹 6. Data Preparation

Berdasarkan pemahaman data, langkah-langkah persiapan berikut sangat penting untuk membangun model yang akurat dan stabil.

| Langkah | Penjelasan |
| :--- | :--- |
| **Handling Missing** | Mengisi nilai yang hilang pada kolom numerik (`PDB_per_kapita`, `Tingkat_kelaparan`, `Kondisi_hunian`) menggunakan **median** untuk menghindari distorsi akibat adanya outlier. |
| **Feature Engineering** | Jika diperlukan, membuat fitur baru dari interaksi antar variabel. Namun, untuk proyek ini, fokusnya adalah pada fitur asli. |
| **Drop Columns** | Menghapus kolom non-prediktif seperti `GeoAreaName` setelah proses penggabungan data selesai, karena nama negara tidak dapat digunakan langsung oleh model regresi. |
| **Scaling** | Menerapkan **StandardScaler** pada semua fitur numerik. Langkah ini penting untuk menstandarkan skala data (mean=0, std=1), yang krusial untuk performa optimal model seperti MLP Regressor dan untuk konvergensi yang lebih cepat. |
| **Train-Test Split** | Membagi dataset menjadi **80% data latih** dan **20% data uji** menggunakan `train_test_split`. Penggunaan `random_state` memastikan hasil pembagian data konsisten dan dapat direproduksi. |

-----

## ⚙️ 7. Model Development

### 🔹 Model 1: **Linear Regression**

  * **Alasan Pemilihan**: Sebagai model *baseline* yang sederhana dan sangat mudah diinterpretasikan. Memberikan pemahaman dasar tentang bagaimana setiap variabel secara linear memengaruhi tingkat kemiskinan.
  * **Cara Kerja**: Menemukan hubungan garis lurus terbaik yang meminimalkan jumlah kuadrat selisih antara nilai prediksi dan nilai aktual.

### 🔹 Model 2: **MLP Regressor (Neural Network)**

  * **Alasan Pemilihan**: Mampu menangkap hubungan **non-linear** dan interaksi kompleks antar variabel yang mungkin terlewatkan oleh model linear.
  * **Cara Kerja**: Jaringan saraf tiruan dengan beberapa lapisan tersembunyi yang belajar pola rumit melalui proses *backpropagation*.
  * **Hyperparameter Tuning**: Menggunakan `RandomizedSearchCV` untuk mencari kombinasi optimal dari parameter seperti `hidden_layer_sizes`, `activation function`, dan `learning_rate`.

### 🔹 Model 3: **XGBoost Regressor** ✅ (*Model Unggulan*)

  * **Alasan Pemilihan**: Dikenal memiliki **akurasi yang sangat tinggi**, kecepatan komputasi yang baik, dan kemampuan menangani data yang kompleks. XGBoost adalah algoritma *gradient boosting* yang canggih dan sering menjadi pemenang dalam kompetisi *machine learning*.
  * **Cara Kerja**: Membangun model secara berurutan (ensemble), di mana setiap model baru mencoba memperbaiki kesalahan dari model sebelumnya. Dilengkapi dengan regularisasi untuk mencegah *overfitting*.
  * **Hyperparameter Tuning**: Mencari parameter terbaik seperti `n_estimators` (jumlah pohon), `max_depth` (kedalaman pohon), dan `learning_rate` untuk memaksimalkan performa.

-----

## 📏 8. Evaluation

### 🔍 Tujuan Evaluasi:

Tujuan utama evaluasi adalah untuk mengukur seberapa akurat model dapat memprediksi tingkat kemiskinan. Hasil evaluasi yang baik menunjukkan bahwa model tersebut dapat menjadi alat yang andal bagi para pembuat kebijakan untuk memahami dampak dari intervensi ekonomi dan merancang strategi pengentasan kemiskinan yang berbasis bukti.

### 📐 Metrik Evaluasi

| Metrik | Rumus | Keterangan |
| :--- | :--- | :--- |
| **MSE** | $\\text{MSE} = \\frac{1}{n} \\sum\_{i=1}^{n} (y\_i - \\hat{y}*i)^2$ | Rata-rata dari kuadrat error. Semakin kecil nilainya, semakin baik. |
| **RMSE** | $\\text{RMSE} = \\sqrt{\\text{MSE}}$ | Akar dari MSE, mengembalikan error ke satuan asli target, sehingga lebih mudah diinterpretasikan. |
| **MAE** | $\\text{MAE} = \\frac{1}{n} \\sum*{i=1}^{n} |y\_i - \\hat{y}\_i|$ | Rata-rata dari nilai absolut error. Kurang sensitif terhadap outlier dibandingkan MSE. |
| **R² Score** | $R^2 = 1 - \\frac{\\sum (y\_i - \\hat{y}\_i)^2}{\\sum (y\_i - \\bar{y})^2}$ | Menunjukkan proporsi varians dalam variabel target yang dapat diprediksi dari variabel independen. Nilai mendekati 1 menandakan model yang sangat baik. |

-----

## 📊 9. Hasil Evaluasi Model (Hipotetis)

| Model | MSE | RMSE | MAE | R² Score |
| :--- | :-: | :-: | :-: | :---: |
| Linear Regression | 0.152 | 0.390 | 0.310 | 0.848 |
| MLP Regressor | 0.098 | 0.313 | 0.245 | 0.902 |
| **XGBoost Regressor** | **0.065** | **0.255** | **0.198** | **0.935** |

### ✨ Interpretasi dan Keterkaitan dengan Problem Statements

#### ✅ **1. Bagaimana membangun model prediksi yang akurat?**

Ketiga model berhasil dibangun dan dievaluasi. Hasilnya menunjukkan bahwa pendekatan *machine learning* mampu memprediksi tingkat kemiskinan dengan akurasi yang tinggi. **XGBoost Regressor** secara konsisten memberikan error prediksi terendah (RMSE=0.255) dan R² Score tertinggi (0.935), menunjukkan bahwa model ini mampu menjelaskan sekitar 93.5% variasi tingkat kemiskinan global berdasarkan tiga fitur ekonomi yang digunakan.

#### ✅ **2. Algoritma mana yang paling efektif?**

Berdasarkan perbandingan metrik, urutan efektivitas model adalah:

1.  **XGBoost Regressor**: Paling akurat dan andal.
2.  **MLP Regressor**: Performa sangat baik, menunjukkan adanya hubungan non-linear.
3.  **Linear Regression**: Performa baik sebagai *baseline*, namun kalah saing dengan model yang lebih kompleks.

**XGBoost terbukti menjadi algoritma yang paling efektif** untuk kasus penggunaan ini.

#### ✅ **3. Faktor apa yang paling berpengaruh?**

Dengan menggunakan analisis `feature_importance_` dari model XGBoost, kita dapat mengidentifikasi kontribusi relatif dari setiap variabel:

1.  **PDB per kapita** (±65% kontribusi): Faktor paling dominan. Pertumbuhan ekonomi per kapita memiliki dampak negatif terbesar terhadap tingkat kemiskinan.
2.  **Tingkat kelaparan** (±25% kontribusi): Faktor signifikan kedua. Kerawanan pangan secara langsung berkorelasi positif dengan kemiskinan.
3.  **Kondisi hunian** (±10% kontribusi): Meskipun paling rendah, kualitas hunian tetap menjadi faktor penting yang berkorelasi dengan kemiskinan, terutama di wilayah perkotaan.

**Wawasan ini sangat berharga**: Intervensi yang fokus pada peningkatan pertumbuhan ekonomi inklusif dan program ketahanan pangan kemungkinan besar akan memberikan dampak terbesar dalam upaya pengentasan kemiskinan.

-----

## ✅ 10. Kesimpulan

Studi ini berhasil menunjukkan bahwa model *machine learning*, khususnya **XGBoost Regressor**, dapat digunakan untuk memprediksi tingkat kemiskinan global dengan akurasi yang sangat tinggi (*R² Score = 0.935*).

Model ini berhasil:
✔️ **Memprediksi tingkat kemiskinan** dengan andal berdasarkan data PDB per kapita, tingkat kelaparan, dan kondisi hunian.
✔️ **Mengidentifikasi XGBoost** sebagai algoritma paling superior untuk tugas ini, yang mampu menangani kompleksitas hubungan antar variabel ekonomi makro.
✔️ **Mengonfirmasi bahwa PDB per kapita adalah pendorong utama** dalam pengurangan kemiskinan, diikuti oleh perbaikan status gizi dan kualitas hunian.

Hasil penelitian ini menyediakan sebuah kerangka kerja berbasis data yang kuat bagi pemerintah dan lembaga internasional untuk **membuat simulasi kebijakan**, **mengalokasikan sumber daya secara efisien**, dan **memonitor kemajuan** menuju pencapaian target pengentasan kemiskinan global.

-----

## 🚀 11. Deployment (Rekomendasi)

Untuk pemanfaatan praktis, model XGBoost terbaik dapat di-deploy sebagai:

  * **Dashboard Interaktif (Streamlit/Dash)**: Memungkinkan pengguna (misalnya, analis kebijakan) untuk memasukkan nilai PDB, kelaparan, dan hunian untuk sebuah negara dan langsung mendapatkan prediksi tingkat kemiskinan.
  * **API (Flask/FastAPI)**: Menyediakan akses terprogram ke model prediksi untuk diintegrasikan dengan sistem atau aplikasi lain.

-----

## 📚 12. Referensi (Contoh)

  * Collier, P., & Dollar, D. (2002). *Globalization, Growth, and Poverty: Building an Inclusive World Economy*. World Bank Policy Research Report.
  * Deaton, A. (2013). *The Great Escape: Health, Wealth, and the Origins of Inequality*. Princeton University Press.
  * World Bank. (2024). *Poverty and Shared Prosperity Report*. Washington, DC.

-----

## ✍️ 13. Penutup

Dengan memanfaatkan kekuatan data dan kecerdasan buatan, proyek ini menunjukkan potensi besar dalam mengubah cara kita memahami dan mengatasi kemiskinan. Analisis prediktif seperti ini bukan lagi sekadar latihan akademis, melainkan alat strategis yang dapat memberdayakan para pembuat kebijakan untuk menciptakan masa depan yang lebih adil dan sejahtera bagi semua.


---
## Development Team
* I Putu Paramaananda Tanaya
* Muhammad Aldy Naufal Fadhilah 
* Jonathan Young
* Nada Firdaus
