# 🫁 Tuberculosis (TB) Detection System from Chest X-Rays

An end-to-end deep learning system and web application designed to detect Tuberculosis (TB) from chest X-ray radiographs using Transfer Learning (VGG16) and Flask.

---

## 📌 Project Overview

Tuberculosis remains one of the world's leading infectious causes of death. Early diagnosis via chest radiography is crucial for effective treatment. This project provides:
- A fine-tuned on Neural Network  based on **VGG16**.
- An interactive, responsive **Flask web application** allowing clinicians or users to upload X-ray images and receive instant probability breakdowns and diagnostic verdicts.
- Evaluation scripts computing Accuracy, Precision, Recall, F1-Score, Confusion Matrix, and ROC Curve.

---

## 👥 Team Members

| Name | Registration Number |
| :--- | :---: |
| **Ishan Choudhary** | 25BCE10753 |
| **Khush Gupta** | 25BCE10038 |
| **Vidit Choudhary** | 25BCE10749 |
| **Saransh Mathur** | 25BCE10354 |
| **Somya Bhardwaj** | 25BCE10409 |

---

## 📊 Datasets Used

This model was trained and evaluated using chest radiograph images curated from the following Kaggle datasets:

1. **[Chest X-Ray Dataset (4 Categories)](https://www.kaggle.com/datasets/pritpal2873/chest-x-ray-dataset-4-categories)**  

2. **[Tuberculosis (TB) Chest X-ray Dataset](https://www.kaggle.com/datasets/tawsifurrahman/tuberculosis-tb-chest-xray-dataset)**

---
## 📁 Project Structure

```text
Tb/
├── dataset/                    # Dataset directory
│   ├── Normal/                 # Normal chest X-ray images
│   └── TB/                     # Tuberculosis-positive X-ray images
├── index.html                  # Frontend user interface
├── app.py                      # Flask web application & prediction API
├── train_model.py              # Model training script (VGG16 + Data Augmentation)
├── evaluate.py                 # Evaluation metrics & ROC curve generator
├── tb_model.keras              # Trained model file
├── roc_curve_standard.png      # Generated ROC evaluation curve
├── requirements.txt            # Python dependencies
└── README.md                   # Project documentation

```

---

## 🚀 Usage

### 1. Run the Web Application
Start the Flask development server:
```bash
python app.py
```
Open your web browser and navigate to:
```
http://127.0.0.1:5000
```
- Click to upload any chest X-ray image (`.png`).
- Click **Predict** to view the confidence scores (`Normal %` vs `Tuberculosis %`) and diagnosis.

### 2. Train the Model (First Time)
To retrain the model from scratch on the dataset:
```bash
python train_model.py
```
This saves the trained weights to `tb_model.keras`.

### 3. Evaluate the Model
To compute classification metrics and generate the ROC curve on the unseen test split:
```bash
python evaluate.py
```
#### 📊 Classification Report

| Class | Precision | Recall | F1-Score |
| :--- | :---: | :---: | :---: |
| **Normal** | 0.85 | 0.90 | 0.88 |
| **Tuberculosis (TB)** | 0.90 | 0.84 | 0.87 |

**Overall Accuracy:** **87.38%**

#### 🧩 Confusion Matrix

| Actual \ Predicted | Predicted Normal | Predicted TB |
| :--- | :---: | :---: |
| **Actual Normal** | **190** (True Negative) | **20** (False Positive) |
| **Actual TB** | **33** (False Negative) | **177** (True Positive) |

- ROC Curve saved and visualized: `roc_curve_standard.png`

---

## ⚠️ Disclaimer

*This application is built for academic and research purposes only. It should not be used as a standalone diagnostic tool without verification from qualified healthcare professionals.*