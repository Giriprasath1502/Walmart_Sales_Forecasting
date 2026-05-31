# Retail Sales Forecasting using SARIMA on Walmart M5 Dataset

## Overview

This project implements a retail sales forecasting pipeline using the Walmart M5 Forecasting dataset. The objective is to predict future product demand using historical daily sales data and classical time-series forecasting techniques.

The workflow simulates a real-world retail demand forecasting scenario similar to platforms such as BigBasket, Blinkit, or Amazon Fresh.

The forecasting model used in this project is:

SARIMA (Seasonal AutoRegressive Integrated Moving Average)

The model captures:

* Trend patterns
* Autocorrelation
* Weekly seasonality in retail demand

---

# Dataset

Dataset Used:
Walmart M5 Forecasting Dataset

Source:
https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

Files Used:

* sales_train_validation.csv

Dataset Characteristics:

* 30,490 product-store combinations
* 1,913 days of historical sales
* Multiple product categories
* Store-level sales records
* Real retail demand behavior

---

# Project Workflow

## 1. Data Loading

The sales dataset is loaded into a Pandas DataFrame.

Each row represents:

* One product
* One store
* Daily sales history

Example:
FOODS_3_586_CA_2_validation

---

## 2. Time Series Extraction

A single high-activity SKU is selected for forecasting.

The metadata columns are removed, keeping only:
d_1 → d_1913

This converts the row into a univariate time series.

---

## 3. Activity Filtering

Products with sparse sales are avoided because:

* Sparse demand creates unstable forecasts
* Seasonal patterns become weak
* ARIMA models struggle with excessive zero values

The selected SKU had approximately 99% active sales days.

---

## 4. Visualization

Several visualizations are created:

* Complete sales history
* Rolling average trend
* Weekly seasonality patterns
* Forecast vs actual comparison

These help identify:

* Demand trends
* Seasonal cycles
* Noise levels
* Forecast quality

---

# Forecasting Model

The model used:

SARIMA(1,1,1)(1,1,1,7)

Where:

* (1,1,1) models trend and autocorrelation
* (1,1,1,7) captures weekly seasonality
* 7 represents the weekly retail cycle

The dataset is split into:

* Training data
* 28-day test horizon

The model predicts the next 28 days of sales demand.

---

# Evaluation Metrics

The forecasting model is evaluated using:

* MAE (Mean Absolute Error)
* RMSE (Root Mean Squared Error)

These metrics measure how close the predictions are to actual sales values.

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Statsmodels
* Scikit-learn

---

# Visualizations Included

* Historical sales trend
* Rolling mean analysis
* Weekly demand behavior
* Forecast vs actual comparison

---

# Future Improvements

Potential extensions:

* Prophet forecasting
* LightGBM forecasting
* LSTM/Transformer models
* Amazon Chronos
* Google TimesFM
* Multi-SKU forecasting
* Promotion-aware forecasting
* Price-sensitive forecasting

---

# Real-World Applications

This forecasting pipeline can be adapted for:

* Grocery demand prediction
* Inventory optimization
* Supply chain forecasting
* Warehouse planning
* Retail analytics
* Dynamic stocking systems

---

# Results

The SARIMA model successfully learned:

* Historical sales trends
* Weekly seasonal behavior
* Demand fluctuations

and generated future demand forecasts for retail inventory planning scenarios.

---

# Repository Structure

```bash
Retail-Sales-Forecasting/
│
├── notebook.ipynb
├── README.md
├── requirements.txt
└── visualizations/
```

---

# Installation

```bash
pip install pandas
pip install numpy
pip install matplotlib
pip install statsmodels
pip install scikit-learn
```

---

# Running the Project

1. Download the M5 Forecasting dataset from Kaggle
2. Open the notebook
3. Run cells sequentially
4. Train the SARIMA model
5. Generate forecasts and visualizations

---
