# Predict Customer Personality to Boost Marketing Campaign by Using Machine Learning

**Dibuat oleh:** Muhammad Hilmi Thabibi[cite: 1]  
**Kontak & LinkedIn:** [Ymuhammadhilmithabibi@gmail.com](mailto:Ymuhammadhilmithabibi@gmail.com) | [LinkedIn Profile](https://www.linkedin.com/in/muhammad-hilmi-thabibi-0647161b9/)[cite: 1]  
**Didukung oleh:** Rakamin Academy[cite: 1]

---

## 📌 Latar Belakang & Pernyataan Masalah
Sebuah perusahaan dapat berkembang pesat jika memahami perilaku kepribadian pelanggannya[cite: 2]. Hal ini memungkinkan perusahaan memberikan layanan yang lebih baik kepada pelanggan yang berpotensi loyal[cite: 2]. Namun, perusahaan sering kali kesulitan mengidentifikasi pelanggan mana yang paling mungkin merespons kampanye pemasaran[cite: 3]. Mengirimkan kampanye kepada seluruh pelanggan tanpa pandang bulu hanya akan memboroskan anggaran dan menurunkan ROI (Return on Investment)[cite: 3].

**Problem Statement:**  
Bagaimana kita dapat menggunakan *machine learning* untuk mengidentifikasi segmen kepribadian pelanggan yang berbeda, dan segmen mana yang harus diprioritaskan untuk pemasaran ulang (*retargeting*) guna memaksimalkan ROI kampanye?[cite: 3]

---

## 🎯 Tujuan Proyek
1. Melakukan *feature engineering* pada tingkat konversi, kelompok usia, dan fitur pengeluaran[cite: 3].
2. Melakukan *Exploratory Data Analysis* (EDA) untuk memahami perilaku pelanggan dan efektivitas kampanye[cite: 3].
3. Membersihkan data dengan menangani nilai yang hilang, duplikat, dan *outliers*[cite: 3].
4. Mengaplikasikan *feature encoding* dan standardisasi agar data siap untuk pemodelan[cite: 3].
5. Menentukan jumlah kluster yang optimal menggunakan *Elbow Method*[cite: 3].
6. Mengimplementasikan *K-Means clustering* dan mengevaluasinya dengan *Silhouette Score*[cite: 3].
7. Menginterpretasikan profil kluster dan mengidentifikasi kandidat untuk *retargeting*[cite: 3].
8. Menghitung potensi dampak bisnis dari pemasaran yang ditargetkan[cite: 3].

---

## 🛠️ Dataset & Metodologi Pipeline
Proyek ini menggunakan dataset yang berisi 2.240 pelanggan dengan 29 fitur asli yang mencakup demografi, perilaku pengeluaran, dan riwayat kampanye[cite: 3, 4]. 

**Pipeline Proyek:**
1. Data Loading[cite: 4]
2. Data Cleaning[cite: 4]
3. Feature Engineering[cite: 4]
4. Feature Encoding[cite: 4]
5. Feature Scaling[cite: 4]
6. K-Means Clustering[cite: 4]
7. Cluster Evaluation[cite: 4]
8. EDA per Cluster[cite: 4]
9. Retargeting & Impact[cite: 4]

---

## 🧹 Pra-Pemrosesan Data
*   **Penanganan Nilai yang Hilang:** Terdapat 24 nilai yang hilang (1,07%) pada kolom `Income`, yang kemudian diisi (imputasi) menggunakan nilai median[cite: 6].
*   **Penghapusan Outlier:** Menghapus 3 data pelanggan yang lahir pada atau sebelum tahun 1900, dan 1 data dengan anomali pendapatan ekstrem di atas 200 Juta IDR[cite: 7]. Total baris akhir setelah pembersihan adalah 2.212 baris (tingkat retensi 98,75%)[cite: 7].
*   **Analisis Fitur Tambahan (EDA):** Ditemukan bahwa usia bukanlah prediktor yang signifikan terhadap tingkat konversi[cite: 5]. Sebaliknya, tingkat pendapatan (*Income Tier*) dan tingkat pengeluaran (*Spend Tier*) sangat signifikan mendorong konversi pelanggan[cite: 5].
*   **Encoding & Standarisasi:** Kolom `Education` diubah menggunakan *Ordinal Encoding*, sedangkan `Marital_Status` menggunakan *One-Hot Encoding*[cite: 8]. Pemodelan menggunakan *StandardScaler (Z-score)* agar variabel berskala besar seperti pendapatan tidak mendominasi model[cite: 9].

---

## 🤖 Pemodelan (K-Means Clustering)
*   Berdasarkan grafik *Elbow Method*, titik patahan (*elbow point*) menunjukkan bahwa jumlah kluster optimal adalah $k=4$[cite: 11].
*   Nilai evaluasi rata-rata *Silhouette Score* untuk model ini adalah 0,2023[cite: 12].

### Interpretasi Profil Kluster
Model berhasil mengidentifikasi 4 segmen pelanggan yang berbeda[cite: 14]:
*   **C0 - Mid-High Spender (n=622):** Pelanggan dewasa (~50 tahun) dengan pengeluaran menengah-tinggi (~857 Ribu IDR) dan pendapatan ~61 Juta IDR[cite: 14]. Mereka adalah target yang baik untuk *upsell* dan program loyalitas[cite: 14].
*   **C1 - Premium Buyer (n=488):** Memiliki pendapatan tertinggi (~79 Juta IDR) dan pengeluaran rata-rata tertinggi (~1,39 Juta IDR)[cite: 14, 15]. Kelompok ini paling responsif dan menjadi prioritas utama[cite: 14].
*   **C2 - Low Engagement (n=633):** Pelanggan dengan pendapatan rendah (~30 Juta IDR) dan pengeluaran rendah (~112 Ribu IDR), namun memiliki kunjungan web yang tinggi (6,9 kali/bulan)[cite: 14]. Perlu optimalisasi *funnel* (alur konversi)[cite: 14].
*   **C3 - Family Budget (n=469):** Segmen dengan jumlah anak terbanyak (1,9) dan anggaran paling ketat[cite: 14]. Cocok untuk promo paket produk keluarga[cite: 14].

---

## 📈 Rekomendasi Bisnis & Potensi Dampak (ROI)
Berdasarkan analisis *response rate* dan rata-rata pengeluaran, prioritas *retargeting* kampanye difokuskan pada dua kluster utama[cite: 17]:
1.  **Target Utama (C1 - Premium Buyer):** Memiliki *response rate* tertinggi (27,7%) dengan estimasi potensi **ROI sebesar 670%**[cite: 17, 18].
2.  **Target Sekunder (C0 - Mid-High Spender):** Memiliki tingkat respons yang baik (14,3%) dengan **ROI sebesar 145%**[cite: 17, 18].
3.  **Prioritas Rendah (C2 & C3):** Kampanye pemasaran pada segmen ini dihentikan sementara atau menggunakan strategi organik, karena simulasi biaya promosi berbayar pada kelompok ini menghasilkan ROI negatif (-74% dan -81%)[cite: 17, 18].

**Dampak Bisnis Keseluruhan:**
Dengan menargetkan gabungan kluster C1 dan C0 (total 1.110 pelanggan), perusahaan diproyeksikan mencapai persentase *response rate* rata-rata sebesar 21,1%[cite: 17]. Estimasi ini akan menghasilkan *Net Revenue* sebesar **208,5 Juta IDR**, dengan total pengembalian kampanye **(ROI) sebesar 376%**[cite: 18].

---

## 💻 Source Code
Seluruh analisis dalam presentasi ini sepenuhnya dapat direproduksi dari *notebook* berikut:  
`conversion_rate_analysis.ipynb`[cite: 20]  
[Link Google Drive Menuju Notebook](https://drive.google.com/file/d/1psDJiTwVbaBkxxMhOvA9nSkKBHI_azsk/view?usp=sharing)[cite: 20]