# 🌦️ Weather Trend Forecasting

This project focuses on analyzing global weather data to understand temperature patterns and forecast future trends using various data science and machine learning techniques.

---

## 📁 Project Structure

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



---

## 🧹 1. Data Cleaning & Preprocessing

**Notebook:** `01_data_cleaning_and_preprocessing.ipynb`

### 🔹 Steps Performed

---

### ✅ Data Loading
- Imported the raw dataset **`GlobalWeatherRepository.csv`** using **Pandas**.  
- Checked dataset structure, data types, and missing values.  

---

### 🩺 Data Validation
- No missing or duplicate values were detected.  
- Converted the `last_updated` column to **datetime** format for temporal analysis.  

---

### 📊 Basic Statistics
Calculated the following metrics to summarize the dataset:
- **Maximum Temperature (°C)**
- **Minimum Temperature (°C)**
- **Mean Temperature (°C)**
- **Average Temperature per Country per Year**

---

### 📦 Column Classification
Identified key feature types:
- **Numerical columns:** temperature, humidity, pressure, etc.  
- **Categorical columns:** city, country, region, etc.  

---

### ⚠️ Outlier Detection & Removal
- Used the **Interquartile Range (IQR)** method to detect and remove outliers in numerical columns.  
- Visualized distributions **before and after cleaning** using **boxplots** for comparison.  

---

### 🔄 Normalization
- Applied **Min-Max Scaling** to normalize all numerical columns (range: `0–1`).  
- Applied **Label Encoding** to transform categorical columns into numeric form for model compatibility.  

---

### 💾 Final Output
- Exported the cleaned and normalized dataset to: data/cleaned_normalized_weather.csv
- This dataset serves as the foundation for **EDA** and **forecasting models** developed in later notebooks.

