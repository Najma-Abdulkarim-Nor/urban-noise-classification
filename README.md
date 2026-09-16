# Urban Noise Monitoring and Classification

[![Published in IEEE Xplore](https://img.shields.io/badge/Published-IEEE%20Xplore-00629B?logo=ieee&logoColor=white)](https://ieeexplore.ieee.org/document/11614142) [![DOI](https://img.shields.io/badge/DOI-10.1109%2FSM69703.2026.11614142-blue)](https://doi.org/10.1109/SM69703.2026.11614142)

Comparative evaluation of **Random Forest**, **SVM**, and a **CNN** for automated urban sound classification, built on the UrbanSound8K dataset. This work was published at the **2026 IEEE International Conference on Smart Mobility (SM2026)**, held 11–13 May 2026 in Al Alamein City, Egypt, and is now indexed in IEEE Xplore.

📄 **Paper:** [ieeexplore.ieee.org/document/11614142](https://ieeexplore.ieee.org/document/11614142) &nbsp;|&nbsp; **DOI:** [10.1109/SM69703.2026.11614142](https://doi.org/10.1109/SM69703.2026.11614142)

## Overview

Urban noise pollution — from traffic, construction, and emergency sirens — degrades quality of life and is difficult to manage without automated, real-time source identification. This project implements and compares three classifiers on three acoustically distinct UrbanSound8K classes (`car_horn`, `jackhammer`, `siren`) to evaluate their suitability for real-time smart-city acoustic monitoring, using Dubai as the motivating use case.

| Model | Accuracy | Notes |
|---|---|---|
| Random Forest | **91.4%** | Hybrid hand-crafted features; strong in resource-constrained settings |
| SVM (RBF) | **88.6%** | Most sensitive to overlapping acoustic features (siren vs. car horn) |
| CNN | **97.1%** | Learns directly from mel-spectrograms; best overall performance |

## Methodology

- **Dataset:** UrbanSound8K, stratified subset of 70 clips per class (210 total), 80/20 train/test split, fixed seed (42) for reproducibility.
- **Classical models (RF, SVM):** 23-D hand-crafted feature vector — 20 MFCCs (mean), mean Chroma, Spectral Centroid, Spectral Rolloff — standardized to zero mean/unit variance.
- **CNN:** 128-band mel-spectrogram input (128×64), 3 convolutional blocks (16/32/64 filters) with max-pooling, a dense layer with dropout, and softmax output. Trained with Adam and sparse categorical cross-entropy.
- **Evaluation:** Accuracy, per-class precision/recall/F1, and confusion matrices on a held-out test set.

Full methodology, related work, and discussion are in the [paper](paper/).

## Repository Structure
