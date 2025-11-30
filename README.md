# 🍄 MushroomInsight_ML  
### Predicting Mushroom Toxicity Using Machine Learning  
**Authors:** Nolwenn Montillot · Hannah Zilesch · Emma Lou Villaret  

---

## 📌 Overview

This repository contains our end-to-end machine learning project **MushroomInsight_ML**, where we classify mushrooms as **edible** or **poisonous** using only their morphological traits.

We approached this project like a small research study:

- we defined hypotheses  
- explored the structure of the data  
- tested statistical associations  
- trained multiple ML models  
- analyzed model behavior  
- evaluated robustness with cross-validation  
- and reflected on real-world limitations  

The dataset is the classic UCI Mushroom dataset:  
clean, categorical, structured, and almost perfectly separable — making it ideal for practicing tabular ML.

---

## 🌱 Goals of the Project

- Identify which traits truly predict mushroom toxicity  
- Explain why some models succeed (or fail) on highly structured categorical data  
- Compare linear, non-linear, tree-based, and distance-based models  
- Evaluate feature importance and model behavior  
- Discuss the dataset’s limitations and lack of real-world realism  

---

## 🧪 Dataset

- **Source:** UCI Machine Learning Repository  
- **Samples:** 8,124 mushrooms  
- **Features:** 22 categorical morphological traits  
- **Target:**  
  - `e` → edible  
  - `p` → poisonous  

Examples of traits:

- Odor  
- Cap shape & cap color  
- Gill size, spacing, color  
- Spore-print-color  
- Stalk root, stalk coloring  
- Bruising  
- Habitat & population  

`stalk-root` contains `?` for missing values — treated as its own category.

---

## 🧭 Project Workflow

### **1. Exploratory Data Analysis**
- Target distribution  
- Stacked barplots  
- Initial hypotheses  
  - **H1:** Odor is the strongest predictor  
  - **H2:** Spore-print-color is also highly predictive  
  - **H3:** Habitat & bruising are weaker secondary features  

### **2. Statistical Association**
- Chi-Square tests  
- Mutual Information (MI) ranking  
- **Cramér’s V heatmap** to examine feature co-dependence  

### **3. Preprocessing**
- Replace `'?'` in `stalk-root`  
- One-hot encode all categorical variables  
- Stratified train/test split  
- Scale features for models that require it (LR, Polynomial LR, KNN)  

### **4. Models Trained**
- Dummy Classifier  
- Logistic Regression  
- Polynomial Logistic Regression  
- Decision Tree  
- Random Forest  
- K-Nearest Neighbors (KNN)  

### **5. Evaluation**
- Accuracy  
- Precision • Recall • F1-score  
- Confusion matrices  
- ROC-AUC  
- **5-fold cross-validation** for robustness  
- Misclassification analysis  

---

## 🧠 Key Findings

### **1. Odor is by far the strongest predictor**  
Tree models instantly split on odor.  
Certain odors (foul, fishy, pungent) align almost perfectly with poisonous mushrooms.

### **2. Spore-print-color is also highly informative**  
Consistently ranks second across MI and Chi-Square.  
Matches what real mycologists use.

### **3. All real models perform nearly perfectly**  
Logistic Regression, Random Forest, and KNN all reach > 0.99 accuracy.

Why?

- One-hot encoding makes the dataset almost linearly separable  
- Mushrooms form tight trait-based clusters  
- Strong, clean features produce extremely simple boundaries  

### **4. Misclassifications reveal ambiguous cases**  
Errors come mainly from mushrooms with:
- neutral odors  
- rare color combinations  
- unusual feature mixes  

---

## ⚠️ Limitations (Important)

This dataset is **not** realistic for real-world mushroom identification. It lacks:

- measurement noise  
- ambiguous look-alikes  
- mislabeled samples  
- environmental context  
- geographic variation  
- visual data  

> **Never use a classifier to decide whether a mushroom is safe to eat.  
This project is strictly educational.**

---

## 📂 Repository Structure

MushroomInsight_ML/
│
├── data/
│ └── agaricus-lepiota.data # UCI dataset (raw)
│
├── notebooks/
│ └── 01_mushroom_classification.ipynb # Full notebook: EDA + models + analysis
│
├── PROJECT_SUMMARY.md # Human-friendly narrative summary
├── README.md # This file
└── .gitignore

