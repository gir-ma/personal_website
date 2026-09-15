---
title: "Airbnb Rating Prediction"
excerpt: "Built a machine learning model to predict Airbnb review scores, improving prediction accuracy through advanced feature engineering and hyperparameter tuning."
skills:
  - Python
  - Pandas
  - Scikit-learn
  - Random Forest
  - Linear Regression
---

<!-- ## Airbnb Rating Prediction -->

<!-- **Duration:** [Month Year] – [Month Year] -->

### Skills Used

| Python | Pandas | Scikit-learn |
|:---:|:---:|:---:|
| **Random Forest** | **Linear Regression** | **Jupyter Notebook** |

### The Challenge
Airbnb hosts and guests rely heavily on review scores to build trust, but predicting what drives a rating is difficult due to noisy, incomplete, and highly variable listing data. The goal was to build a model that could accurately estimate review scores from listing and host attributes, helping surface the key factors behind guest satisfaction.

### Approach
- Cleaned and prepared a large, messy Airbnb dataset using **imputation, feature scaling, and one-hot encoding** to handle missing values and categorical variables.
- Engineered and selected features to improve signal quality before modeling.
- Trained and compared multiple models, including **Linear Regression** and **Random Forest**, to evaluate performance trade-offs.
- Tuned hyperparameters (e.g., tree depth, number of estimators) to reduce error and improve generalization.
- Conducted exploratory data analysis and visualization in **Jupyter Notebook** to validate assumptions and interpret model behavior.

### Results
- Achieved a **Mean Absolute Error (MAE) of 0.298** using the tuned Random Forest model.
- Improved prediction accuracy by **3%** through hyperparameter tuning and preprocessing refinements.
- Random Forest outperformed baseline Linear Regression, confirming the value of non-linear modeling for this dataset.

### Key Achievements
-  **3% improvement** in prediction accuracy after tuning
-  **0.298 MAE** with the optimized Random Forest model
-  Robust preprocessing pipeline (imputation, scaling, encoding) that generalized well across the dataset