# Data Science Portfolio: Time Series Projects

This repository contains my portfolio of Time Series projects showcasing different techniques and datasets.

## Projects

# Comprehensive E-commerce Analytics: Forecasting, Customer Segmentation, and Performance Modeling

This repository contains a deep-dive data science project performed on a classic online retail dataset. The project walks through the entire data science lifecycle, from data cleaning and preprocessing to advanced modeling, evaluation, and interpretation of results.

## Project Overview

The primary goal of this project was to extract actionable business insights from a large transactional dataset. This was achieved through two major analytical modules:

1.  **Sales Forecasting:** Predicting future daily sales revenue using a variety of time-series models.
2.  **Customer Segmentation:** Using RFM (Recency, Frequency, Monetary) analysis to segment the customer base for targeted marketing strategies.

The project emphasizes not just building models, but critically evaluating and iteratively improving them to achieve robust and reliable outcomes.

## Table of Contents

- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Part 1: Sales Forecasting](#part-1-sales-forecasting)
  - [Models Compared](#models-compared)
  - [Key Findings](#key-findings)
- [Part 2: RFM Customer Segmentation](#part-2-rfm-customer-segmentation)
  - [Methodology](#methodology)
  - [Key Findings](#key-findings-1)
- [Technologies Used](#technologies-used)
- [How to Run This Project](#how-to-run-this-project)

## Dataset

The analysis uses the "Online Retail" dataset from the UCI Machine Learning Repository. It contains transactional data for a UK-based online retail company from December 2009 to December 2011.

-   **Size:** ~1,000,000+ transactions before cleaning.
-   **Key Attributes:** `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country`.

## Project Workflow

1.  **Data Cleaning and Preprocessing:**
    -   Handled missing values, especially `CustomerID`.
    -   Removed duplicate entries and canceled orders.
    -   Filtered non-product transactions (e.g., postage, manual entries).
    -   Engineered a `TotalPrice` feature.
2.  **Exploratory Data Analysis (EDA):**
    -   Investigated sales trends, seasonality, and geographic distribution.
3.  **Time-Series Forecasting:**
    -   Aggregated data to a daily sales series.
    -   Compared Prophet, XGBoost, and LSTM models.
    -   Performed advanced feature engineering and hyperparameter tuning to improve model performance.
4.  **RFM Customer Segmentation:**
    -   Calculated Recency, Frequency, and Monetary metrics for each customer.
    -   Segmented customers into actionable groups like "Champions," "At Risk," and "Hibernating."
    -   Visualized segment characteristics for strategic planning.

## Part 1: Sales Forecasting

### Models Compared

-   **Prophet:** A decomposable time-series model from Facebook, excellent for its automation and interpretability.
-   **XGBoost:** A powerful gradient-boosting algorithm, treated as a regression problem with engineered time-based features.
-   **LSTM:** A deep learning (RNN) model, initially considered for its ability to learn from sequences.

### Key Findings

-   The initial **LSTM model performed poorly** (negative R² score), primarily due to insufficient data for a deep learning approach and its inability to easily capture the explicit seasonality that tree-based models can. It was subsequently dropped from the analysis.
-   The initial Prophet and XGBoost models captured the weekly seasonality but failed to predict the magnitude of sales peaks.
-   **Improving Prophet** with a simple custom holiday period for the "Christmas rush" actually degraded its performance. The simplistic definition interfered with its more nuanced, built-in seasonality modeling.
-   **Improving XGBoost** was a major success. By engineering advanced features (lags, rolling windows, Fourier terms) and performing automated hyperparameter tuning with Optuna, the model's performance significantly improved.
-   **Final Conclusion:** The **Ultimate XGBoost** model was the definitive winner, achieving the highest accuracy (R² of 0.41) and demonstrating the power of sophisticated feature engineering for time-series regression.

## Part 2: RFM Customer Segmentation

### Methodology

-   **Recency**, **Frequency**, and **Monetary** values were calculated for over 5,800 customers.
-   Customers were scored on a 1-4 scale for each metric using quantiles to handle skewed data distributions.
-   Scores were combined to assign customers to 9 distinct segments, from "Champions" to "Hibernating."

### Key Findings

-   The analysis successfully categorized the customer base, revealing a classic retail distribution: a small core of high-value **Champions** (13% of customers) and a large group of inactive **Hibernating** customers (35%).
-   Identified a critical segment of **"Cannot Lose Them"** customers—previously high-value customers who have not purchased in a long time, making them a prime target for win-back campaigns.
-   Provided actionable lists of customer IDs for each segment, enabling direct implementation of targeted marketing strategies.

## Technologies Used

-   **Python 3.x**
-   **Pandas:** For data manipulation and analysis.
-   **NumPy:** For numerical operations.
-   **Matplotlib & Seaborn:** For data visualization.
-   **scikit-learn:** For evaluation metrics.
-   **Prophet:** For time-series forecasting.
-   **XGBoost:** For gradient-boosted machine learning models.
-   **Optuna:** For hyperparameter optimization.
-   **Jupyter Notebook / VS Code:** For development.

