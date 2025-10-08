# 🌦️ Weather Trend Forecasting

This project focuses on analyzing global weather data to understand temperature patterns and forecast future trends using various data science and machine learning techniques.

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



---

## 📊 Exploratory Data Analysis (EDA)

### 🔹 Dataset Overview
- Dataset loaded from: `../data/GlobalWeatherRepository.csv`
- Key features include:
  - **Temperature (°C / °F)**
  - **Humidity**
  - **Pressure (mb)**
  - **Precipitation (mm)**
  - **Wind Speed (kph)**
  - **Visibility (km)**
  - **Air Quality (PM2.5, PM10)**
  - **UV Index**, **Cloud Cover**, **Condition Text**

---

## 📈 Key Visualizations

### 🌡️ 1. Temperature Distributions
- Histograms showing temperature spread in Celsius and Fahrenheit.

### 🔥 2. Correlation Heatmap
- Highlights relationships between temperature, humidity, pressure, and precipitation.

### 🗺️ 3. Country-Level Average Temperature
- Top 15 hottest countries visualized via bar chart.

### 🌧️ 4. Feature Relationships
- **Temperature vs Precipitation**
- **Temperature (°C) vs (°F)**
- **Temperature vs Humidity**
- **Cloud Cover vs UV Index**
- **Pressure vs Precipitation**
- **PM2.5 vs PM10**
- **Wind Speed vs Visibility**
- **Latitude vs Temperature**

### 🕒 5. Temporal Trends
- Line plot showing **temperature changes over time**.

### ☁️ 6. Weather Condition Frequency
- Bar chart of the most common global weather conditions.

### 🧩 7. PCA for Dimensionality Reduction
- Principal Component Analysis visualizing feature variance.
- **Explained variance ratio:** ~XX% (replace with your output).

### 🌡️ 8. Heat Index vs Actual Temperature
- Scatter plot comparing **feels-like** temperature with actual temperature, colored by humidity.

---
 
## 🌍 Advanced Exploratory Data Analysis (EDA)

This notebook performs **advanced data analysis** on cleaned and normalized weather data, focusing on **anomaly detection** techniques to identify unusual or extreme weather patterns using multiple models.

---

### 📘 Notebook Overview
**File:** `03_advanced_exploratory_data_analysis.ipynb`  
**Dataset:** `../data/cleaned_normalized_weather.csv`

---

### 🧾 1. Dataset Overview
After loading the cleaned dataset:
- Displays dataset shape and column information.
- Focuses on **numerical meteorological features** such as:
  - `temperature_celsius`
  - `wind_kph`
  - `pressure_mb`
  - `humidity`
  - `visibility_km`
  - `gust_kph`
  - `air_quality_PM2.5`
  - `air_quality_PM10`
  - `air_quality_Ozone`

---

### ⚙️ 2. Anomaly Detection Techniques

The notebook applies three robust anomaly detection models to identify **irregular weather data points**:

### 🧩 a. Isolation Forest
- Detects **global outliers** using random tree partitions.  
- Configured with `contamination=0.02`.

### 🔍 b. Local Outlier Factor (LOF)
- Detects **local outliers** based on neighborhood density.  
- Uses `n_neighbors=20`, `contamination=0.02`.

### ⚡ c. One-Class SVM
- Identifies anomalies using a **non-linear boundary (RBF kernel)**.  
- Parameters: `nu=0.02`, `gamma='auto'`.

---

### 📊 3. Visualizing Detected Anomalies

### 🟢 Isolation Forest
Scatter plot showing:
- **X-axis:** Temperature (°C)  
- **Y-axis:** Pressure (mb)  
- Green = Normal data  
- Red = Detected anomalies  

### 📈 Comparison of Detectors
The notebook prints the count of anomalies found by each method: 
  1- Isolation Forest anomalies: 667
  2- Local Outlier Factor anomalies: 667
  3- One-Class SVM anomalies: 666

---

## 🧠 4. Anomaly Insights

- Extracts and displays top 10 anomalous records:
  - Country  
  - Location name  
  - Condition text  
  - Temperature  
  - Pressure  

These anomalies often correspond to **extreme weather events** or **sensor errors**.

---

## 🔥 5. Correlation Analysis

A **heatmap** visualizes the correlation between numerical features like temperature, wind speed, humidity, and air quality indicators.

---
# 🤖 Model Building

This notebook focuses on building and evaluating **machine learning models** to forecast temperature trends using the cleaned and normalized weather dataset.

---

## 📘 Notebook Overview
**File:** `04_model_building.ipynb`  
**Dataset:** `../data/cleaned_normalized_weather.csv`

---

## 🧾 1. Data Preparation

### 🧩 Steps:
1. Loaded dataset and converted `last_updated` to datetime.
2. Sorted records by timestamp for temporal consistency.
3. Extracted time-based features:
   - `year`, `month`, `day`, `hour`, `dayofweek`
4. Selected **target variable** and **input features**:
   ```python
   target = 'temperature_celsius'
   features = [
       'month', 'day', 'hour', 'humidity', 'wind_kph', 'pressure_mb',
       'precip_mm', 'feels_like_celsius', 'visibility_km', 'uv_index'
   ]
5- Split dataset chronologically:
    80% → Training set
    20% → Test set

--- 

⚙️ 2. Forecasting Models

The following models were trained and compared:

📈 Linear Regression

A simple baseline model capturing linear relationships.

🌲 Random Forest Regressor

An ensemble model with n_estimators=200, providing higher accuracy and robustness to noise.

⚡ XGBoost Regressor

A gradient boosting model optimized for performance:  model = xgb.XGBRegressor(n_estimators=300, learning_rate=0.05, random_state=42)
 
--- 

📊 3. Model Evaluation

Each model was evaluated using the following metrics:

* MAE — Mean Absolute Error

* RMSE — Root Mean Squared Error

* R² — Coefficient of Determination

### Evaluation Function
def evaluate_model(y_true, y_pred, model_name):
    mae = mean_absolute_error(y_true, y_pred)
    rmse = np.sqrt(mean_squared_error(y_true, y_pred))
    r2 = r2_score(y_true, y_pred)
    print(f"\n{model_name} Performance:")
    print(f"MAE:  {mae:.3f}")
    print(f"RMSE: {rmse:.3f}")
    print(f"R²:   {r2:.3f}") ... ```

| Model             | MAE    | RMSE   | R²       |
| ----------------- | ------ | ------ | -------- |
| Linear Regression | 0.0005 | 0.0006 | 0.999987 |
| Random Forest     | 0.0002 | 0.0005 | 0.999991 |
| XGBoost           | 0.0003 | 0.0005 | 0.999990 |

---

📉 4. Visualizations
🔹 Actual vs Predicted Temperature

Line plots comparing true vs predicted values for each model over time.

🔹 7-Day Temperature Forecast

Forecasts next 7 days of temperature using Random Forest:

Assumes average values for non-temporal features.

Plotted predicted temperatures over future dates.

🔹 Model Comparison

Overlayed predictions from all three models:

Blue → Actual

Orange → Random Forest

Green → XGBoost

🌟 5. Feature Importance (XGBoost)

Bar chart ranking the most influential features in forecasting:

feels_like_celsius

humidity

pressure_mb

uv_index

precip_mm


