# Open-Source Keratoconus Detection (Vision AI)
Author: Nick Pandolfi

## Project Overview 
Keratoconus is a progressive eye disease characterized by the thinning and bulging of the cornea into a cone-like shape. While advanced cases are easily diagnosed, early-stage "Suspect" or "Forme Fruste" cases are frequently missed, leading to irreversible vision loss.

The Mission: To develop an open-source screening tool to provide eye doctors worldwide with a high-accuracy, accessible diagnostic layer using Computer Vision in an effort to detect early signs of Keratoconus at scale.

## Strategic Objectives
* Early Detection: Building a multi-class model to distinguish between Normal, Suspect, and Confirmed Keratoconus cases.
* Clinical Explainability: Integrating Grad-CAM heatmaps so clinicians can visualize the specific corneal regions flagged by the AI.
* Probabilistic Reliability: Utilizing Bayesian Neural Networks to provide an "Uncertainty Score," ensuring the model only provides high-confidence diagnostic support.
* Global Accessibility: Deploying the final model via a Streamlit web interface under an MIT License for widespread clinical use.

## Technical Architecture
The model utilizes a Hybrid Deep Learning Construct inspired by state-of-the-art research in translational vision science.
* Base Model: EfficientNet-B0 (Transfer Learning) for its optimal balance of high accuracy and low computational footprint in a clinic setting.
* Input Data: 7 specific corneal maps per case (Anterior/Posterior Elevation, Sagittal Curvature, and Thickness) standardized to 224x224 pixels
* Loss Function: Weighted Cross-Entropy to address natural class imbalance (significantly more "Normal" data than "Keratoconus" data).
* Framework: Developed in PyTorch with training optimized for both NVIDIA GPUs (CUDA) and Apple Silicon (MPS).

      https://www.kaggle.com/datasets/elmehdi12/keratoconus-detection


## Current Benchmarks
Our initial baseline model (Simple CNN) achieved an 80% overall accuracy on a 3-class system. Current development focuses on improving "Suspect" recall ) through advanced feature fusion and hyperparameter tuning.

| Class | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **Normal** | 0.76 | 0.89 | 0.82 |
| **Suspect** | 0.60 | 0.45 | 0.51 |
| **KCN (Keratconus)** | 0.92 | 0.92 | 0.92 |

## Roadmap
[x] Phase 1: Data Acquisition and Pre-processing standardization.

[x] Phase 2: Baseline Model Architecture (Simple CNN).

[ ] Phase 3: Transition to EfficientNet-B0 Transfer Learning.

[ ] Phase 4: Implementation of Grad-CAM for Explainability.

[ ] Phase 5: Deployment of Streamlit Web Interface.

## Core Libraries
* Python 3.10+: Core programming language for data science and model development.
* PyTorch: Primary deep learning framework for building the SimpleKCNNet and EfficientNet-B0 architectures.
* Torchvision: For accessing pre-trained weights and implementing standardized clinical image transforms.
* Scikit-learn: Used for calculating precision, recall, and generating the Confusion Matrix to evaluate diagnostic performance.
* Pillow (PIL): For loading and pre-processing multi-map corneal imagery into standardized $224 \times 224$ tensors.
* Matplotlib & Seaborn: For visualizing training loss curves and creating professional-grade heatmaps of model predictions.
* Streamlit: The frontend framework for deploying the open-source screening interface for global clinical use.

## Works Referenced
This project is built upon the methodology and clinical standards established in the following foundational studies:
* Primary Methodology: Al-Timemy AH, Mosa ZM, et al. "A Hybrid Deep Learning Construct for Detecting Keratoconus From Corneal Maps." Translational Vision Science & Technology, 2021.
* Architecture Inspiration: Tan M, Le QV. "EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks." ICML, 2019.
* Clinical Benchmarking: Lavric A, et al. "Detecting keratoconus from corneal imaging data using machine learning." IEEE Access, 2020.
* Diagnostic Standards: Belin MW, Ambrósio R Jr. "Enhanced tomographic assessment to detect corneal ectasia based on artificial intelligence." American Journal of Ophthalmology, 2018.

# Clinical Disclaimer
### This project is a Clinical Decision Support Tool designed for screening assistance and research purposes only. It is not a replacement for a professional clinical examination by a licensed ophthalmologist.
