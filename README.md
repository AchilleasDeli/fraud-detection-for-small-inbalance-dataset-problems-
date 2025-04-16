
#  Fraud Detection on Limited Data: A Classifier Reality Check

## Overview

This notebook explores the limits of traditional machine learning models in detecting fraud when working with a **small and highly imbalanced dataset**. It serves as a realistic case study on why even the most popular classifiers often struggle in fraud detection without sufficient data and meaningful features.

---

## Models Used

We tested the following models under two different resampling strategies (70:30 undersampling and SMOTE):

- Logistic Regression
- Random Forest
- Decision Tree
- Support Vector Machine (SVM)
- K-Nearest Neighbors
- Neural Network (via Keras + Grid Search)

Each model was trained and evaluated with the goal of understanding how well it can detect fraud in a skewed, small-scale scenario.

---

## Challenges Faced

This project makes it clear that:

- **Accuracy is misleading**: A model predicting only the majority class (non-fraud) can still achieve >90% accuracy.
- **Low fraud volume hurts performance**: Classifiers need enough examples to learn meaningful patterns.
- **Feature limitations**: Transaction-level features alone are often too weak to distinguish fraud from legit behavior.
- **Resampling isn't magic**: SMOTE and undersampling help, but don't fix the lack of signal in small datasets.

---

## Metrics Evaluated

We focused on:
- Precision
- Recall
- F1 Score
- ROC AUC

Across models, **recall on the fraud class remained poor**, often under 20%, even when accuracy and AUC looked decent. This reinforces why recall and F1 are more reliable for imbalanced problems like fraud detection.

---

## Neural Network

We also built a fully tunable Neural Network using Keras, applying grid search to optimize:
- Number of hidden layers
- Number of neurons
- Activation functions
- Optimizer
- Batch size and epochs

Despite tuning, the neural net still struggled to generalize, reaffirming that **more data, not just deeper models, is what's truly needed**.

---

## Key Takeaways

- Fraud detection on small datasets is **not a modeling problem**, it’s a **data problem**.
- You need strong **behavioral, time-based, or contextual features** to make models work.
- Sometimes anomaly detection (e.g. Isolation Forest, Autoencoders) is more effective than supervised models in this setting.

---

## Recommendations for Future Work

- Collect more fraud samples (even synthetic session-based data)
- Engineer user-level and temporal features
- Try unsupervised anomaly detection
- Explore ensemble methods like EasyEnsemble or CatBoost with scale_pos_weight

---

## Stack

- Python 3, scikit-learn, imbalanced-learn, Keras
- SMOTE, GridSearchCV
- Matplotlib / Seaborn for visuals

---

## Final Thought

If you're working on fraud detection and your dataset is small and imbalanced — this repo is your **reality check**. Don't trust accuracy. Focus on recall. And always dig deeper into the data.

