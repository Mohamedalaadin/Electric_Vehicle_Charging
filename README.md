# **Time Series Analysis and Forecasting of kWh Consumption**

## Introduction

In this project, we aim to forecast the total energy consumption (in kWh) from a dataset of electric vehicle (EV) charging sessions. Accurate forecasting of energy consumption is crucial for efficient energy management and planning in EV charging stations. This can help in optimizing the energy supply, managing loads, and ensuring that the charging infrastructure operates smoothly.

## Problem Definition

The primary objective of this analysis is to develop a model that can accurately predict the total energy consumption (kWh) for future time periods based on historical data. Given the dataset’s time span of less than a year, we also need to address challenges related to seasonality and potential data trends.

## Dataset Description

The dataset used for this project is sourced from Kaggle and contains detailed information on electric vehicle charging sessions. It includes data from 3,395 high-resolution charging sessions from 85 EV drivers at 105 stations across 25 sites. These sites are part of a workplace charging program under the U.S. Department of Energy's workplace charging challenge. The data is available in CSV format and can be found at the following link: [Electric Vehicle Charging Dataset on Kaggle](https://www.kaggle.com/datasets/michaelbryantds/electric-vehicle-charging-dataset/code?datasetId=2597433&sortBy=voteCount).

## Approach (Thinking Path)

### Initial Thoughts and Planning

When I first received the dataset and the task of forecasting the total energy consumption (kWh), I recognized the need for a systematic and methodical approach. Understanding that the data spans less than a year, I anticipated challenges in detecting seasonality. Therefore, I planned to take the following steps to ensure a thorough analysis and accurate forecasting:

### 1. Data Understanding and Preparation

- **Initial Data Loading**: Load the dataset into a pandas DataFrame to explore its structure and content.
- **Data Cleaning**: Handle missing or inconsistent values, check for null values, and ensure proper data types. Notably, there were no missing values except in the *distance column*.
- **Date-Time Conversion**: Convert relevant columns into a datetime format.

### 2. Exploratory Data Analysis (EDA)

- **Descriptive Statistics**: Start with basic descriptive statistics to get an overview of the data distribution, central tendencies, and variability.
- **Visual Analysis**: Use plots and graphs to visualize the data, identify trends, patterns, and potential outliers, including time series plots for kWh consumption.
- **Outlier Detection**: Use box plots and scatter plots to identify and handle outliers, especially in the kWhTotal.

### 3. Feature Engineering

- **Lag Features**: Create lagged versions of the kWh consumption data to capture temporal dependencies.
- **Day of the Week Analysis**: Add one-hot encoded features for each day, recognizing that energy consumption might vary by day of the week. Weekends generally showed lower kWh consumption.
- **Charge Time Hours**: Include this feature after resampling it to match the kWh data's frequency, as charge time might influence energy consumption.

### 4. Handling Missing Values

- **Rolling Mean Imputation**: Use rolling means to fill any gaps in the data. This method leverages the local mean, which can be more reliable than global mean imputation. A 7-day window was found to be optimal for capturing trends without being too sensitive.
- **Validation**: Validate the results after filling missing values to ensure the imputation did not introduce bias.

### 5. Model Selection and Training

- **Model Exploration**: Start with AutoReg and ARIMA models due to their suitability for time series data. Ensure data stationarity for ARIMA.
- **Feature Addition**: Enhance the model by adding more features (7-day lags, day of the week flags, and charge time). Use the correlation matrix to select the most relevant features.
- **Alternative Models**: Explore different models including Linear Regression, XGBoost, and Random Forest, which provided better results due to the enriched feature set.

### 6. Hyperparameter Tuning

- **Grid Search**: Use Grid Search for hyperparameter tuning to find the optimal model configuration for models like Random Forest and XGBoost.

### 7. Forecasting and Evaluation

- **Walk-Forward Validation**: Use walk-forward validation for testing the model, which involves training on past data and predicting the next time step iteratively.
- **Performance Metrics**: Evaluate the model using metrics such as Mean Absolute Error (MAE) to quantify prediction accuracy.
- **Result Interpretation**: Compare the model predictions with actual values and provide insights into the energy consumption patterns.

## Implementation Steps

Following this plan, I executed the steps as described:

- Loaded and cleaned the data, converting date columns and handling missing values.
- Conducted EDA to visualize trends and detect outliers.
- Engineered relevant features, including lag features and one-hot encoded weekdays.
- Filled missing values using rolling means and validated the imputation.
- Selected and trained models, performing hyperparameter tuning where necessary.
- Used walk-forward validation for forecasting and evaluated model performance using MAE.
- Interpreted the results and prepared the final notebook with all steps documented and visualized.

## Conclusion

This project demonstrates a comprehensive approach to time series forecasting for energy consumption in EV charging stations. The use of feature engineering, model selection, and hyperparameter tuning contributed to the development of an accurate and reliable forecasting model. The insights gained from this analysis can help in optimizing energy management and planning in EV charging stations.

Feel free to reach out if you have any questions or suggestions!

---
