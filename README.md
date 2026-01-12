# Wine Quality Classification
A machine learning classification project that predicts **wine quality (low vs high)** from physicochemical measurements, compares multiple models (Logistic Regression, Tree, Random Forest, Boosting, Neural Net, KNN, SVM), and evaluates performance using **Accuracy, F1 Score, and AUC**.

> Slides included: **Wine Quality Classification – Hwan Cho** 

---

## Features

### Dataset & Problem Setup
- Uses the **UCI Wine Quality** datasets (red + white)
- Combines both datasets and adds **`wine_type`** dummy variable (0 = white, 1 = red) :contentReference[oaicite:1]{index=1}  
- Converts original quality score into a **binary target**:
  - **Low quality:** 0–5  
  - **High quality:** 6–10 :contentReference[oaicite:2]{index=2}
- Train/test split: **70% train / 30% test**
- Metrics: **Accuracy, F1 Score, AUC** (accounts for baseline/no-information rate) :contentReference[oaicite:3]{index=3}

### Feature Engineering & Selection
- **Stepwise AIC** feature selection: removed **`chlorides`** (lower AIC) :contentReference[oaicite:4]{index=4}
- **Scaling applied only when needed** (e.g., KNN, SVM, Neural Networks, Logistic Regression) :contentReference[oaicite:5]{index=5}

### Models Implemented
- Logistic Regression (baseline)
- Classification Tree (cp tuned via CV)
- Random Forest (mtry tuned via CV)
- Gradient Boosting (gbm with tuned depth/trees/shrinkage)
- Neural Network (nnet with tuned size/decay)
- KNN (tuned k, odd grid search)
- SVM (radial kernel; tuned cost & gamma/sigma; compared vs linear) :contentReference[oaicite:6]{index=6}

### Evaluation & Visualization
- Confusion matrices for each model
- ROC curves per model + combined ROC comparison plot
- Summary table comparing **Accuracy / F1 / AUC** across all models

### Key Findings
- **Random Forest selected as the best overall model** based on:
  - Highest accuracy
  - Strong ROC/AUC performance
  - Practical computational performance :contentReference[oaicite:7]{index=7}
- Interpretable economic takeaway: **wine quality can be predicted from measurable inputs**, helping producers optimize controllable factors :contentReference[oaicite:8]{index=8}  
- Example “top variables” highlighted in the slides include **Alcohol, Volatile Acidity, Density** :contentReference[oaicite:9]{index=9}

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/wine-quality-classification.git
   cd wine-quality-classification

2. Create a project-specific library
   ```bash
   install.packages("renv")
   renv::init()
   renv::activate()

3. Install dependencies
   ```bash
   install.packages(c(
  "MASS",
  "pROC",
  "caret",
  "ROCR",
  "rpart",
  "rpart.plot",
  "randomForest",
  "gbm",
  "nnet",
  "class",
  "e1071"
))

## Usage

Execute main script
```bash
Rscript wine_quality_models.R


## Project Structure

wine-quality-classification/
├── wine_quality.Rmd      # Single script containing all models + evaluation
├── winequality-red.csv        # Dataset (red wine)
├── winequality-white.csv      # Dataset (white wine)
├── slides/
│   └── Wine_Quality_Classification- Hwan_Cho.pptx
├── README.md
└── LICENSE

