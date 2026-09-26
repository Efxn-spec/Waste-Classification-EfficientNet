# Automated Waste Classification using CNN & Transfer Learning (EfficientNetB0)

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)
[![Accuracy](https://img.shields.io/badge/Test%20Accuracy-97.28%25-brightgreen.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()

> Computer Vision project comparing a custom lightweight Convolutional Neural Network (CNN) against Transfer Learning with EfficientNetB0 for automated waste segregation into hazardous and recyclable categories.

---

## 📌 Project Overview

Efficient municipal and industrial waste segregation is essential for preventing environmental contamination, especially regarding hazardous items like batteries and recyclable materials like cardboard and glass. Manual sorting is labor-intensive, hazardous, and prone to human error.

This project implements an end-to-end Computer Vision pipeline to classify waste items into three distinct categories:
- **Battery** (Hazardous waste requiring specialized chemical handling)
- **Brown Glass** (Recyclable glass material)
- **Cardboard** (Recyclable paper/fibre material)

---

## 🔬 Methodology & Architecture

### 1. Dataset & Preprocessing
- **Total Images**: 2,443 grayscale images across 3 classes.
- **Data Split**: 70% Train (1,710 images), 15% Validation (366 images), 15% Test (367 images).
- **Preprocessing Pipeline**:
  - Resized to standard resolution: `224 × 224`.
  - Normalized pixel intensities: `[0, 1]`.
  - Data Augmentation: Random horizontal flips, rotations, zooming, and brightness adjustments.
  - Grayscale input channel to reduce computational footprint and prioritize structural/edge features over lighting variations.

### 2. Evaluated Architectures

| Model Architecture | Description | Parameters |
|---|---|---|
| **Custom CNN Baseline** | 3 Convolutional blocks (32, 64, 64 filters, 3×3 kernels), MaxPooling downsampling, Dropout (0.3), Dense classification head (64 neurons + Softmax). | Lightweight (~350k) |
| **EfficientNetB0 (Transfer Learning)** | Pre-trained ImageNet backbone with frozen weights, Global Average Pooling (GAP), Dropout regularization (0.3), Dense output layer (3 classes + Softmax). | Pre-trained Backbone + Adaptable Head |

---

## 📊 Results & Performance Evaluation

The models were evaluated on the independent held-out test set of 367 images:

### Summary Comparison

| Model | Test Accuracy | Macro Precision | Macro Recall | Macro F1-Score |
|---|---|---|---|---|
| **Custom CNN** | 84.20% | 0.8423 | 0.8213 | 0.8286 |
| **EfficientNetB0 (Transfer Learning)** | **97.28%** | **0.9733** | **0.9764** | **0.9747** |

### Per-Class Performance (EfficientNetB0)

| Class | Precision | Recall | F1-Score | Support |
|---|---|---|---|---|
| **Battery** | 0.9857 | 0.9583 | 0.9718 | 144 |
| **Brown Glass** | 0.9770 | 1.0000 | 0.9884 | 85 |
| **Cardboard** | 0.9571 | 0.9710 | 0.9640 | 138 |

**Key Takeaways**:
- EfficientNetB0 compound scaling achieved superior feature representation, reducing inter-class confusion between visually ambiguous categories (battery vs brown glass).
- Global Average Pooling significantly lowered overfitting risk compared to flattening dense feature maps.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+
- Jupyter Notebook or JupyterLab

### Installation

```bash
# Clone the repository
git clone https://github.com/Efxn-spec/Waste-Classification-EfficientNet.git
cd Waste-Classification-EfficientNet

# Install required dependencies
pip install -r requirements.txt
```

### Running the Notebook

```bash
jupyter notebook garbage_classification_project.ipynb
```

---

## 📂 Repository Structure

```text
├── docs/
│   ├── project_report.pdf         # Comprehensive academic project report
│   └── presentation_slides.pptx   # Project presentation slide deck
├── garbage_classification/        # Dataset organized by class
│   ├── battery/
│   ├── brownglass/
│   └── cardboard/
├── garbage_classification_project.ipynb  # Full training, evaluation & visualization code
├── requirements.txt               # Python package dependencies
├── .gitignore
└── README.md
```

---

## 👤 Author

- **Ahmad Irfan Johan Bin Mazlan**
- Faculty of Artificial Intelligence, Universiti Teknologi Malaysia (UTM)
- Course: SAIA 2133 Computer Vision
- 💼 LinkedIn: [ahmad-irfan-johan-bin-mazlan](https://www.linkedin.com/in/ahmad-irfan-johan-bin-mazlan-5b583a377)
- 📧 Email: [irfanjohan990@gmail.com](mailto:irfanjohan990@gmail.com)
