# 🛒 Walmart Retail Demand Forecasting

An end-to-end Machine Learning project that forecasts Walmart's weekly sales using historical sales records, store information, promotional markdowns, and economic indicators. The project follows a complete ML workflow including data preprocessing, exploratory data analysis, feature engineering, model development, hyperparameter tuning, model evaluation, and model selection.

---

# 📌 Project Objective

The objective of this project is to accurately predict weekly sales for Walmart stores and departments to support inventory planning, demand forecasting, and business decision-making.

---

# 📂 Project Structure

```
Walmart Retail Demand Forecasting/
│
├── data/
│   ├── raw/                  # Original Walmart datasets
│   ├── merged_data/          # Merged datasets
│   └── modeling/             # Train & validation datasets
│
├── retail-env/              # Virtual environment
│
├── MODEL_COMPARISON.md      # Model comparison report
├── README.md
├── random_forest_model.joblib
│
├── Retail_Demand_Forecasting (EDA).ipynb
├── Retail_Demand_Forecasting (ML Modelling).ipynb
│
└── Retail_Demand_Forecasting_Process_Flow_Document.pdf
```

---

# 📊 Dataset

The project uses the Walmart Store Sales Forecasting dataset.

Files used:

- train.csv
- test.csv
- features.csv
- stores.csv

After loading the datasets, they are merged using:

- Store
- Date
- IsHoliday

---

# ⚙️ Project Workflow

### 1. Data Loading

- Loaded all Walmart datasets
- Merged datasets using common keys
- Validated data structure

---

### 2. Data Cleaning

- Converted Date to datetime format
- Handled missing values
- Filled missing promotional markdown values with 0
- Converted holiday flag to binary format
- Checked duplicates
- Assessed numerical and categorical features

---

### 3. Exploratory Data Analysis

Performed business-oriented analysis including:

- Weekly sales trends
- Store-wise sales analysis
- Department-wise sales
- Holiday impact
- Seasonal trends
- Correlation analysis
- Distribution of Weekly Sales

---

### 4. Feature Engineering

Created features including:

- Year
- Month
- WeekOfYear
- Quarter
- Lag_1
- Rolling_Mean_4
- Total_MarkDown

These features capture temporal patterns and historical demand behavior to improve forecasting performance.

---

### 5. Model Development

Implemented multiple machine learning models:

- Linear Regression
- Random Forest Regressor
- XGBoost Regressor

Random Forest was further optimized using **Optuna Hyperparameter Optimization**.

---

### 6. Model Evaluation

Models were evaluated using a chronological validation strategy (last 26 weeks reserved for validation).

Evaluation Metrics:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

---

# 📈 Model Performance

| Model | MAE | RMSE | R² Score |
|------|------:|------:|------:|
| Linear Regression | 1561.52 | 3257.15 | 0.9782 |
| Random Forest | 1466.72 | 3049.20 | 0.9809 |
| XGBoost | 1565.60 | 3232.39 | 0.9785 |
| **Random Forest (Tuned)** | **1408.16** | **2890.97** | **0.9828** |

The tuned Random Forest model achieved the best forecasting performance and was selected as the final model.

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Optuna
- Joblib

---

# 🚀 Installation

Clone the repository

```bash
git clone <repository-url>
```

Create a virtual environment

```bash
python -m venv retail-env
```

Activate the environment

### Windows

```bash
retail-env\Scripts\activate
```

### Install dependencies

```bash
pip install -r requirements.txt
```

---

# ▶️ Running the Project

1. Download the Walmart dataset.
2. Place the CSV files inside the `data/raw` folder.
3. Open the notebooks.
4. Execute the notebooks in the following order:

- `Retail_Demand_Forecasting (EDA).ipynb`
- `Retail_Demand_Forecasting (ML Modelling).ipynb`

---

# 📁 Project Files

| File | Description |
|------|-------------|
| Retail_Demand_Forecasting (EDA).ipynb | Data preprocessing and exploratory analysis |
| Retail_Demand_Forecasting (ML Modelling).ipynb | Feature engineering, model training, evaluation, and tuning |
| MODEL_COMPARISON.md | Comparison of all developed models |
| Retail_Demand_Forecasting_Process_Flow_Document.pdf | Complete project workflow documentation |
| random_forest_model.joblib | Final trained Random Forest model |

---

# 📌 Future Improvements

- Implement statistical forecasting models such as ARIMA and Prophet.
- Evaluate deep learning models such as LSTM or GRU.
- Add model explainability using SHAP.
- Deploy the model using FastAPI and Docker.
- Build an interactive forecasting dashboard.

---
---

# 📝 Note on Test Dataset

The original Walmart `test.csv` dataset was not used for model evaluation because it does not contain the target variable (`Weekly_Sales`). Since the developed forecasting model relies on lag-based features (`Lag_1` and `Rolling_Mean_4`), generating predictions for multiple future weeks requires recursive forecasting, where predictions from previous weeks are used to construct features for subsequent weeks.

To ensure a fair and reliable evaluation, the model was trained on historical data and validated using a chronological hold-out strategy, reserving the last 26 weeks as an out-of-time validation set. This approach preserves the temporal nature of the data and provides an unbiased estimate of the model's forecasting performance.


# Author

**Hemanth Goud**

AI / ML Engineer Project