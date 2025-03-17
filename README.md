## 1. Overview

Repository ini berisi dua Jupyter Notebook utama yang saling mendukung untuk menganalisis faktor-faktor ekonomi yang memengaruhi kemiskinan di berbagai negara. Analisis ini berfokus pada tiga variabel kunci:  
- **Produk Domestik Bruto (PDB) per kapita**  
- **Tingkat kelaparan**  
- **Kondisi hunian (persentase populasi perkotaan yang tinggal di rumah tidak layak)**  

Pendekatan ini diharapkan memberikan pemahaman mendalam mengenai dampak masing-masing variabel terhadap tingkat kemiskinan serta membantu dalam merumuskan strategi pengentasan kemiskinan yang efektif.

## 2. Latar Belakang & Konteks Penelitian

Kemiskinan merupakan tantangan global yang sangat kompleks, terutama di negara-negara berkembang. Kondisi ini tidak hanya mempengaruhi kesejahteraan individu tetapi juga menghambat kemajuan ekonomi dan sosial secara keseluruhan. Indikator ekonomi seperti PDB per kapita, tingkat kelaparan, dan kondisi hunian menjadi elemen penting dalam mengukur dan memahami fenomena kemiskinan.  
Penelitian ini bertujuan untuk:
- Menganalisis korelasi antara variabel-variabel ekonomi tersebut dengan tingkat kemiskinan.
- Mengukur persentase pengaruh tiap variabel terhadap tingkat kemiskinan.
- Membuat prediksi mengenai tingkat kemiskinan di masa mendatang (misalnya, tahun 2023) guna mendukung perumusan kebijakan ekonomi dan sosial yang lebih tepat sasaran.

Hasil dari analisis ini diharapkan dapat memberikan kontribusi ilmiah serta masukan praktis bagi pembuat kebijakan, lembaga internasional, dan pemerintah dalam upaya pengurangan kemiskinan secara berkelanjutan.

## 3. Struktur Notebook

### main.ipynb
- **Tujuan:**  
  Memuat dan menggabungkan data dari berbagai file Excel, yang masing-masing berisi informasi terkait PDB per kapita, tingkat kelaparan, kondisi hunian, dan data target kemiskinan.
- **Langkah Utama:**
  1. Mengimpor library `numpy` dan `pandas`.
  2. Membaca file Excel seperti `fitur_1.xlsx`, `fitur_2.xlsx`, `fitur_3.xlsx`, dan `target.xlsx`.
  3. Menggabungkan data berdasarkan kolom kunci (misalnya, "GeoAreaName") untuk membentuk dataset komprehensif.

### ml.ipynb
- **Tujuan:**  
  Melakukan pra-pemrosesan data dan membangun model machine learning (regresi) untuk menganalisis serta memprediksi tingkat kemiskinan.
- **Langkah Utama:**
  1. Mengimpor library yang diperlukan untuk analisis data dan pemodelan, seperti `pandas`, `numpy`, `scikit-learn`, `matplotlib`, dan `seaborn`.
  2. Membaca dataset gabungan yang telah disiapkan (misalnya `merged_data.xlsx`).
  3. Menangani nilai yang hilang dengan strategi pengisian (seperti menggunakan rata-rata).
  4. Memisahkan data menjadi set pelatihan dan pengujian.
  5. Melatih model MLP Regressor untuk memprediksi tingkat kemiskinan berdasarkan variabel ekonomi yang ada.
  6. Menyajikan visualisasi untuk mendukung analisis dan interpretasi hasil.

## 4. Dependensi

Pastikan Anda telah menginstal paket-paket berikut sebelum menjalankan notebook:

- Python 3.x
- `numpy`
- `pandas`
- `scikit-learn`
- `matplotlib`
- `seaborn`
- `openpyxl` (untuk membaca file Excel)

Instalasi dapat dilakukan dengan perintah:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn openpyxl
```

## 5. Cara Menjalankan Notebook

1. **Persiapan Data:**  
   Pastikan file-file Excel berikut berada di direktori yang sama dengan notebook:
   - `fitur_1.xlsx`
   - `fitur_2.xlsx`
   - `fitur_3.xlsx`
   - `target.xlsx`
   - (Untuk ml.ipynb) File dataset gabungan, misalnya `merged_data.xlsx`.

2. **Buka Notebook:**  
   Gunakan Jupyter Notebook atau Jupyter Lab untuk membuka file **main.ipynb** dan **ml.ipynb**.

3. **Jalankan Notebook:**  
   Ikuti langkah-langkah di masing-masing notebook secara berurutan untuk memastikan seluruh proses (dari penggabungan data hingga pembuatan model) berjalan tanpa kendala.

## 6. Manfaat Penelitian

Penelitian ini memiliki manfaat ganda:
- **Ilmiah:**  
  Berkontribusi pada kajian ekonomi pembangunan dan kebijakan sosial, serta menjadi referensi untuk penelitian lanjutan dalam memahami faktor-faktor penyebab kemiskinan.
- **Praktis:**  
  Menyediakan data empiris dan prediksi yang dapat membantu pemerintah dan pembuat kebijakan dalam menentukan prioritas intervensi ekonomi dan sosial untuk pengurangan kemiskinan secara berkelanjutan.
