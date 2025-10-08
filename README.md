🌦️ Weather Trend Forecasting

This project focuses on analyzing global weather data to understand temperature patterns and forecast future trends using various data science and machine learning techniques.

Weather-Trend-Forecasting-Project/
│
├── data/
│   ├── GlobalWeatherRepository.csv
│   └── cleaned_normalized_weather.csv
│
├── notebooks/
│   ├── 01_data_cleaning_and_preprocessing.ipynb
│   ├── 02_eda_visualization.ipynb
│   ├── 03_forecasting_models.ipynb
│   └── 04_advanced_analysis_and_insights.ipynb
│
├── models/
│   ├── random_forest_model.pkl
│   ├── linear_regression_model.pkl
│   └── gradient_boosting_model.pkl
│
├── results/
│   ├── evaluation_metrics.csv
│   └── forecast_visualizations/
│
└── README.md

🧹 1. Data Cleaning & Preprocessing

Notebook: 01_data_cleaning_and_preprocessing.ipynb

Steps Performed:
✅ Data Loading

Imported the raw dataset GlobalWeatherRepository.csv using Pandas.

Checked dataset structure, types, and missing values.

🩺 Data Validation

No missing or duplicate values were detected.

Converted last_updated to datetime format for temporal analysis.

📊 Basic Statistics

Calculated:

Max Temperature

Min Temperature

Mean Temperature

Average temperature per country per year

📦 Column Classification

Identified:

Numerical columns: temperature, humidity, pressure, etc.

Categorical columns: city, country, region, etc.

⚠️ Outlier Detection & Removal

Used IQR (Interquartile Range) to detect and remove outliers in numerical columns.

Visualized before and after cleaning using boxplots.

🔄 Normalization

Applied Min-Max Scaling to normalize numerical columns (range: 0–1).

Applied Label Encoding to transform categorical columns into numerical format.

💾 Final Output

Exported cleaned and normalized dataset to:
