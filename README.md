# Tubes-Fintech-Occupation-Outcomes
Tugas Besar Mata Kuliah Analisa Keputusan untuk Teknologi Finansial 

# 💰 Analisis Risiko Kredit & Prediksi Kapasitas Bayar (Credit Scoring AI)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Pendahuluan (*Project Overview*)
Dalam industri *Fintech* dan Perbankan, kemampuan memprediksi kelayakan kredit calon nasabah (*Creditworthiness*) adalah aset strategis untuk memitigasi risiko gagal bayar (*Non-Performing Loan*). 

Proyek ini bertujuan untuk memprediksi Kapasitas Bayar (*Capacity to Repay*) seseorang berdasarkan profil sosio-ekonomi mereka, dengan penekanan pada variabel Pekerjaan (*Occupation*), Pendidikan, dan Usia. Kami menggunakan pendekatan *Data Science* untuk menjawab tantangan strategis: menyeimbangkan antara Akurasi Model dan Interpretabilitas Keputusan.

---

## 📂 Tentang Dataset
Proyek ini menggunakan dataset publik **Adult Census Income** (sumber: Kaggle/Census Bureau) yang berfungsi sebagai proksi data kredit.

* **Fitur (*Features*):** Atribut demografis meliputi `Occupation`, `Workclass`, `Education`, `Age`, `Marital Status`, dan `Hours-Per-Week`.
* **Target:** Tingkat Penghasilan (`Income`).
    * `>50K` : Diasumsikan sebagai **Low Risk** (Layak Kredit).
    * `<=50K`: Diasumsikan sebagai **High Risk** (Berisiko Tinggi).
* **Tantangan Data:** Dataset mentah memiliki *missing values* yang signifikan dan ketimpangan kelas (*class imbalance*) yang ekstrem (76% vs 24%), mensimulasikan kondisi nyata data perbankan.

---

## 🛠️ Metodologi (*Methods Used*)
Proyek ini mengikuti siklus hidup *Data Science* yang ketat (*Rigorous Lifecycle*):

### 1. Pra-pemrosesan Data (*Data Preprocessing*)
* **Handling Missing Values:** Imputasi menggunakan *Median* (numerik) dan *Mode* (kategorikal).
* **Data Cleaning:** Pembersihan inkonsistensi data dan duplikasi.
* **Encoding:** Transformasi variabel kategorikal menjadi numerik (*Label Encoding*).

### 2. Exploratory Data Analysis (EDA)
* Visualisasi distribusi pendapatan antar profesi.
* Analisis statistik deskriptif untuk memahami faktor risiko dominan.

### 3. Penanganan Imbalance (*Data Preparation*)
* Menerapkan **SMOTE (Synthetic Minority Over-sampling Technique)**.
* Langkah ini krusial untuk mencegah bias model terhadap kelas mayoritas, memastikan model mampu "belajar" mengenali nasabah kaya (minoritas) dengan lebih baik.

### 4. Strategi Pemodelan (*Modeling Strategy*)
Kami melakukan komparasi terhadap tiga algoritma *Supervised Learning*:
* **Decision Tree:** Model *White-box* untuk mengekstrak aturan keputusan eksplisit.
* **Gradient Boosting:** Model *Ensemble* untuk meminimalkan error prediksi.
* **Random Forest:** Model *Ensemble Bagging* untuk memaksimalkan akurasi dan stabilitas.

### 5. Optimasi Model (*Hyperparameter Tuning*)
Dilakukan penyetelan parameter secara manual menggunakan **6 Skenario Eksperimen** pada model *Random Forest* dengan memvariasikan parameter:
* `n_estimators` (Jumlah Pohon: 100, 200, 300)
* `max_depth` (Kedalaman: 10, 20, 30, None)
* `min_samples_split` (Split Node: 2, 5, 10)

---

## 📊 Hasil dan Evaluasi

### 1. Komparasi Performa Model
Berdasarkan pengujian pada *Testing Set* (30% data):

| Model | Akurasi | Keterangan |
| :--- | :--- | :--- |
| Decision Tree | ~76.04% | Baseline |
| Gradient Boosting | ~81.18% | Challenger |
| **Random Forest** | **~88.01%** | **Champion (Terbaik)** |

### 2. Hasil Optimasi (Skenario Terbaik)
Dari 6 skenario optimasi manual, **Skenario 5** terpilih sebagai konfigurasi paling optimal:
* **Setting:** `n_estimators=300`, `max_depth=None`, `min_samples_split=2`.
* **Hasil:** Mencapai akurasi tertinggi (**88.01%**) dengan stabilitas yang baik terhadap data *unseen*.

### 3. Faktor Penentu (*Feature Importance*)
Analisis menunjukkan 3 indikator utama kelayakan finansial:
1.  **Marital Status:** Indikator stabilitas sosial-ekonomi.
2.  **Age:** Indikator kematangan karir dan aset.
3.  **Education/Occupation:** Indikator potensi pendapatan.

---

## 🚦 Simulasi Bisnis & Deployment
Untuk meningkatkan nilai bisnis (*Business Value*), proyek ini dilengkapi dengan:

### A. Simulasi "Traffic Light System"
Menerjemahkan probabilitas matematis menjadi rekomendasi keputusan yang mudah dipahami manajer bank:
* ✅ **HIJAU (Approved):** Probabilitas > 70%.
* ⚠️ **BIRU (Manual Review):** Probabilitas 40% - 70%.
* ⛔ **MERAH (Rejected):** Probabilitas < 40%.

### B. Deployment
* Model terbaik disimpan dalam format `.pkl` (*Pickle*).
* Dilakukan pengujian pemuatan ulang (*loading*) dan tes prediksi menggunakan data nasabah buatan (*dummy*) untuk memastikan model siap produksi.

---

## 🚀 Cara Menjalankan Project
1.  Jalankan Notebook secara berurutan dari Blok 1 (Load Data) hingga Blok 6 (Deployment).
2.  Gunakan fitur **Simulasi Interaktif** di bagian akhir untuk menguji profil nasabah secara acak.

---
### KESIMPULAN
Proyek ini berhasil membangun sistem Credit Scoring cerdas dengan akurasi 88.01% menggunakan algoritma Random Forest yang telah dioptimasi (Skenario 5). Sistem ini tidak hanya akurat secara teknis, tetapi juga interpretatif melalui fitur simulasi keputusan, sehingga siap digunakan sebagai alat pendukung keputusan (Decision Support System) di industri finansial.

---
*Note: This repository is currently under active development. Results and deployment instructions will be updated soon.*
