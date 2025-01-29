# Forecasting 

## 1. Introduction & Problem Statement
The objective of this project is to forecast **electric load demand** at 15-minute intervals for the given dataset. The project is divided into two main tasks:

- **Task 1:** Short-term forecasting for **December 14, 2020** at a 15-minute frequency.
- **Task 2:** Imputing missing values in the `load` column, which contained approximately **1000 NaNs** in 6 clustered sections.

Given the availability of multiple features (e.g., temperature, humidity, wind speed, etc.), a **machine learning-based approach** using **XGBoost** was chosen for forecasting.
## 2. Approach & Methodology

### Data Preprocessing & Feature Engineering

1. **Handling Missing Data:**
   - Missing values in the `load` column were imputed using machine learning techniques (XGBoost), rather than traditional methods like interpolation.

2. **Feature Engineering:**
   - **Datetime Features:** Extracted additional time-based features (hour, day of the week, etc.) to enhance model performance.
   - **Lags & Rolling Statistics:** Created lag features and rolling averages to capture temporal dependencies and improve forecasting accuracy.

3. **Train-Test Split:**
   - A **90-10 split** was used to train and evaluate the model.
   - **TimeSeriesSplit** was employed for cross-validation to maintain temporal order in the data.
   - 
## 3. Model Training & Forecasting

- **XGBoost** was selected as the a best model due to its robustness in handling tabular time-series data.
- Hyperparameters used: 
  - `n_estimators=100`, 
  - `learning_rate=0.1`, 
  - `objective='reg:squarederror'`.
- **MAPE (Mean Absolute Percentage Error)** was used as the primary evaluation metric.
- The model was trained on historical data and tested on unseen future values.

## 4. Results & Insights

### MAPE Scores:
- **MAPE on Training Data:** ~5.06% (indicating a good fit).
- **MAPE on Test Data: **9.08%**

### Forecasting Performance:
- The model successfully predicted **December 14, 2020**'s load values with reasonable accuracy.

### Imputation of Missing Values:
- The trained XGBoost model was used to **fill NaN values**, ensuring the dataset remained complete.
- The imputed values were saved in a separate **CSV file** for further validation.

## 5. Conclusion :

### ✅ Key Takeaways:
- **XGBoost performed well**, achieving a MAPE of ~9.08%, making it a reliable model for load forecasting.
- Missing values in the `load` column were successfully imputed using machine learning instead of traditional interpolation.
  

