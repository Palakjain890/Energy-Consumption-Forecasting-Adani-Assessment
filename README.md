# 🔌 Energy Consumption Forecasting using Machine Learning

## 📌 Problem Statement
The objective of this project is to forecast short-term electricity consumption using historical hourly demand data from a transmission system operator. The dataset represents a univariate time series with strong seasonal patterns. The goal is to build a data-driven machine learning model to predict future energy demand and analyze its implications for energy management and sustainability.

---

## 📂 Dataset
The dataset contains hourly electricity consumption values along with timestamps.

Key columns:
- Start time UTC → Timestamp of each hour
- Electricity consumption (MWh) → Target variable (energy demand)

The dataset spans multiple years, capturing daily and weekly seasonal patterns.

---

## 🛠 Methodology

### 1. Data Preprocessing
- Converted timestamp column to datetime format.
- Sorted data chronologically to preserve time order.
- Removed unnecessary columns.
- Created lag-based features to convert time series into supervised learning format.
- Removed missing values created due to lag shifting.

### 2. Exploratory Data Analysis (EDA)
- Visualized electricity demand over time to observe seasonality.
- Checked distribution of energy consumption values.
- Identified strong daily and weekly cycles indicating seasonal behavior.

### 3. Feature Engineering
Lag features were created to capture temporal dependencies:
- Lag 1 hour (short-term dependency)
- Lag 24 hours (daily seasonality)
- Lag 168 hours (weekly seasonality)

These features allow machine learning models to learn time-based patterns.

---

## 🤖 Model Selection

### Random Forest Regressor (Primary Model)
Random Forest was selected because:
- It can capture nonlinear relationships.
- It models interactions between lag features.
- It does not require stationarity assumptions like ARIMA.
- It is robust to noise and performs well with tabular data.

### Linear Regression (Baseline Model)
Linear Regression was used as a baseline to evaluate whether linear assumptions are sufficient for this dataset. Higher error compared to Random Forest indicates that the data exhibits nonlinear temporal behavior.

---

## 📊 Model Evaluation

A time-based train-test split was used to avoid data leakage.

Evaluation metrics:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

Additionally, predicted values were compared with actual values using time-series plots to visually assess model performance and seasonal trend capture.

---

## ⚠ Overfitting Analysis

The Random Forest model showed lower training error compared to test error, indicating some degree of overfitting, which is expected for ensemble tree-based models. Regularization techniques such as limiting tree depth and increasing minimum samples per leaf were explored to reduce variance. However, moderate overfitting is acceptable for this assessment as the objective is to demonstrate modeling approach rather than production deployment.

---

## 🌱 Interpretation and Business Impact

The forecasting model successfully captures daily and weekly demand patterns in electricity consumption. Accurate short-term forecasting can help transmission operators:
- Optimize generation scheduling
- Improve grid stability
- Reduce energy wastage
- Support sustainable energy management by minimizing unnecessary reserve power usage

---

## ▶ How to Run

1. Install required libraries:
   pip install pandas scikit-learn matplotlib

2. Run the notebook:
   jupyter notebook Energy_prediction.ipynb

Ensure that the dataset file `Predicting Energy Consumption.csv` is in the same directory as the notebook.

---

## 📌 Note

This project was completed as part of a technical assessment for a Predictive Analytics role, focusing on modeling approach, feature engineering, and interpretation rather than enterprise-level optimization.
