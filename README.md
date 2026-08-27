<div align="center">
  
  <img src="https://img.icons8.com/external-solid-design-circle/100/00e5ff/external-Geology-mining-solid-design-circle.png" alt="Geology AI Logo" width="80" />

  # 🌐 Geological AI Engine
  **Industrial Mineral Prospectivity Mapping & Exploration Pipeline**

  <p align="center">
    <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.11+-050507?style=for-the-badge&logo=python&logoColor=00e5ff" alt="Python"></a>
    <a href="https://scikit-learn.org/"><img src="https://img.shields.io/badge/scikit--learn-Enabled-050507?style=for-the-badge&logo=scikit-learn&logoColor=00e5ff" alt="Scikit-Learn"></a>
    <a href="https://xgboost.readthedocs.io/"><img src="https://img.shields.io/badge/XGBoost-Optimized-050507?style=for-the-badge&logo=xgboost&logoColor=ff3366" alt="XGBoost"></a>
    <a href="https://qgis.org/"><img src="https://img.shields.io/badge/QGIS-Spatial_Analysis-050507?style=for-the-badge&logo=qgis&logoColor=00e5ff" alt="QGIS"></a>
  </p>

  > Advanced machine learning architecture for high-resolution copper and gold deposit prediction in the Banswara-Bhilwara region, utilizing multi-layered geological, geochemical, and geophysical telemetry.
  
</div>

---

## 🚀 Executive Summary

Traditional prospecting methods struggle with the extreme multidimensionality of geological factors. This engine digitizes and automates the **Mineral Systems Approach**, leveraging **Random Forest** and **XGBoost** algorithms to process bedrock samples and lithogeochemical data from Geological Survey of India (GSI) exploration reports. 

By stacking ensemble models, the engine generates high-fidelity prospectivity maps that isolate critical exploration targets with >90% precision.

## ⚙️ Core Architecture & Pipeline

The pipeline is built on a Human-in-the-Loop (HITL) and AI-stacked methodology, converting raw geospatial data into actionable commercial mining targets.

1. **Data Ingestion & Balancing:** Extracts G2, G3, and G4 stage exploration reports. Implements a 3km buffer exclusion zone to generate balanced non-mineralized reference points.
2. **Feature Engineering (17-Layer Matrix):**
   * **Lithology:** 14 grouped geological classifications (Bhukosh 1:50,000).
   * **Structural:** 1st-order (10km buffered) and 2nd-order (7km buffered) lineaments.
   * **Alteration Indices:** ASTER band ratios (Ferric B2/B1, Ferrous B5/B4, Kaolin B6/B5).
   * **Geochemistry:** PCA-optimized stream sediment trace elements (Cu, Au, As, Pb, Zn, Th, etc.).
   * **Geophysics:** Reduced-to-Pole (RTP) magnetic and residual gravity anomalies (<500m).
3. **Model Stacking:** Independent Random Forest and XGBoost models are trained across 5 K-Fold datasets. The final output is a combined consensus score from `0` (Barren) to `5` (Maximum Prospectivity).

---

## 📊 Performance Metrics

The engine underwent rigorous out-of-sample validation, achieving exceptional discriminatory power across both target minerals.

| Target Mineral | Algorithm | Average Accuracy | Average ROC AUC | Key Geochemical Vectors |
| :--- | :--- | :---: | :---: | :--- |
| **Copper (Cu)** | Random Forest | **91.8%** | **95.1%** | `Fe2O3`, `Cr2O3`, `MgO`, `Gravity` |
| **Copper (Cu)** | XGBoost | **89.4%** | **95.0%** | `Lineaments`, `MgO`, `Cr2O3` |
| **Gold (Au)** | Random Forest | **93.8%** | **97.8%** | `Th`, `Na2O`, `Cu`, `RTP Mag` |
| **Gold (Au)** | XGBoost | **90.6%** | **95.4%** | `Th`, `Na2O`, `Lineaments` |

---

## 🎯 Verified Exploration Targets

Based on the 5-point consensus stacking algorithm, the following zones have been flagged for immediate commercial evaluation and core drilling:

### 🟡 Gold (Au) Primary Targets
* Salumbar-Dhariwad-Barwali Extension of Bhukiya-Japura
* Dhosar-Sopura Block
* Phalet-Kurabad Block
* Kapasan-South Dariba Block

### 🟠 Copper (Cu) Primary Targets
* Khemli-Nandwel-Kurabad Extension
* Narwali Block & Dhariwad Block
* Gangapur-Surawas-Pahooni Block

---

## 📂 Repository Structure

<details>
<summary><b>Click to expand directory tree</b></summary>

```text
├── Data/
│   ├── Copper/
│   │   ├── CuTS01.csv to CuTS05.csv     # Balanced training locations
│   └── Gold/
│       ├── AuTS01.csv to AuTS05.csv     # Balanced training locations
├── Features/                            
│   └── BP1.tif to BP17.tif              # Rescaled/resampled 100x100m predictor maps
├── Models/
│   ├── random_forest_model.joblib       # Production-ready serialized RF model
│   └── xgboost_model.joblib             # Production-ready serialized XGB model
├── Notebooks/
│   ├── Copper/
│   │   ├── CuPyML_TS01.ipynb            # Random Forest Training Pipeline
│   │   └── CuPyML_TS01XGB.ipynb         # XGBoost Training Pipeline
│   └── Gold/
│       ├── Au_ML_TS01.ipynb             # Random Forest Training Pipeline
│       └── Au_ML_TS01XGB.ipynb          # XGBoost Training Pipeline
├── Outputs/
│   ├── CuTS01_prediction.tif            # Rendered Raster Maps
│   └── XGBTS01_au.tif                   
└── README.md
