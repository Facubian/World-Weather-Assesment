# PM Accelerator Data Scientist Assesment: 📊 Weather Trend Forecasting
📌 Overview

This project analyzes the Global Weather Repository dataset to explore weather patterns and build forecasting models. It covers data cleaning, exploratory data analysis (EDA), time series modeling, and advanced analytical techniques.

The goal is to showcase end-to-end data science skills, from preprocessing to model evaluation and insights generation.

📂 Dataset
Source: Kaggle – Global Weather Repository
Contains daily weather data across multiple cities worldwide
Includes 40+ features such as:
Temperature
Precipitation
Air quality
Wind conditions
Timestamps (last_updated)

⚙️ Project Structure
├── notebook.ipynb
├── README.md
├── requirements.txt
🧹 Data Cleaning & Preprocessing
Handled missing values using appropriate imputation strategies
Removed invalid and inconsistent values (e.g., negative precipitation)
Detected and filtered outliers using:
Manual inspection
Interquartile Range (IQR) method
Normalized numerical features for modeling
📊 Exploratory Data Analysis (EDA)

Performed EDA to identify trends, patterns, and relationships:

Distribution analysis (histograms)
Temperature and precipitation analysis
Correlation analysis between variables
Time-based trends using last_updated
Key insights:
Temperature shows clear temporal patterns
Precipitation is highly skewed with extreme values
Some variables show moderate correlation with weather conditions
⏳ Time Series Analysis
Converted last_updated into datetime format
Resampled data to analyze temporal trends
Extracted time-based features:
Hour
Day
Month
🤖 Model Building

Implemented forecasting models to predict weather variables:

Models used:
Linear Regression (baseline)
Random Forest Regressor
XGBoost Regressor
Evaluation metrics:
MAE (Mean Absolute Error)
RMSE (Root Mean Squared Error)
🔁 Ensemble Model

An ensemble approach was implemented by averaging predictions from multiple models to improve performance.

🚨 Advanced Analysis
🔍 Anomaly Detection
Used Isolation Forest to detect unusual weather patterns
Identified extreme or abnormal conditions in the dataset
📈 Feature Importance
Evaluated feature importance using tree-based models
Identified key drivers of weather predictions
🌍 Climate & Geographical Analysis
Analyzed weather patterns across different regions
Studied long-term trends and variability
Compared conditions across locations
🌫 Environmental Impact
Explored relationships between air quality and weather variables
📦 Requirements

Install dependencies with:

pip install -r requirements.txt

Main libraries used:

pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
statsmodels

▶️ How to Run
Clone the repository:
git clone <repo-link>
Open the notebook:
jupyter notebook
Run all cells
📽 Demo

A short demo video explaining the project and results is included here:
👉 (add your link here)

📈 Results & Conclusions
Ensemble models improved prediction performance compared to individual models
Time-based features significantly enhanced forecasting accuracy
Outlier handling and anomaly detection were crucial for robust modeling
Weather patterns vary significantly across regions, highlighting the importance of spatial analysis
🚀 Future Improvements
Incorporate deep learning models (LSTM for time series)
Use external datasets for richer context
Improve spatial analysis with geospatial visualization tools
Perform hyperparameter tuning for all models
📬 Contact

If you have any questions or feedback, feel free to reach out.
