# 🫁 Tuberculosis (TB) Detection System from Chest X-Rays

An end-to-end deep learning system and web application designed to detect Tuberculosis (TB) from chest X-ray radiographs using Transfer Learning (VGG16) and Flask.

---

## 📌 Project Overview

Tuberculosis remains one of the world's leading infectious causes of death. Early diagnosis via chest radiography is crucial for effective treatment. This project provides:
- A fine-tuned Deep Convolutional Neural Network (CNN) based on **VGG16**.
- A balanced training pipeline with data augmentation and regularization.
- An interactive, responsive **Flask web application** allowing clinicians or users to upload X-ray images and receive instant probability breakdowns and diagnostic verdicts.
- Evaluation scripts computing Accuracy, Precision, Recall, F1-Score, Confusion Matrix, and ROC Curve.

---

## 📊 Datasets Used

This model was trained and evaluated using chest radiograph images curated from the following Kaggle datasets:

1. **[Chest X-Ray Dataset (4 Categories)](https://www.kaggle.com/datasets/pritpal2873/chest-x-ray-dataset-4-categories)**  
   *Curated by Pritpal Singh on Kaggle* — Contains categorized chest X-ray images used for normal and respiratory condition benchmarks.

2. **[Tuberculosis (TB) Chest X-ray Dataset](https://www.kaggle.com/datasets/tawsifurrahman/tuberculosis-tb-chest-xray-dataset)**  
   *Curated by Tawsifur Rahman et al. on Kaggle* — A dedicated collection of verified Tuberculosis-positive and Normal chest X-ray images.

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

## 🧠 Model Architecture & Methodology

- **Base Model**: Pretrained **VGG16** (ImageNet weights, frozen feature extractor)
- **Top Layers**:
  - `GlobalAveragePooling2D`
  - `Dense(32, activation='relu', L2 Regularization=0.02)`
  - `Dropout(0.40)`
  - `Dense(1, activation='sigmoid')`
- **Data Augmentation**: Rotation (15°), horizontal flips, width/height shifts, zoom.
- **Optimization & Loss**:
  - Optimizer: Adam (Learning Rate = `1.5e-4`)
  - Loss Function: Binary Crossentropy with label smoothing (`0.04`) for calibrated probabilities.
- **Data Split**: Stratified 70% Training / 15% Validation / 15% Unseen Test.

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/somyabhardwaj574-max/pe2026-tb-detection-system.git
cd pe2026-tb-detection-system
```

### 2. Create and Activate a Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
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
- Click to upload any chest X-ray image (`.png`, `.jpg`, `.jpeg`).
- Click **Predict** to view the confidence scores (`Normal %` vs `Tuberculosis %`) and diagnosis.

### 2. Train the Model (Optional)
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
Outputs include:
- Test Accuracy, Precision, Recall, and F1-Score
- Confusion Matrix
- ROC Curve saved to `roc_curve_standard.png`

---

## 🌐 Deployment

The web app is configured for local execution as well as cloud deployment platforms like [Render](https://render.com/):
- Dynamically binds to the assigned `$PORT` environment variable.
- Production WSGI deployment supported with `gunicorn`:
  ```bash
  gunicorn app:app
  ```

---

## ⚠️ Disclaimer

*This application is built for academic and research purposes only. It should not be used as a standalone diagnostic tool without verification from qualified healthcare professionals.*
