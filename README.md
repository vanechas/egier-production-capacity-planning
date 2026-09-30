# 🎒 Bag Production Trend Analysis & Capacity Planning

Proyek analisis data dan peramalan (*forecasting*) tren produksi tas industri (**EGIER**) selama rentang waktu 144 bulan (12 tahun). Proyek ini memanfaatkan pemodelan **Polynomial Regression (Degree 3)** untuk memodelkan kurva pertumbuhan produksi non-linear dan algoritma optimasi numerik **Newton-Raphson** guna menentukan estimasi waktu ekspansi kapasitas gudang penyimpanan secara presisi.

---

## 📌 Ringkasan Proyek & Studi Kasus

Seiring dengan meningkatnya permintaan pasar, kapasitas fasilitas produksi dan penyimpanan menjadi faktor krusial dalam menjaga kelancaran rantai pasok (*supply chain*). Proyek ini berfokus pada:
1. **Analisis Data Historis:** Mengevaluasi pola pertumbuhan produksi tas bulanan dari bulan ke-1 ($M_1$) hingga bulan ke-144 ($M_{144}$).
2. **Pemodelan Regresi Polinomial:** Menyesuaikan data runtun waktu ke dalam fungsi polinomial derajat 3 ($y = ax^3 + bx^2 + cx + d$) untuk menangkap tren percepatan produksi.
3. **Evaluasi Akurasi Model:** Mengukur performa kecocokan kurva (*goodness of fit*) menggunakan metrik $R^2$, Mean Squared Error (MSE), dan Root Mean Squared Error (RMSE).
4. **Perencanaan Kapasitas Gudang (*Capacity Planning*):** Menghitung titik waktu ketika volume produksi melebihi ambang batas kapasitas gudang maksimum (25.000 unit), serta menghitung waktu mulai pembangunan (*lead time* 13 bulan) agar fasilitas baru siap tepat waktu.

---

## 📈 Persamaan Model & Hasil Analisis

### 1. Persamaan Polinomial (Orde 3)
Berdasarkan optimasi *least-squares polynomial fit*, diperoleh fungsi aproksimasi produksi:

$$\hat{y}(x) = 0.004x^3 - 0.134x^2 + 47.22x + 1749$$

*(di mana $x$ adalah indeks bulan dan $\hat{y}$ adalah estimasi jumlah produksi tas).*

### 2. Metrik Evaluasi Model
Model polinomial derajat 3 menunjukkan akurasi yang sangat tinggi terhadap data aktual:
* **Koefisien Determinasi ($R^2$):** **0.996** (model mampu menjelaskan 99.6% varians data produksi)
* **Mean Squared Error (MSE):** `83,195.127`
* **Root Mean Squared Error (RMSE):** `288.436 unit`

---

## 🏭 Keputusan Bisnis: Perencanaan Gudang Baru

* **Kapasitas Maksimum Gudang Saat Ini:** $25.000$ unit/bulan
* **Durasi Pembangunan Gudang Baru (*Lead Time*):** $13$ bulan
* **Hasil Perhitungan Numerik (Newton-Raphson):**
  * Produksi diestimasikan melampaui $25.000$ unit pada **Bulan ke-168**.
  * Pembangunan gudang baru harus mulai direalisasikan paling lambat pada **Bulan ke-155** ($168 - 13$) agar tidak terjadi *overcapacity* atau kendala operasional logistik.

---

## 🛠️ Tech Stack & Pustaka

* **Bahasa Pemrograman:** Python 3.x
* **Manipulasi & Analisis Data:** `Pandas`, `NumPy`
* **Visualisasi Data:** `Matplotlib`
* **Metode Numerik:** `scipy` / implementasi kustom `Newton-Raphson Method`

---

## 📁 Struktur Direktori

```text
├── data/
│   └── aol_data.csv          # Dataset historis produksi 144 bulan
├── notebook/
│   └── bag_production.ipynb  # Notebook analisis, pemodelan, dan grafik
├── assets/                   # Grafik tren dan visualisasi perencanaan gudang
├── README.md                 # Dokumentasi proyek
└── requirements.txt          # Daftar dependensi Python
```
