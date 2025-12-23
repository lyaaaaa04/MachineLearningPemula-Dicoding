# Machine Learning untuk Pemula - Dicoding 
## Integrasi Clustering dan Klasifikasi pada Data Transaksi Bank  
*(Submission Program Dicoding)*

---

## Deskripsi Proyek
Proyek ini merupakan bagian dari **submission kelas Machine Learning untuk Pemula di Dicoding** yang bertujuan untuk mengimplementasikan **dua pendekatan machine learning**, yaitu **unsupervised learning (clustering)** dan **supervised learning (classification)** dalam satu alur pemodelan.

Pada proyek ini, dilakukan analisis terhadap **dataset transaksi perbankan** untuk:
1. Mengelompokkan data transaksi menggunakan teknik **clustering**
2. Menggunakan hasil clustering sebagai **label (Target)**
3. Membangun model **klasifikasi** untuk memprediksi kelas transaksi berdasarkan fitur yang tersedia

Pendekatan ini mensimulasikan kondisi **dataset tanpa label**, kemudian menghasilkan label secara otomatis melalui clustering.

---

## Tujuan Proyek
- Menerapkan konsep **unsupervised learning (clustering)**
- Menghasilkan label dari data tanpa kelas
- Mengintegrasikan hasil clustering ke dalam **supervised learning**
- Membangun dan mengevaluasi model klasifikasi
- Memahami alur machine learning end-to-end sesuai standar industri dasar

---

## Dataset
Dataset yang digunakan adalah **Bank Transactions Data**, yang menggambarkan perilaku transaksi dan aktivitas keuangan nasabah.

### Karakteristik Dataset
- Jumlah data: 2.537 transaksi
- Tipe data: Numerik & Kategorikal
- Potensi penggunaan:  
  - Analisis perilaku nasabah  
  - Deteksi anomali  
  - Segmentasi pelanggan  

### Fitur Utama (Tidak Termasuk Fitur yang Mengandung Keterangan ID dan IP Address)
- `TransactionAmount` – Nilai transaksi
- `TransactionType` – Debit / Credit
- `Location` – Lokasi transaksi
- `Channel` – Online, ATM, Branch
- `CustomerAge` – Usia nasabah
- `CustomerOccupation` – Pekerjaan
- `TransactionDuration` – Durasi transaksi
- `LoginAttempts` – Jumlah percobaan login
- `AccountBalance` – Saldo setelah transaksi 

---

## Alur Pengerjaan Proyek

### Data Loading & Exploratory Data Analysis (EDA)
- Memuat dataset langsung dari Google Drive
- Menampilkan `head()`, `info()`, dan `describe()`
- Analisis distribusi data numerik
- Visualisasi korelasi dan outlier

---

### Data Preprocessing
Tahapan preprocessing dilakukan secara bertahap sesuai kriteria submission:

- Pengecekan missing value dan duplikasi data
- Feature scaling menggunakan **MinMaxScaler**
- Encoding fitur kategorikal menggunakan **LabelEncoder**
- Drop kolom ID dan IP Address
- Handling missing value
- Handling outlier menggunakan metode IQR
- Feature binning pada:
  - `CustomerAge`
  - `TransactionAmount`

---

## Unsupervised Learning – Clustering

### Metode yang Digunakan
- **K-Means Clustering**

### Langkah-langkah:
- Menentukan jumlah cluster optimal menggunakan **Elbow Method**
- Melatih model K-Means
- Evaluasi menggunakan **Silhouette Score**
- Visualisasi cluster menggunakan **PCA**
- Menyimpan model clustering (`model_clustering.h5`)

### Hasil Clustering
- Jumlah cluster optimal: **3**
- Silhouette Score: **0.54**  
  (menunjukkan kualitas cluster cukup baik)
<Figure size 800x550 with 2 Axes><img width="745" height="507" alt="image" src="https://github.com/user-attachments/assets/1cdb40e0-b6fe-4668-857d-0f2dae0a48f7" />

---

## Interpretasi Cluster
Setiap cluster dianalisis berdasarkan nilai mean, min, dan max dari fitur numerik serta mode fitur kategorikal.

Contoh interpretasi:
- **Cluster 1**: Nasabah dengan transaksi reguler dan saldo menengah  
- **Cluster 2**: Nasabah aktif dengan pola transaksi awal  
- **Cluster 3**: Nasabah dengan transaksi lebih besar dan saldo lebih tinggi  

Hasil clustering kemudian disimpan sebagai kolom **Target** dan diekspor ke file CSV.

---

## Supervised Learning – Klasifikasi

### Tujuan
Membangun model klasifikasi untuk **memprediksi hasil cluster (Target)** berdasarkan fitur transaksi.

### Tahapan:
- Memuat dataset hasil clustering
- Encoding dan scaling ulang fitur
- Train-test split (80:20) dengan stratifikasi
- Membangun model klasifikasi

### Model yang Digunakan
- **Decision Tree Classifier**
- **Random Forest Classifier**
- **Support Vector Machine**
- **Naive Bayes Classifier**

### Hasil Evaluasi Model
| Model | Akurasi | Precision | Recall | F1-Score |
|------|--------|--------|--------|--------|
| Decision Tree Classifier | 1.000000 | 1.000000 | 1.00000 | 1.000000 |
| Random Forest Classifier | 1.000000 | 1.000000 | 1.00000 | 1.000000 |
| Support Vector Machine | 0.956332 | 0.956851 | 0.95679 | 0.956067 |
| Naive Bayes Classifier | 0.986900 | 0.986969 | 0.98694 | 0.986947 |

---

## Kesimpulan
Proyek ini berhasil mengimplementasikan integrasi **unsupervised learning dan supervised learning** dalam satu alur machine learning. Teknik clustering digunakan untuk menghasilkan label pada dataset tanpa kelas, yang kemudian dimanfaatkan sebagai target dalam proses klasifikasi.

Melalui proyek ini, diperoleh pemahaman tentang:
- Pentingnya preprocessing data
- Cara menentukan jumlah cluster optimal
- Interpretasi hasil clustering
- Penggunaan hasil clustering sebagai label untuk klasifikasi

Pendekatan ini sangat relevan untuk kasus nyata seperti **segmentasi nasabah**, **analisis perilaku pengguna**, dan **deteksi pola transaksi**.

---
