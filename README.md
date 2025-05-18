# Team_9_CNN_Component
## Anomalous Packet Detection in Public WiFi Networks

This repository contains the code and documentation for a two-stage deep learning system designed to detect and classify network anomalies in public WiFi environments. This work was completed as a final project for CPE 313 (Data Science) at the Technological Institute of the Philippines.

Complete Project's Repository located at: https://github.com/JemDeGuzman/team_9_cpe313_final_project

## 📁 Dataset

We used the **CIC-DDoS2019** dataset, a realistic and labeled dataset that includes:
- 80 extracted flow-based features
- 12 different DDoS attack types (e.g., DrDoS_NTP, UDP-lag, WebDDoS, etc.)
- A large number of benign samples

> ✅ Preprocessing included:
- Feature scaling
- Class balancing 
- Dropping non-informative identifiers (e.g., IP/Port info)

## 🧠 Project Architecture

This project implements a **two-stage anomaly detection and classification pipeline**:

### Stage 1: Autoencoder-Based Anomaly Detection
Autoencoder Repository: https://github.com/JemDeGuzman/Team_9_Autoencoder_Component
Three different autoencoder models were trained on benign traffic only to detect anomalies based on reconstruction error:
- **Simple Autoencoder**
- **Variational Autoencoder (VAE)**
- **Deep Recurrent Autoencoder (DRAE)**

Thresholds were selected using **ROC-AUC analysis**.

### Stage 2: Attack Type Classification (Image-Based)
Anomalous traffic was converted into RGB images (77x77x3) and passed to image classification models:
- **Convolutional Neural Network (CNN)**
- **ResNet50 (fine-tuned on ImageNet)**
- **EfficientNetV2B0 (two-phase training: head training + fine-tuning)**

## 📊 Model Performance

| Model                  | Task                   | Accuracy | F1-Score | 
|------------------------|------------------------|----------|----------|
| Simple Autoencoder     | Anomaly Detection      | 97.00%   | 0.97     | 
| Variational Autoencoder| Anomaly Detection      | 95.65%   | 0.9572   | 
| Deep Recurrent AE      | Anomaly Detection      | 96.00%   | 0.96     |
| CNN                    | Attack Classification  | 95.26%   | 0.9509   |
| ResNet50               | Attack Classification  | 91.97%   | 0.9203   | 
| EfficientNetV2B0       | Attack Classification  | 93.80%   | 0.9343   | 
