# ⚡ Household Electricity Demand & Price Prediction

A Machine Learning project that predicts **household electricity demand** and estimates the **electricity cost** based on consumption patterns, time-based features, and tariff rules.

The project uses historical household electricity consumption data and applies multiple Machine Learning algorithms to forecast future electricity demand and support better energy management.

---

## 📌 Project Overview

Electricity consumption varies depending on time, day, household activity, and usage patterns.

This project aims to answer:

> **Can Machine Learning predict future household electricity consumption and estimate its electricity cost?**

The system analyzes historical electricity usage and generates predictions that can help households and buildings:

* Monitor electricity consumption
* Identify high-demand periods
* Estimate electricity costs
* Improve energy management
* Support energy conservation
* Plan future electricity demand

---

## 🎯 Objectives

The main objectives of this project are:

1. Predict future household electricity consumption.
2. Analyze electricity usage patterns.
3. Identify peak and off-peak consumption periods.
4. Compare different Machine Learning models.
5. Estimate electricity cost from predicted consumption.
6. Build a simple interactive dashboard for prediction and analysis.

---

## 📊 Dataset

### Dataset Name

**Individual Household Electric Power Consumption**

### Dataset Source

**UCI Machine Learning Repository**

The dataset contains household electricity measurements collected over time.

### Main Features

| Feature               | Description                     |
| --------------------- | ------------------------------- |
| Date                  | Date of electricity measurement |
| Time                  | Time of electricity measurement |
| Global Active Power   | Total active power consumed     |
| Global Reactive Power | Reactive power measurement      |
| Voltage               | Voltage level                   |
| Global Intensity      | Current intensity               |
| Sub Metering 1        | Energy sub-metering             |
| Sub Metering 2        | Energy sub-metering             |
| Sub Metering 3        | Energy sub-metering             |

---

## 🧹 Data Preprocessing

The dataset is processed before applying Machine Learning.

### Preprocessing Steps

```text
Raw Dataset
     ↓
Data Loading
     ↓
Column Cleaning
     ↓
Missing Value Handling
     ↓
Duplicate Checking
     ↓
Date & Time Conversion
     ↓
Data Type Conversion
     ↓
Outlier Analysis
     ↓
Feature Engineering
     ↓
Model Ready Dataset
```

### Data Cleaning

The following operations are performed:

* Handling missing values
* Converting numerical columns
* Combining Date and Time
* Sorting records chronologically
* Removing unnecessary columns
* Interpolating missing time-series values
* Checking duplicate records

---

## ⚙️ Feature Engineering

Additional features are created from the original electricity consumption data.

### Generated Features

* Hour
* Day
* Month
* Weekday
* Weekend indicator
* Peak-hour indicator
* Lag consumption
* Rolling average

Example:

```python
df["hour"] = df.index.hour
df["day"] = df.index.day
df["month"] = df.index.month
df["weekday"] = df.index.weekday
df["is_weekend"] = (df["weekday"] >= 5).astype(int)
```

Lag and rolling features are used to capture previous consumption behavior and recent electricity usage trends.

---

## 🤖 Machine Learning Models

The project compares multiple Machine Learning algorithms.

### 1. Linear Regression

Used as a simple baseline model for predicting electricity demand.

### 2. Random Forest

An ensemble learning algorithm that can capture nonlinear relationships between electricity consumption and the input features.

### 3. XGBoost

A gradient boosting algorithm used for high-performance regression and nonlinear prediction.

### 4. LSTM

Long Short-Term Memory is a deep learning model designed for sequential and time-series data.

```text
Historical Electricity Data
          ↓
   Feature Engineering
          ↓
     Train / Test Split
          ↓
 ┌────────┼─────────┐
 ↓        ↓         ↓
Linear   Random   XGBoost
Regression Forest
          ↓
        LSTM
          ↓
 Model Comparison
          ↓
 Best Model
          ↓
 Electricity Prediction
```

---

## 📈 Model Evaluation

The models are evaluated using the following metrics:

### MAE — Mean Absolute Error

Measures the average absolute difference between actual and predicted values.

### RMSE — Root Mean Squared Error

Measures prediction error while giving more weight to larger errors.

### MAPE — Mean Absolute Percentage Error

Measures prediction error as a percentage.

### R² Score

Measures how well the model explains the variation in electricity consumption.

### Evaluation Metrics

| Metric | Purpose                  |
| ------ | ------------------------ |
| MAE    | Average prediction error |
| RMSE   | Penalizes large errors   |
| MAPE   | Percentage-based error   |
| R²     | Goodness of fit          |

The model with the best performance is selected for deployment.

---

## 💰 Electricity Price Prediction

In addition to electricity demand prediction, the project estimates the **electricity cost** based on predicted energy consumption.

The general calculation is:

```text
Energy Consumption (kWh)
            ×
       Tariff Rate
            +
     Standing Charge
            =
    Estimated Electricity Cost
```

The application can distinguish between:

* Peak hours
* Off-peak hours
* Weekend usage

> **Note:** The tariff values used in the application are example/demo rates. They should be replaced with the actual electricity tariff applicable to the deployment location.

---

## 🖥️ Deployment

The trained Machine Learning model is deployed using **Gradio**.

The dashboard allows users to enter electricity-related information and receive:

* Predicted electricity demand
* Estimated energy consumption
* Estimated electricity cost
* Peak/off-peak information
* Energy management insights

### Deployment Flow

```text
User Input
    ↓
Feature Processing
    ↓
Trained ML Model
    ↓
Demand Prediction
    ↓
Energy Consumption
    ↓
Tariff Calculation
    ↓
Cost Estimation
    ↓
Dashboard Result
```

---

## 📁 Project Structure

```text
Household-Electricity-Demand-Price-Prediction/
│
├── app/
│   └── app.py
│
├── data/
│   └── README.md
│
├── models/
│   └── README.md
│
├── notebooks/
│   └── README.md
│
├── outputs/
│   └── README.md
│
├── src/
│   ├── train.py
│   └── README.md
│
├── .gitignore
├── LICENSE
├── project_manifest.json
├── requirements.txt
└── README.md
```

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Scikit-learn
* XGBoost
* TensorFlow / Keras
* Matplotlib
* Gradio
* Joblib

### Machine Learning

* Linear Regression
* Random Forest Regressor
* XGBoost Regressor
* LSTM

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Household-Electricity-Demand-Price-Prediction.git
```

### 2. Open the Project

```bash
cd Household-Electricity-Demand-Price-Prediction
```

### 3. Create a Virtual Environment

```bash
python -m venv venv
```

### 4. Activate the Environment

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / macOS

```bash
source venv/bin/activate
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 📥 Dataset Setup

Place the electricity dataset inside the `data/` folder.

Expected file:

```text
data/household_electricity_consumption_100k.csv
```

Large datasets are intentionally excluded from GitHub using `.gitignore`.

---

## 🏋️ Train the Model

Run:

```bash
python src/train.py
```

The training process will:

1. Load the dataset
2. Clean the data
3. Perform feature engineering
4. Split the data
5. Scale the features
6. Train Machine Learning models
7. Evaluate the models
8. Compare model performance
9. Save the trained model

---

## 🌐 Run the Gradio Application

After training the model:

```bash
python app/app.py
```

The Gradio application will start locally.

Open the local Gradio URL shown in the terminal.

---

## 📊 Expected Output

The application provides:

```text
┌─────────────────────────────────────┐
│   Household Electricity Dashboard   │
├─────────────────────────────────────┤
│                                     │
│  Input Electricity Information      │
│              ↓                      │
│      ML Demand Prediction           │
│              ↓                      │
│     Energy Consumption              │
│              ↓                      │
│      Electricity Cost               │
│                                     │
└─────────────────────────────────────┘
```

---

## 🌱 Real-World Impact

This project can support:

* **Energy conservation**
* **Household energy management**
* **Demand planning**
* **Peak-hour awareness**
* **Electricity cost estimation**
* **Smart energy dashboards**

In a larger deployment, the system could be integrated with smart meters or IoT-based energy monitoring systems.

---

## ⚠️ Limitations

Current limitations include:

* Prediction quality depends on the available historical data.
* Household electricity behavior can change unexpectedly.
* External factors such as weather are not included.
* Actual electricity tariffs vary by location and provider.
* LSTM requires additional computational resources.
* Predictions should not be considered exact electricity bills.

---

## 🔮 Future Improvements

Possible future improvements include:

* Integrating real-time smart-meter data
* Adding weather information
* Adding temperature and humidity features
* Using advanced LSTM/GRU architectures
* Developing a real-time monitoring dashboard
* Adding electricity tariff APIs
* Supporting multiple households
* Cloud deployment
* IoT integration
* Automated energy-saving recommendations

---

## 🔐 Data & Model Files

Large datasets and trained model files are not included in the Git repository by default.

This keeps the repository lightweight and easier to clone.

The required files can be generated/downloaded separately and placed in:

```text
data/
models/
```

---

## 👨‍💻 Author

**Abhin Krishna**

Data Science / B1
Trycod Tech School

### Mentor

**Faizal**

---

## 📜 License

This project is licensed under the MIT License.

See the `LICENSE` file for more information.

---

## ⭐ Project Summary

**Household Electricity Demand & Price Prediction** combines time-series feature engineering, Machine Learning, and an interactive Gradio dashboard to predict electricity demand and estimate electricity costs.

```text
Historical Data
      ↓
Data Cleaning
      ↓
Feature Engineering
      ↓
Machine Learning
      ↓
Demand Prediction
      ↓
Cost Estimation
      ↓
Interactive Dashboard
```

**⚡ Predict energy. Understand usage. Estimate cost. Manage better.**
