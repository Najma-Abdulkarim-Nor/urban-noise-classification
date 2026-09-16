# Urban Noise Monitoring and Classification

Comparative evaluation of **Random Forest**, **SVM**, and a **CNN** for automated urban sound classification, built on the UrbanSound8K dataset. This work was published at the **2026 IEEE International Conference on Smart Mobility (SM2026)** and is now indexed in IEEE Xplore.

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

```
urban-noise-classification/
├── notebooks/
│   └── Urban_Noise_Monitoring_and_Classification.ipynb   # Full pipeline: preprocessing → features → RF/SVM/CNN → Gradio demo
├── paper/
│   └── Urban_Noise_Monitoring_and_Classification_IEEE_SM2026.pdf
├── presentation/
│   └── urban_noise_presentation.pptx
├── test_audio/
│   ├── Construction_1.wav
│   ├── Construction_2.wav
│   ├── emergency2.wav
│   ├── traffic_1.wav
│   └── traffic_2.wav
├── requirements.txt
├── LICENSE
└── README.md
```

## Getting Started

### 1. Clone and install dependencies
```bash
git clone https://github.com/Najma-Abdulkarim-Nor/urban-noise-classification.git
cd urban-noise-classification
pip install -r requirements.txt
```

### 2. Get the dataset
Download [UrbanSound8K](https://urbansounddataset.weebly.com/urbansound8k.html) and place it locally (the notebook currently expects a Google Drive path — see **Notes** below to adapt it for local/Colab use).

### 3. Run the notebook
Open `notebooks/Urban_Noise_Monitoring_and_Classification.ipynb` in Jupyter or Google Colab and run all cells. It will:
1. Load and balance the dataset (3 classes, 70 clips each)
2. Extract MFCC/Chroma/Spectral features (RF, SVM) and mel-spectrograms (CNN)
3. Train and evaluate all three models with confusion matrices
4. Launch a **Gradio** demo where you can upload any `.wav` file (try the samples in `test_audio/`) and classify it live with your model of choice

## Notes / Known Limitations

- The notebook was developed in Google Colab and currently mounts Google Drive for the dataset path (`base_path`) — update this to a local path if running outside Colab.
- Results are based on a balanced 3-class, 210-clip subset for lightweight edge-deployment simulation; they may not generalize to the full 10-class UrbanSound8K dataset.
- High CNN accuracy may partly reflect limited data size and lack of augmentation (noted as a limitation in the paper).

## Citation

If you use this work, please cite:

> N. Nour, M. Alblooshi, and K. Elgazzar, "Urban Noise Monitoring and Classification Using Machine Learning and Deep Learning," *2026 IEEE International Conference on Smart Mobility (SM)*, IEEE Xplore, 2026.

## Authors

- **Najma Nour** — Canadian University Dubai, UAE
- **Maryam Alblooshi** — Canadian University Dubai, UAE
- **Khalid Elgazzar** — IoT Research Laboratory, Ontario Tech University, Canada

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
