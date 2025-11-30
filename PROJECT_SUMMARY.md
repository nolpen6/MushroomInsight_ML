# MushroomInsight ML — Project Summary  
**By Nolwenn Montillot · Hannah Zilesch · Emma Lou Villaret**  
*Final Machine Learning Project*

---

## 1. Introduction

This project explores whether we can classify mushrooms as **edible** or **poisonous** using only their physical characteristics — things like odor, cap color, gill structure, habitat, and bruising.

We chose the UCI Mushroom dataset because it’s the classic “ML playground”: fully categorical, extremely clean, and surprisingly fun to analyze. Our goal wasn’t just to reach high accuracy, but to understand *why* the model works, which traits matter most, and how different algorithms behave when the data is this structured.

---

## 2. Initial Hypotheses

Before training any models, we defined three hypotheses based on intuition and basic mycology:

### **H1 — Odor is the strongest predictor of toxicity.**
Many strong or unpleasant odors typically signal poisonous species.

### **H2 — Spore-print-color is also highly predictive.**
This is a widely used identification trick in real-world mushroom foraging.

### **H3 — Habitat and bruising provide additional signal but are secondary.**
These features matter, but less dramatically.

---

## 3. Exploratory Analysis

We performed both visual and analytical exploratory analysis:

- Target distribution  
- Stacked barplots for key features  
- Chi-square tests  
- Mutual Information ranking  
- Cramér’s V heatmap to understand feature–feature relationships  

### Key Findings

- **Odor** is overwhelmingly predictive.  
- **Spore-print-color** ranks consistently high across statistical methods.  
- **Gill-size, gill-color, and stalk-root** form structured, species-like groups.  
- **Cap-color** provides almost no predictive signal.  
- **Habitat and bruises** show mild but meaningful associations.

The Cramér’s V heatmap demonstrated strong internal structure, showing that many traits tend to co-occur in consistent bundles. This is part of why the classification task becomes so easy.

---

## 4. Models Trained

We trained six models:

- Dummy Classifier (baseline)  
- Logistic Regression  
- Polynomial Logistic Regression (degree 2)  
- Decision Tree  
- Random Forest  
- K-Nearest Neighbors (KNN)  

Each model was evaluated using:

- Accuracy  
- Confusion matrices  
- Precision, Recall, F1-score  
- ROC-AUC (for probabilistic models)  
- **5-fold cross-validation** to assess robustness  

---

## 5. What We Found (Model Behavior Summary)

All meaningful models achieved **near-perfect accuracy**, often above 0.99.

### Why This Happens

#### **1. One-hot encoding makes classes almost linearly separable.**
Logistic Regression already performs almost perfectly.

#### **2. Odor and spore-print-color create huge natural splits.**
Decision Trees and Random Forests pick these up instantly.

#### **3. KNN works because edible and poisonous mushrooms form tight clusters.**
There is almost no overlap in feature space.

#### **4. Polynomial features don’t help.**
The dataset is already too clean for higher-order interactions.

#### **5. Random Forest handles the few edge cases.**
Averaging trees stabilizes decisions and improves consistency.

Cross-validation confirmed that these results are not due to lucky splits: performance was extremely stable across folds.

---

## 6. Misclassifications

We inspected the few samples misclassified by the Random Forest model. These mushrooms tended to have:

- neutral or ambiguous odors,  
- rare gill or stalk-color combinations,  
- or unusual trait combinations that did not appear often in training.

These are natural edge cases and reflect dataset limitations, not model weaknesses.

---

## 7. Limitations

Despite the extremely high accuracy, the dataset has strong limitations:

- No measurement noise  
- No ambiguous species  
- No mislabeled samples  
- No environmental or geographic variation  
- No visually confusing look-alikes  
- No realistic uncertainty  

**This dataset is a great teaching tool but not a realistic mushroom identification system.**

> **This model should never be used for real mushroom foraging.**

A practical system would require:
- images  
- environmental context  
- expert validation  
- uncertainty estimation  
- additional sensory information  

---

## 8. Final Thoughts

This project was a great way to learn how different ML models behave on structured categorical data. It helped us understand:

- how one-hot encoding influences decision boundaries,  
- how statistical association aligns with model behavior,  
- why different models converge when the dataset is highly separable,  
- and how cross-validation supports robustness claims.

It also reinforced an important ML truth:

> **A model is only as good as the data it learns from.**  
> This dataset is exceptionally clean — real mushrooms are not.

Overall, the project strengthened our intuition about machine learning and gave us a much better sense of how to interpret models beyond a single accuracy score.

And yes — we now tend to mentally classify mushrooms on hikes…  
but just to be clear: **in the forest, trust a mycologist, not a model.**
