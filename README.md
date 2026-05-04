# 🌍 Global Weather Trend Forecasting

**PM Accelerator — Tech Assessment**

> PM Accelerator is the #1 Product Manager accelerator program in the world. We are dedicated to helping aspiring and experienced PMs break into the industry and accelerate their careers through hands-on experience, mentorship, and a global community.

---

## 📋 Overview

This project analyzes the [Global Weather Repository](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository/code) dataset to forecast weather trends and uncover climate patterns across countries and continents. The analysis covers the full data science pipeline: preprocessing, EDA, outlier detection, correlation analysis, feature importance, predictive modeling, and geographical visualization.

**Target variable:** `temperature_celsius`  
**Time range:** May 2024 – May 2026  
**Scope:** Daily weather records from cities worldwide (40+ features)

---

## 📁 Repository Structure

```
├── PM_Accelerator_mission.ipynb   # Main notebook with all analyses
├── requirements.txt               # Required Python libraries
├── GlobalWeatherRepository.zip    # Data used in this project
└── README.md                      # This file
```

> **Note:** To run this code it's needed to unzip GlobalWeatherRepository.zip which contains the data used. Another option is to download it from [Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository/code) and place it in the same directory as the notebook.

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/Facubian/World-Weather-Assesment.git
cd World-Weather-Assesment
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Unzip or Download the dataset**
Unzip the GlobalWeatherRepository.zip file which contains the data used and place the csv in the project root. If running on Google Colab, upload it to `/content/` or update the path in the notebook's loading cell.

Download `GlobalWeatherRepository.csv` from [Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository/code) and place it in the project root. If running on Google Colab, upload it to `/content/` or update the path in the notebook's loading cell.

**4. Run the notebook**
```bash
jupyter notebook PM_Accelerator_mission.ipynb
```

---

## 🔬 Methodology

### 1. Data Cleaning & Preprocessing
- Parsed `last_updated` as datetime
- Removed duplicate rows and null values
- Engineered time features: `hour`, `day`, `is_day` (day/night flag)
- Encoded `country` as a categorical numeric variable
- Mapped each country to its continent for regional analysis
- Removed physically impossible values identified via pairplot (e.g., negative PM10, wind speed > 1000 km/h, temperature > 70°C)

### 2. Exploratory Data Analysis
- **Day vs Night:** Distribution and boxplot comparison of temperature and precipitation between daytime (6:00–18:00) and nighttime hours
- **Time Series:** Rolling mean and standard deviation bands (±1σ, ±2σ) for temperature and precipitation over the full date range
- **Outlier Analysis:** IQR-based detection across 9 key variables, reporting Q1, Q3, IQR, lower/upper limits, outlier count, and percentage

### 3. Correlation Analysis
- Computed full correlation matrix across 19 numeric features
- Visualized with an annotated heatmap
- Selected features with |correlation| > 0.1 with `temperature_celsius` for modeling

### 4. Feature Importance
- Used `RandomForestRegressor` averaged over 10 runs to estimate stable feature importances
- Iteratively removed low-importance features
- Ran two separate experiments: **with** and **without** `feels_like_celsius` to assess data leakage

### 5. Predictive Modeling
Three models were trained and evaluated on an 80/20 train-test split (`random_state=42`):

| Model | Description |
|---|---|
| Linear Regression | Baseline linear model |
| Random Forest | 200 trees, no max depth |
| XGBoost | 100 estimators, learning rate 0.1, max depth 3 |

An **ensemble** (simple average of the three predictions) was also evaluated.

Metrics reported: **RMSE** and **R²**, for both the with/without `feels_like_celsius` scenarios.

### 6. Geographical Patterns
- Choropleth maps (Plotly) showing mean temperature and PM2.5 by country
- Boxplots comparing temperature, precipitation, humidity, wind speed, and pressure across 6 continents

---

## 📦 Requirements

```
pandas
numpy
matplotlib
seaborn
scipy
plotly
scikit-learn
xgboost
jupyter
```

Install all with:
```bash
pip install -r requirements.txt
```

---

## 📊 Key Results

- **Day temperatures** are on average higher than night temperatures, as expected, with a wider distribution during daytime hours.
- **Correlation analysis** shows `feels_like_celsius`, `humidity`, and `air_quality_Carbon_Monoxide` as the strongest predictors of temperature.
- **With `feels_like_celsius`:** All three models achieve very high R² (expected, as it is a near-linear transformation of the target).
- **Without `feels_like_celsius`:** Performance drops significantly, giving a more honest picture of predictive power.
- **Geographical patterns:** Africa and Asia show the highest mean temperatures; Europe and Oceania the lowest. Asia leads in PM2.5 concentration.

---

## 📌 Notes

- The notebook was developed on Google Colab. The dataset path `/content/GlobalWeatherRepository.csv` may need to be updated when running locally.
- Feature importance runs 10 Random Forest fits per iteration — this may take a few minutes depending on hardware.
