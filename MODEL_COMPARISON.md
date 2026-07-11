# Model Comparison Report

## Project
**Retail Demand Forecasting using Walmart Store Sales Dataset**

---

# Objective

The objective of this project is to accurately forecast weekly sales for Walmart stores using machine learning models. Multiple regression models were developed and evaluated using a time-based validation strategy to identify the most suitable model for retail demand forecasting.

---

# Models Evaluated

The following models were implemented:

- Linear Regression
- Random Forest Regressor
- XGBoost Regressor
- Tuned Random Forest (Optuna)

---

# Model Performance Comparison

| Model | MAE | RMSE | R² Score |
|------|------:|------:|------:|
| Linear Regression | 1561.52 | 3257.15 | 0.9782 |
| Random Forest | 1466.72 | 3049.20 | 0.9809 |
| XGBoost | 1565.60 | 3232.39 | 0.9785 |
| **Random Forest (Optuna Tuned)** | **1408.16** | **2890.97** | **0.9828** |

---

# Model Selection

The tuned Random Forest model achieved the best overall performance across all evaluation metrics.

Reasons for selecting the final model:

- Lowest Mean Absolute Error (MAE)
- Lowest Root Mean Squared Error (RMSE)
- Highest R² Score
- Better ability to model nonlinear relationships
- Robust performance across different stores and departments
- Effective handling of mixed numerical and categorical features

---

# Model Evaluation Strategy

A chronological validation strategy was adopted to prevent data leakage.

- Training Data: Historical observations
- Validation Data: Last 26 weeks
- Evaluation Metrics:
  - MAE
  - RMSE
  - R² Score

This approach simulates a real-world forecasting scenario where future sales are predicted using only historical information.

---

# Hyperparameter Optimization

Hyperparameter tuning was performed using Optuna for the Random Forest model.

Best Parameters:

- n_estimators = 300
- max_depth = 20
- min_samples_split = 5
- min_samples_leaf = 2
- max_features = log2

The optimized model further reduced forecasting errors compared to the baseline Random Forest model.

---

# Model Explainability

To improve model transparency:

- Random Forest Feature Importance was analyzed.
- Business interpretation was provided for the most influential features.

Key features influencing predictions include:

- Lag_1
- Rolling_Mean_4
- Department
- Store
- Promotional MarkDown features
- Store Size

---

# Conclusion

Among all evaluated models, the tuned Random Forest demonstrated the best balance between predictive performance, robustness, and business applicability. Therefore, it was selected as the final model for Walmart weekly sales forecasting.