# Wine Quality Classification
A machine learning classification project that predicts **wine quality (low vs high)** from physicochemical measurements, compares multiple models (Logistic Regression, Tree, Random Forest, Boosting, Neural Net, KNN, SVM), and evaluates performance using **Accuracy, F1 Score, and AUC**.

> Slides included: **Wine Quality Classification – Hwan Cho** 

---

## Features

### Dataset & Problem Setup
- Uses the **UCI Wine Quality** datasets (red + white)
- Combines both datasets and adds **`wine_type`** dummy variable (0 = white, 1 = red)
- Converts original quality score into a **binary target**:
  - **Low quality:** 0–5  
  - **High quality:** 6–10 
- Train/test split: **70% train / 30% test**
- Metrics: **Accuracy, F1 Score, AUC** (accounts for baseline/no-information rate) 

### Feature Engineering & Selection
- **Stepwise AIC** feature selection: removed **`chlorides`** (lower AIC) 
- **Scaling applied only when needed** (e.g., KNN, SVM, Neural Networks, Logistic Regression) 

### Models Implemented
- Logistic Regression (baseline)
- Classification Tree (cp tuned via CV)
- Random Forest (mtry tuned via CV)
- Gradient Boosting (gbm with tuned depth/trees/shrinkage)
- Neural Network (nnet with tuned size/decay)
- KNN (tuned k, odd grid search)
- SVM (radial kernel; tuned cost & gamma/sigma; compared vs linear)

### Evaluation & Visualization
- Confusion matrices for each model
- ROC curves per model + combined ROC comparison plot
- Summary table comparing **Accuracy / F1 / AUC** across all models

### Key Findings
- **Random Forest selected as the best overall model** based on:
  - Highest accuracy
  - Strong ROC/AUC performance
  - Practical computational performance 
- Interpretable economic takeaway: **wine quality can be predicted from measurable inputs**, helping producers optimize controllable factors 
- Example “top variables” highlighted in the slides include **Alcohol, Volatile Acidity, Density** 

---

## Installation

  1. Clone the repository:
     ```bash
     git clone https://github.com/yourusername/wine-quality-classification.git
     cd wine-quality-classification
     ```
  
  2. Create a project-specific library
     ```bash
     install.packages("renv")
     renv::init()
     renv::activate()
     ```
    
  3. Install dependencies
     ```bash
     install.packages(c("MASS", "pROC", "caret", "ROCR", "rpart", "rpart.plot", "randomForest", "gbm", "nnet", "class", "e1071"))
     ```

## Usage

Execute the main script:
  ```bash
  Rscript Wine_Quality.Rmd
  ```

## Project Structure
  ```bash
  wine-quality-classification/
  ├── wine_quality.Rmd
  ├── winequality-red.csv
  ├── winequality-white.csv
  ├── slides/
  │   └── Wine_Quality_Classification- Hwan_Cho.pptx
  ├── README.md
  └── LICENSE
  ```
## Development

### Reproducibility
- Set a seed before splitting (e.g., set.seed(123))
- Fit scaling only on the training set, then apply to test

### (Optional) Future Refactor
If you want to modularize later:
- src/preprocessing.R
- src/models/*.R
- src/evaluation.R

## Contributions

To contribute:
1. Fork the repository
2. Create a feature branch (git checkout -b feature/YourFeature)
3. Commit your changes (git commit -m "Add YourFeature")
4. Push to the branch (git push origin feature/YourFeature)
5. Open a Pull Request

## License
This project is licensed under the **MIT License**.  

## Acknowledgments

- UCI Machine Learning Repository for the Wine Quality datasets
- caret package for model training, cross-validation, and evaluation workflows
- randomForest, gbm, e1071, nnet for machine learning implementations
- ROCR and pROC for ROC curve and AUC analysis









