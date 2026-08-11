# Task 02 – Exploratory Data Analysis & Baseline Modeling

## Overview

This task was completed as part of my AI/ML internship at Career Launchpad.

The objective of this task was to perform Exploratory Data Analysis (EDA), feature engineering, identify important relationships in the dataset, and build baseline regression models for energy consumption prediction.

## Dataset

The dataset contains energy consumption measurements from a steel manufacturing plant.

The engineered dataset contains:

- 35,040 records
- 17 columns

The target variable used for prediction was:

- `Usage_kWh`

## Part 1 – Exploratory Data Analysis

The following EDA steps were performed:

- Loaded and inspected the dataset
- Checked dataset shape and column information
- Examined numerical and categorical features
- Analyzed energy consumption distribution
- Performed outlier analysis using the IQR method
- Created a boxplot for `Usage_kWh`
- Generated a correlation heatmap
- Identified the features most strongly correlated with energy usage
- Compared average energy consumption across load types
- Analyzed average energy consumption by hour of the day

## Feature Engineering

Several features were already engineered or prepared for modeling, including:

- `Hour`
- `Day_of_Week_Extracted`
- `Month`
- `Day_Type`
- `Power_Factor_Ratio`
- `High_Load`

The `High_Load` feature was created using the 75th percentile of `Usage_kWh`.

The calculated 75th percentile was approximately:

`51.2375 kWh`

Observations above this value were classified as high-load observations.

## Correlation Analysis

The three features with the strongest correlation with `Usage_kWh` were:

| Feature | Correlation |
|---|---:|
| CO2(tCO2) | 0.9882 |
| Lagging_Current_Reactive.Power_kVarh | 0.8961 |
| High_Load | 0.8678 |

These relationships provided useful insight into variables associated with energy consumption.

## Energy Consumption by Load Type

Average energy consumption was calculated for each load category:

| Load Type | Average Usage (kWh) |
|---|---:|
| Light Load | 8.63 |
| Medium Load | 38.45 |
| Maximum Load | 59.27 |

The analysis showed substantially higher energy consumption for Maximum Load compared with Light Load.

## Hourly Energy Usage

Energy consumption was also analyzed by hour of the day.

The highest average usage was:

- **58.55 kWh at 9:00**

The lowest average usage was:

- **4.22 kWh at 6:00**

This analysis helped identify periods of high and low energy demand.

## Baseline Regression Models

Four regression models were trained and evaluated:

1. Linear Regression
2. Ridge Regression
3. Decision Tree
4. Random Forest

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

## Model Evaluation Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 2.6339 | 4.1460 | 0.9849 |
| Ridge Regression | 4.3604 | 6.2666 | 0.9655 |
| Decision Tree | 0.5331 | 1.4737 | 0.9981 |
| Random Forest | 0.3541 | 1.0439 | 0.9990 |

## 5-Fold Cross-Validation

5-fold cross-validation was performed to compare model performance more reliably.

| Model | Test RMSE | Mean CV RMSE |
|---|---:|---:|
| Linear Regression | 4.1460 | 4.5125 |
| Ridge Regression | 6.2666 | 6.2285 |
| Decision Tree | 1.4737 | 1.4785 |
| Random Forest | 1.0439 | 1.0252 |

## Best Performing Model

Based on the 5-fold cross-validation results, **Random Forest** was selected as the best-performing baseline model.

Results:

- Mean CV RMSE: **1.0252**
- Test RMSE: **1.0439**
- Test MAE: **0.3541**
- Test R²: **0.9990**

The Random Forest model achieved the lowest cross-validation RMSE among the four tested models.

## Files

### `week2_eda.ipynb`

Contains the exploratory data analysis, feature engineering, outlier analysis, correlation analysis, and energy consumption visualizations.

### `week2_baseline_models.ipynb`

Contains preprocessing, baseline regression models, model evaluation, and 5-fold cross-validation.

### `steel_energy_engineered.csv`

Contains the engineered dataset used for the analysis and modeling.

## Tools & Libraries

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Key Learning Outcomes

Through this task, I practiced:

- Exploratory Data Analysis
- Feature Engineering
- Data Visualization
- Outlier Detection
- Correlation Analysis
- Regression Modeling
- Model Evaluation
- Cross-Validation
- Model Comparison and Selection
