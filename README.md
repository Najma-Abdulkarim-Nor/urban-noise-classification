<div align="center">

# 🔊 Urban Noise Monitoring and Classification Using Machine Learning and Deep Learning

**Najma Nour**¹ · **Maryam Alblooshi**¹ · **Khalid Elgazzar**²

¹Canadian University Dubai, UAE &nbsp;&nbsp;·&nbsp;&nbsp; ²IoT Research Laboratory, Ontario Tech University, Canada

**2026 IEEE International Conference on Smart Mobility (SM2026)** · Al Alamein City, Egypt · 11–13 May 2026

[![Paper](https://img.shields.io/badge/IEEE%20Xplore-Paper-00629B?logo=ieee&logoColor=white)](https://ieeexplore.ieee.org/document/11614142)
[![DOI](https://img.shields.io/badge/DOI-10.1109%2FSM69703.2026.11614142-blue)](https://doi.org/10.1109/SM69703.2026.11614142)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)

</div>

---

## 📝 Abstract

> Urban environmental noise threatens public health and complicates smart city management. This paper presents a comparative evaluation of three classifiers — Random Forest (RF), Support Vector Machine (SVM), and Convolutional Neural Network (CNN) — for automated urban sound classification using the UrbanSound8K dataset. A hybrid feature extraction pipeline of MFCCs, Chroma, Spectral Centroid, and Spectral Rolloff feeds the classical models, while a Mel-spectrogram representation feeds the CNN. Experimental results show the CNN achieves the highest accuracy (**97.1%**), followed by RF (**91.4%**) and SVM (**88.6%**), highlighting the value of deep representation learning for real-time traffic noise analysis and smart mobility applications.

## 🔑 Highlights

- 🏆 **CNN reaches 97.1% test accuracy**, outperforming classical RF/SVM baselines on a 3-class UrbanSound8K subset (`car_horn`, `jackhammer`, `siren`)
- 🧠 **Hybrid feature pipeline** — hand-crafted MFCC/Chroma/Spectral features for classical models vs. learned Mel-spectrogram representations for the CNN
- ⚡ **Lightweight, edge-deployable models** — designed for real-time smart-city acoustic sensor deployment, not just offline benchmarking
- 🎛️ **Interactive Gradio demo** included — classify your own `.wav` file with any of the three trained models
- 🔁 **Fully reproducible** — fixed seed (42), stratified splits, documented hyperparameters throughout

## 📊 Results

| Model | Accuracy | Macro F1 | Notes |
|:---|:---:|:---:|:---|
| Random Forest | 91.4% | 0.92 | 150 trees, hybrid hand-crafted features — strong in resource-constrained settings |
| SVM (RBF) | 88.6% | — | Most sensitive to overlapping acoustic features (siren ↔ car horn) |
| **CNN** | **97.1%** | — | 3-block Conv2D on Mel-spectrograms — best overall, real-time capable |

Most classification errors occurred between `siren` and `car_horn` (spectral similarity), while `jackhammer` achieved high recall due to its distinctive broadband signature. Full precision/recall/F1 breakdowns and confusion matrices are generated in the notebook.

## 🧩 Method Overview
