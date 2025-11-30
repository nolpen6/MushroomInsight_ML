# 🍄 MushroomInsight_ML  
### Predicting Toxic Mushrooms Using Machine Learning  
**Final ML Project — Group Work**  
**Authors:** Nolwenn Montillot · Hannah Zilesch · Emma Lou Villaret  

---

## 📌 Overview

This repository contains our complete end-to-end machine learning project **MushroomInsight_ML**, where we attempt to classify mushrooms as **edible** or **poisonous** based solely on their morphological traits.

We treat this project like a mini research study:  
- we define hypotheses,  
- explore the data,  
- test statistical associations,  
- train multiple ML models, and  
- analyze model behavior and errors.

The dataset is the well-known **UCI Mushroom dataset**, which is clean, fully categorical, and almost perfectly separable — making it ideal for learning and practicing tabular ML.

---

## 🌱 Goals of the Project

- Understand which visible traits are most predictive of mushroom toxicity  
- Build multiple ML models to classify edible vs poisonous mushrooms  
- Interpret feature importance and model behavior  
- Compare linear, non-linear, tree-based, and distance-based models  
- Highlight limitations of this toy dataset vs real-world mushroom identification  

---

## 🧪 Dataset

- **Source:** UCI Machine Learning Repository  
- **Samples:** 8,124 mushrooms  
- **Features:** 22 categorical attributes  
- **Target:** `poisonous`  
  - `e` → edible  
  - `p` → poisonous  

Examples of features:
- odor  
- cap shape / cap color  
- gill size / gill spacing  
- spore-print-color  
- stalk shape / stalk root  
- bruising  
- habitat  

---

## 🧭 Project Workflow

Our notebook & script follow a clear ML pipeline:

### **1. Exploratory Data Analysis**
- Target distribution  
- Feature vs toxicity visualizations  
- Domain-driven hypotheses:
  - **H1:** Odor is the strongest predictor  
  - **H2:** Spore-print-color is highly predictive  
  - **H3:** Habitat + bruises are secondary predictors  

### **2. Statistical Association**
- **Chi-Square** test  
- **Mutual Information** ranking  
- Confirm odor and spore-print-color dominate feature importance  

### **3. Preprocessing**
- Replace unknown values (`?`)  
- Treat missing `stalk-root` as `"missing"` category  
- One-hot encode all categorical features  
- Stratified train/test split (80/20)  
- Scale features for LR & KNN  

### **4. Models Trained**
We trained and evaluated the following models:
- Dummy Classifier (baseline)  
- Logistic Regression  
- Polynomial Logistic Regression (degree 2)  
- Decision Tree  
- Random Forest  
- K-Nearest Neighbors (KNN)  

### **5. Evaluation**
- Accuracy  
- ROC-AUC  
- Confusion matrices  
- Feature importance  
- Error analysis (focus on Random Forest)  

### **6. Model Comparison**
Nearly all models reach **near-perfect accuracy**, revealing the dataset’s almost perfect separability.

---

## 🏆 Key Findings

### 🎯 1. Odor is the strongest predictor  
Statistical tests + tree-based models instantly split on odor.  
Certain odors (foul, fishy, pungent) correspond almost exclusively to poisonous examples.

### 🎯 2. Spore-Print-Color is highly predictive  
This feature ranks second across both MI and chi-square.  
Matches real-world mycology techniques.

### 🎯 3. Most models perform perfectly  
Logistic Regression, Random Forest, and KNN all achieve near 100% accuracy.

Reason:  
**Once one-hot encoded, the dataset becomes almost linearly separable.**  
Most mushrooms form tight clusters representing edible or poisonous categories.

### 🎯 4. Misclassifications reveal ambiguous odor profiles  
The few errors come from mushrooms with:
- neutral or common odors  
- rare gill/stalk colors  
- unusual feature combinations  
that appear very few times in the training set.

---

## ⚠️ Limitations of the Dataset

This dataset is **excellent for teaching** but **not realistic** for actual mushroom foraging.

It lacks:
- noisy human measurements  
- geographically varying species  
- real look-alike mushroom species  
- environmental conditions  
- mislabeled samples  

👉 A model that reaches 100% accuracy here does **not** translate into safe real-world identification.

**Never eat a mushroom based on a classifier. Ever.**  
This project is *only* for educational purposes.
