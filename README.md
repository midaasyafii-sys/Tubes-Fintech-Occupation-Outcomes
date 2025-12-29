# Tubes-Fintech-Occupation-Outcomes
Tugas Besar Mata Kuliah Analisa Keputusan untuk Teknologi Finansial 

Analisis Risiko Kredit Berbasis Profil Okupasi Menggunakan Machine Learning
1. Pendahuluan
Dalam sektor teknologi finansial (Fintech) dan perbankan, kemampuan memprediksi kelayakan kredit calon nasabah merupakan fondasi utama untuk memitigasi risiko gagal bayar (Non-Performing Loan). Proyek ini berfokus pada Analisis Keputusan Finansial dengan tujuan memprediksi kemampuan bayar (Capacity to Repay) individu berdasarkan profil sosio-ekonomi mereka, dengan penekanan khusus pada variabel pekerjaan (Occupation).

Tantangan utama dalam pemodelan kredit adalah menyeimbangkan antara Akurasi Model (seberapa tepat prediksi) dan Interpretabilitas Keputusan (kemudahan menjelaskan alasan penolakan/penerimaan kredit). Proyek ini menjawab tantangan tersebut melalui pendekatan Data Science yang komprehensif, mulai dari penanganan data yang tidak seimbang hingga simulasi keputusan kredit yang transparan.

2. Tentang Dataset
Proyek ini menggunakan dataset publik Adult Census Income (bersumber dari Kaggle/Census Bureau) sebagai data proksi untuk kelayakan kredit.

Sumber: Data Sensus Biro Statistik.

Fitur Utama: Atribut demografis seperti Occupation (Pekerjaan), Age (Usia), Education (Pendidikan), Marital Status (Status Pernikahan), dan Hours-Per-Week (Jam Kerja).

Target Prediksi: Tingkat Penghasilan (Income).

>50K: Diasumsikan sebagai Low Risk (Kapasitas bayar tinggi/Layak Kredit).

<=50K: Diasumsikan sebagai High Risk (Kapasitas bayar rendah/Berisiko).

Tantangan Data: Data mentah memiliki nilai yang hilang (missing values) dan ketimpangan kelas yang ekstrem (class imbalance), di mana jumlah kelompok berpenghasilan rendah jauh lebih dominan dibandingkan kelompok berpenghasilan tinggi.

3. Metodologi (Alur Pengerjaan)
Proyek ini mengikuti siklus hidup Data Science yang ketat dengan tahapan sebagai berikut:

A. Pra-pemrosesan Data (Data Preprocessing)
Pembersihan Data: Menangani nilai null menggunakan imputasi statistik (Median untuk data numerik dan Modus untuk data kategorikal).

Rekayasa Fitur: Mengubah data kategorikal (teks) menjadi format numerik menggunakan Label Encoding.

Data Splitting: Membagi data menjadi 70% Training Set dan 30% Testing Set.

B. Penanganan Ketimpangan Data (Handling Imbalance)
Menerapkan teknik SMOTE (Synthetic Minority Over-sampling Technique) pada data latih.

Tujuan: Membangkitkan data sintetis untuk kelas minoritas (>50K) agar model tidak bias memprediksi kelas mayoritas saja. Hasilnya, distribusi kelas menjadi seimbang sebelum proses pelatihan.

C. Strategi Pemodelan (Modeling Strategy)
Kami melakukan studi komparasi terhadap tiga algoritma Supervised Learning:

Decision Tree: Sebagai model baseline untuk melihat aturan keputusan yang eksplisit (White-box).

Gradient Boosting: Untuk menguji kemampuan model berbasis boosting dalam meminimalisir error.

Random Forest: Menggunakan pendekatan ensemble bagging untuk memaksimalkan stabilitas dan akurasi.

D. Optimasi Model (Hyperparameter Tuning)
Dilakukan penyetelan parameter secara manual melalui 6 Skenario Eksperimen pada model Random Forest untuk mencari konfigurasi terbaik. Parameter yang diuji meliputi n_estimators (jumlah pohon), max_depth (kedalaman), dan min_samples_split.

4. Hasil Eksperimen dan Evaluasi
Komparasi Model
Berdasarkan pengujian pada data uji (testing set), diperoleh hasil akurasi sebagai berikut:

Decision Tree: ~76%

Gradient Boosting: ~81%

Random Forest: ~88% (Model Terbaik/Champion)

Model Random Forest terpilih karena memiliki akurasi tertinggi dan nilai Recall yang seimbang, artinya model sangat baik dalam mendeteksi nasabah potensial (kelas >50K) tanpa terlalu banyak kesalahan prediksi.

Faktor Penentu (Feature Importance)
Analisis model menunjukkan bahwa faktor terpenting dalam menentukan kelayakan kredit bukanlah pekerjaan semata, melainkan:

Marital Status (Status Pernikahan): Indikator stabilitas finansial.

Age (Usia): Indikator kematangan karir.

Education (Pendidikan): Indikator potensi pendapatan.

5. Simulasi dan Deployment
Sebagai langkah akhir untuk membuktikan nilai bisnis (Business Value):

Simulasi Traffic Light System: Dikembangkan antarmuka simulasi interaktif yang menerjemahkan probabilitas matematis menjadi status yang mudah dipahami manajer bank:

🟢 Hijau: Approved (Probabilitas > 70%).

🔵 Biru: Manual Review (Probabilitas 40-70%).

🔴 Merah: Rejected (Probabilitas < 40%).

Model Deployment: Model terbaik disimpan dalam format .pkl (Pickle) dan telah diuji kemampuannya untuk memuat ulang (load) serta memprediksi data nasabah baru yang belum pernah dilihat sebelumnya.

6. Kesimpulan
Proyek ini berhasil membangun sistem Credit Scoring cerdas dengan akurasi 88.01% menggunakan algoritma Random Forest yang telah dioptimasi (Skenario 5). Sistem ini tidak hanya akurat secara teknis, tetapi juga interpretatif melalui fitur simulasi keputusan, sehingga siap digunakan sebagai alat pendukung keputusan (Decision Support System) di industri finansial.

---
*Note: This repository is currently under active development. Results and deployment instructions will be updated soon.*
