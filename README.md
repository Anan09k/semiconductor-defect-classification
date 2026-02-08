# Semiconductor Defect Classification

## Problem Statement
We built a multi-class classifier to detect and categorize semiconductor wafer defects using SEM inspection images. The goal is to automate visual inspection, improve consistency, enable edge deployment, and reduce manual quality control effort.

## Dataset
- 8 defect categories including `Bridge`, `Opens`, `Particle`, `LER`, `CMP`, etc.
- Total: 800 images (100 per class).
- Data split:
  - Train: 70% (560 images)
  - Validation: 15% (120 images)
  - Test: 15% (120 images)
  
- Images are organized in:
- dataset/
├── train/
│ └── class folders
├── val/
│ └── class folders
└── test/
└── class folders

## Model Architecture
- Custom classifier based on MobileNetV2 (width multiplier = 0.5) trained from scratch.
- Input: grayscale SEM image resized to 224×224.
- Lightweight design for edge inference.

## Training
- **Framework**: PyTorch
- **Augmentation**: rotation, flips, mild brightness/contrast
- **Training hardware**: Google Colab GPU environment.

## Model Export & Compression
- The trained model was exported to ONNX.
- FP16 quantization used to reduce size.
- Final model: **1.58 MB (FP16 ONNX)**.

## 📌 Results on Test Set
- **Accuracy:** 98.3%
- **Macro Precision:** 0.985
- **Macro Recall:** 0.983
- **F1-score:** 0.983
- **Confusion Matrix:** see `results/confusion_matrix.png`
