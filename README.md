# Temp-Prediction
A comparative time-series analysis predicting daily temperature using Holt-Winters, Facebook Prophet, and XGBoost with Lag Features. Includes feature engineering and model evaluation.

# 🌤️ Comparative Analysis of Weather Forecasting Models

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Kaggle](https://img.shields.io/badge/Dataset-Kaggle-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/)

## 📌 Project Overview
Project ini bertujuan untuk memprediksi suhu harian (**Daily Temperature**) secara akurat menggunakan data historis cuaca. Analisis ini membandingkan efektivitas tiga pendekatan berbeda dalam *Time Series Forecasting*:

1.  **Statistical Method:** Holt-Winters Exponential Smoothing (Triple Exponential Smoothing).
2.  **Automated Forecasting:** Facebook Prophet.
3.  **Machine Learning:** XGBoost Regressor (dengan *Custom Feature Engineering*).

Fokus utama eksperimen ini adalah membuktikan bahwa pendekatan Machine Learning dengan fitur "memori" (*Lag Features*) mampu mengungguli metode statistik tradisional dalam menangkap pola cuaca yang kompleks.

## 📂 Dataset & Kaggle Code
Dataset yang digunakan berisi data cuaca per jam (Hourly) yang mencakup fitur seperti suhu, kelembaban, kecepatan angin, dan tekanan udara.

* **Sumber Dataset:** Weather History Dataset.
* **Link Kaggle:** [👉 Klik disini untuk melihat Notebook/Dataset saya di Kaggle](LINK_KAGGLE_KAMU_DISINI)
    *(Silakan ganti teks ini dengan link profil Kaggle atau link dataset kamu)*

## 🛠️ Methodology

### 1. Data Preprocessing
* **Resampling:** Mengubah data per jam (*hourly*) menjadi rata-rata harian (*daily*) untuk mengurangi noise dan fokus pada tren makro.
* **Cleaning:** Menangani *missing values* dan konversi zona waktu (UTC).
* **Feature Engineering (XGBoost):**
    * `Lag_1`, `Lag_2`, `Lag_7`: Menambahkan fitur suhu 1 hari, 2 hari, dan 1 minggu sebelumnya sebagai konteks.
    * `Rolling_Mean`: Menambahkan tren rata-rata bergerak 3 harian.

### 2. Models Used
* **Holt-Winters:** Dipilih karena kemampuannya menangani *Seasonality* (musiman tahunan) secara eksplisit.
* **Prophet:** Digunakan sebagai pembanding otomatis yang tahan terhadap *outlier*.
* **XGBoost:** Model *Gradient Boosting* yang di-tuning untuk mempelajari pola non-linear dari fitur historis (*lags*).

## 📊 Results Comparison

Evaluasi model dilakukan menggunakan metrik **Root Mean Squared Error (RMSE)**. Berikut adalah hasil eksperimen:

| Model | Type | RMSE (Celcius) | Performance Analysis |
| :--- | :--- | :--- | :--- |
| **Holt-Winters** | Statistik | *[Nilai RMSE HW]* | Cukup baik menangkap pola tahunan, namun kurang responsif pada fluktuasi harian. |
| **Prophet** | Automated | *[Nilai RMSE Prophet]* | Stabil, namun cenderung *underfitting* pada perubahan cuaca ekstrem. |
| **XGBoost** | Machine Learning | **[Nilai RMSE XGB]** | **Best Performance**. Fitur *Lag* sangat membantu model memprediksi suhu berdasarkan konteks hari sebelumnya. |

> *Semakin kecil nilai RMSE, semakin akurat prediksi model.*

## 📈 Visualizations
*(Best Model Performance: XGBoost with Lag Features)*

![Forecast Result](link_gambar_grafik_xgboost_kamu.png)
*Grafik di atas menunjukkan hasil prediksi XGBoost (Merah) yang mampu mengikuti tren data Aktual (Biru) dengan sangat rapat pada data uji.*

## 🚀 How to Run
1.  Clone repository ini:
    ```bash
    git clone [https://github.com/username-kamu/weather-forecasting.git](https://github.com/username-kamu/weather-forecasting.git)
    ```
2.  Install library yang dibutuhkan:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn xgboost statsmodels prophet
    ```
3.  Jalankan notebook:
    ```bash
    jupyter notebook TempPrediction.ipynb
    ```

## 🤝 Conclusion
Dari eksperimen ini, disimpulkan bahwa **XGBoost** dengan *Feature Engineering* yang tepat (Lag & Rolling Window) memberikan hasil prediksi yang paling akurat dibandingkan metode statistik murni. Hal ini menunjukkan pentingnya *contextual features* dalam pemodelan Machine Learning untuk data deret waktu (*time-series*).

---
*Created by [Nama Kamu]*
