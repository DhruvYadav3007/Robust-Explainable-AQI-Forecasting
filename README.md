# Robust and Explainable AQI Forecasting under Missing Pollutant Observations

**An Imputation-Based Machine Learning Approach**

## Overview

This research investigates the robustness and explainability of Machine Learning-based Air Quality Index (AQI) prediction when pollutant observations are missing.

The study evaluates an XGBoost-based AQI prediction model under controlled missingness in six major pollutants: PM2.5, PM10, NO2, SO2, CO, and O3.

Six imputation strategies are compared across four missingness levels (5%, 10%, 20%, and 30%) to understand their impact on prediction accuracy and model reliability. SHAP is further employed to investigate changes in feature importance under incomplete pollutant observations.

## Research Objectives

- Evaluate AQI prediction performance under increasing pollutant missingness.
- Compare six imputation strategies for handling missing observations.
- Analyze the robustness of XGBoost-based AQI prediction.
- Investigate changes in feature importance using SHAP.
- Examine whether predictive accuracy and model interpretability remain consistent under incomplete data.

## Dataset

The study uses the Delhi Pollution AQI dataset, focusing on the NSIT Dwarka monitoring station in Delhi.

| Parameter | Description |
|---|---|
| Monitoring Station | NSIT Dwarka, Delhi |
| Time Period | 2020–2025 |
| Original Observations | 8,768 |
| Modeling Observations | 8,740 |
| Observation Frequency | Four observations per day |
| Target Variable | Air Quality Index (AQI) |

### Features

- **Pollutants:** PM2.5, PM10, NO2, SO2, CO, O3
- **Meteorological:** Temperature, Humidity, Wind Speed, Visibility
- **Temporal:** Hour, Day, Month, Year, Day of Week, Season
- **Historical:** Lagged AQI observations

## Methodology

### 1. Data Preprocessing
- Chronological data sorting and preprocessing.
- Generation of historical AQI lag features.
- Separation of training and testing datasets.

### 2. Controlled Missingness

Missing values are introduced into the six pollutant variables at four levels:

- 5%
- 10%
- 20%
- 30%

### 3. Imputation Techniques

Six strategies are evaluated:

1. Mean Imputation
2. Median Imputation
3. Forward Fill
4. Linear Interpolation
5. K-Nearest Neighbors (KNN)
6. XGBoost-based Imputation

### 4. AQI Prediction

XGBoost Regressor is used as the common prediction model to compare the impact of different missing-data handling strategies.

### 5. Model Explainability

SHAP (SHapley Additive exPlanations) is used to analyze feature contributions and investigate how model behaviour changes as pollutant observations become unavailable.

## Experimental Configuration

| Parameter | Configuration |
|---|---|
| Training Period | 2020–2024 |
| Testing Period | 2025 |
| Prediction Model | XGBoost |
| Estimators | 300 |
| Maximum Depth | 6 |
| Learning Rate | 0.05 |
| Evaluation Metrics | MAE, RMSE, R² |
| Explainability | SHAP |

## Results

### Complete-Data Baseline

| Metric | Result |
|---|---:|
| MAE | 0.7774 |
| RMSE | 1.2228 |
| R² | 0.9999 |

### Average MAE Across Missingness Levels

| Imputation Method | Average MAE |
|---|---:|
| Mean | 3.8473 |
| Median | 3.8919 |
| XGBoost | 4.3438 |
| KNN | 5.1726 |
| Linear Interpolation | 5.9261 |
| Forward Fill | 6.4703 |

Mean imputation achieved the lowest average MAE among the six evaluated strategies.

### SHAP Explainability Findings

- PM2.5 was the dominant predictor under complete-data conditions, contributing 77.40% of feature importance.
- PM10 was the second most influential feature.
- Under missing-pollutant conditions, visibility became the dominant feature.
- Meteorological and seasonal features gained importance as pollutant observations became increasingly unavailable.

These findings highlight the importance of evaluating model explainability alongside predictive performance.

## Repository Structure

```text
Robust-Explainable-AQI-Forecasting/
│
├── models/
│   └── Trained model files
│
├── figures/
│   └── Experimental visualizations
│
├── paper/
│   └── AQI_Robust_Research_Paper.pdf
│
└── README.md
```

## Technologies Used

- Python
- XGBoost
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- SHAP
- Machine Learning
- Explainable AI

## Research Paper

The complete research paper is available in the [`paper/`](paper/) directory.

**Title:** Robust and Explainable AQI Forecasting under Missing Pollutant: An Imputation-Based Machine Learning Approach.

## Future Work

- Evaluation using real-world sensor outages.
- Testing across independent air quality monitoring stations.
- Exploring additional imputation techniques.
- Investigating alternative missingness mechanisms.
- Improving robustness and interpretability under changing environmental conditions.

---

**Research Areas:** Machine Learning | Air Quality Prediction | Missing Data Imputation | XGBoost | Explainable AI | SHAP
