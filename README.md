# 🎯 Final Project — Rating Prediction Recommender System (Option 1)
Mata Kuliah: **12S4054 – Recommendation System**  
Institut Teknologi Del  
Semester: **Odd 2025/2026**

---

## 📘 Deskripsi Proyek
Project ini merupakan implementasi dari **Option 1: Rating Prediction (Explicit Feedback)** pada tugas akhir mata kuliah Recommender System.  
Tujuan utama project ini adalah membangun sistem rekomendasi yang mampu **memprediksi rating** yang akan diberikan user terhadap sebuah item menggunakan dataset Amazon 2023 Challenge (FIT512 S1 2025).

---

## 📂 Dataset
Dataset diambil dari kompetisi Kaggle:

- **train.csv** → berisi user_id, product_id, rating, dan metadata produk  
- **test.csv** → berisi pasangan user–product tanpa rating (harus diprediksi)
- **sample_submission.csv** → format submission Kaggle

### Struktur train.csv:

| Kolom | Deskripsi |
|-------|-----------|
| user_id | ID user unik |
| product_id | ID produk unik |
| product_name | Nama produk (metadata) |
| rating | Rating 1–5 (target prediksi) |
| votes | Jumlah vote produk (metadata) |
| helpful_votes | Jumlah helpful vote |
| ID | Index |

Dataset bersifat **explicit rating** dan sangat **sparse** (>99%).

---

## 📊 Exploratory Data Analysis (EDA)

### 🔹 Statistik Dataset
- Jumlah rating: **745.889**
- Jumlah user unik: **2.000**
- Jumlah item unik: **201.325**
- Sparsity: **~99.81%**

### 🔹 Distribusi Rating
Rating sangat condong ke nilai tinggi:
- Rating 5 mendominasi (>55%)
- Rating 4 kedua terbanyak

### 🔹 Analisis Aktivitas
- Beberapa user sangat aktif memberi rating.
- Banyak item hanya menerima 1 rating → dataset sangat sparse.

### 🔹 Sparsity Matrix Visualization
Spy plot menunjukkan bahwa hampir seluruh user-item matrix kosong — tipikal dataset e-commerce skala besar.

---

## ⚙️ Metode yang Digunakan

Project ini menggunakan dua pendekatan utama:

---

## 1️⃣ **Baseline Collaborative Filtering**

### ✔ User-Based Collaborative Filtering  
- Menghitung similarity antar user (cosine similarity)  
- Prediksi rating berdasarkan tetangga user (top-k)

### ✔ Item-Based Collaborative Filtering  
- Menghitung similarity antar item  
- Prediksi rating berdasarkan item mirip yang pernah dirating user

### 📏 Evaluasi Baseline  
Metric: **RMSE (Root Mean Squared Error)**  
Baseline digunakan sebagai model pembanding sebelum membuat model advanced.

---

## 2️⃣ **Model Advanced — Matrix Factorization (SVD)**

Menggunakan library *Surprise*, model **SVD** dibangun untuk:
- Menangani sparsity
- Menangkap struktur latent user–item
- Menghasilkan prediksi yang lebih akurat daripada baseline

SVD biasanya memberikan RMSE jauh lebih rendah dibanding CF memory-based.

---

## 🧪 Evaluasi & Hasil

- Evaluasi dilakukan menggunakan validasi 80/20 pada train.csv  
- Metric utama: **RMSE**  
- Hasil model dibandingkan:
  - User-Based CF  
  - Item-Based CF  
  - SVD (model terbaik)

Model SVD dipilih untuk menghasilkan prediksi final pada test.csv.

---

## 📤 Submission Kaggle
File submission yang dihasilkan:

