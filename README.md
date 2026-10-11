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

## 📊 Dataset & Splitting

The balanced dataset contains a total of **2,800 chest radiographs** (1,400 Normal and 1,400 TB-positive).

The dataset is partitioned into:
- **Training Set (70%):** 1,960 images
- **Validation Set (15%):** 420 images
- **Held-out Test Set (15%):** 420 images

The project utilizes curated chest radiographs sourced from two benchmark datasets:
1. **[Chest X-Ray Dataset (4 Categories)](https://www.kaggle.com/datasets/pritpal2873/chest-x-ray-dataset-4-categories)**
2. **[Tuberculosis (TB) Chest X-ray Dataset](https://www.kaggle.com/datasets/tawsifurrahman/tuberculosis-tb-chest-xray-dataset)**

---

## 🛠️ Tech Stack

- **Programming Language**: Python 3.10+
- **Deep Learning Framework**: TensorFlow / Keras (VGG16 Transfer Learning)
- **Backend Web Framework**: Flask
- **Frontend**: HTML5, CSS3, JavaScript (interactive image preview & real-time progress bars)
- **Image Processing**: Pillow (PIL), NumPy

---

## 🚀 How to Run the Project
1. Install Dependencies
```bash
pip install -r requirements.txt
```
2. Train the Model (Optional - pretrained `tb_model.keras` already included)
```bash
python train_model.py
```
3. Check Model Accuracy & Evaluation
```bash
python calculate_accuracy.py
```
4. Launch the Web Application
```bash
python app.py
```
Open your browser and navigate to:
```text
http://127.0.0.1:5000

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