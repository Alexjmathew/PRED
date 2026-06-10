# ✈️ Zero Downtime: Predictive Maintenance for NASA Turbofan Engines

![Python](https://img.shields.io/badge/Python-3.10-blue.svg)
![LightGBM](https://img.shields.io/badge/LightGBM-Enabled-brightgreen.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

## 📌 Overview
This project develops a machine learning pipeline to predict the **Remaining Useful Life (RUL)** of turbofan engines using the NASA CMAPSS (Commercial Modular Aero-Propulsion System Simulation) dataset. By accurately forecasting engine degradation, this solution enables proactive maintenance, minimizing unexpected failures and reducing operational downtime.

The pipeline processes multivariate sensor data (subset FD001), extracts critical degradation signals, benchmarks multiple regression models, and culminates in a simulated "Digital Twin" for real-time engine monitoring.

## 📊 Dataset
* **Source:** NASA CMAPSS Dataset (FD001 Subset)
* **Features:** 21 sensor readings (temperature, pressure, fan speed, etc.) and 3 operational settings recorded per engine cycle.
* **Target Variable:** Remaining Useful Life (RUL) — the number of operational cycles remaining before engine failure.

## ⚙️ Methodology & Pipeline

### 1. Feature Engineering
* **Dead Sensor Removal:** Identified and dropped sensors with zero variance (`nunique() <= 1`) to eliminate noise and reduce dimensionality.
* **RUL Clipping:** Capped the maximum RUL at **125 cycles**. This is a crucial domain-specific step that prevents the model from over-penalizing early-stage predictions, forcing it to focus strictly on the physical degradation phase.
  


### 2. Exploratory Data Analysis (EDA)
* <img width="1127" height="453" alt="image" src="https://github.com/user-attachments/assets/a4fbdb62-2b5e-435e-9950-5222b26331ae" />
* **Correlation Analysis:** Identified the top 5 most informative sensors heavily correlated with engine failure.
* <img width="946" height="697" alt="image" src="https://github.com/user-attachments/assets/ec08ac1c-074b-4395-9e15-ca2a69167bf9" />

* **State Separation (KDE):** Visualized the divergence between healthy (early cycles) and failing (late cycles) sensor distributions.
* **PCA Trajectory:** Mapped high-dimensional sensor data into a 2D Principal Component space to visually track the degradation trajectory over time.

### 3. Model Benchmarking
Data was normalized using a `MinMaxScaler` (fitted strictly on the training set to prevent data leakage). We benchmarked four distinct regression models:
* **Linear Regression** (Baseline)
* **Random Forest**
* **XGBoost**
* **LightGBM**
  <img width="1245" height="482" alt="image" src="https://github.com/user-attachments/assets/aed9e585-fc3b-4b0e-826e-693ce3483b79" />



