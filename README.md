# 🌲 GeoForest-AI: Large-Scale Satellite Forest Mapping & Land Cover Classification

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Accelerated-green.svg)](https://xgboost.readthedocs.io/)
[![Rasterio](https://img.shields.io/badge/Rasterio-Geospatial-orange.svg)](https://rasterio.readthedocs.io/)
[![Accuracy](https://img.shields.io/badge/Generalization%20Accuracy-98.30%25-success.svg)](#key-results)

An end-to-end geospatial machine learning pipeline designed to perform scalable binary forest cover classification on multispectral satellite imagery acquired from the **Algerian Space Agency (ASAL)**.

The system processes 12-band GeoTIFF imagery, optimizes feature extraction through spectral band selection, and performs pixel-level inference to reconstruct spatial forest maps with out-of-region generalization.

---

## 📌 Key Highlights & Results

* **Large-Scale Data Pipeline:** Engine trained on **6,000,000 pixel observations** sampled across 4 distinct geographic Wilayas (regions) in Algeria.
* **Dimensionality Reduction:** Reduced feature space from 14 parameters (12 bands + GPS coordinates) down to **4 critical spectral bands** (`Band 12`, `Band 7`, `Band 3`, `Band 6`) while maintaining top-tier classification performance[cite: 20, 21, 22].
* **High Out-of-Region Generalization:** Tested on an unseen, un-sampled region (**Tiaret Dataset**, 1.5M samples), achieving **98.30% accuracy**[cite: 23].
* **Geospatial Export Engine:** Converts tabular predictions back into georeferenced binary raster masks (`.tif`) preserving original spatial metadata.

---

## 📊 Benchmark & Performance Summary

### Model Metrics Across Stages

| Dataset Stage | Features Used | Samples | Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Validation Set** | 14 Features (All Bands + GPS) | 1,200,000[cite: 20] | **99.58%** | 1.00 | 1.00 | 1.00 |
| **Optimized Model** | Top 4 Bands (`B12, B7, B3, B6`) | 1,200,000[cite: 22] | **99.05%**[cite: 22] | 0.99[cite: 22] | 0.99[cite: 22] | 0.99[cite: 22] |
| **Out-of-Region Test (Tiaret)** | Top 4 Bands[cite: 23] | 1,500,000[cite: 23] | **98.30%**[cite: 23] | 0.98[cite: 23] | 0.98[cite: 23] | 0.98[cite: 23] |

### Out-of-Region Confusion Matrix (Tiaret Region)[cite: 23]

```text
               Predicted Non-Forest (0)    Predicted Forest (1)
Actual Non-Forest (0)       737,416[cite: 23]                 12,584[cite: 23]
Actual Forest     (1)        12,907[cite: 23]                737,093[cite: 23]
