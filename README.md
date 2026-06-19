# 🍽️ Time Series Demand Forecasting Using ARIMA, Linear Regression, and XGBoost

## 📌 Project Overview

Demand forecasting is a critical task in supply chain management, inventory optimization, and business decision-making. Accurate demand prediction helps organizations reduce waste, improve resource allocation, and increase operational efficiency.

This project presents a comparative study of statistical and machine learning approaches for time-series demand forecasting. Three forecasting models were implemented and evaluated:

- ARIMA (AutoRegressive Integrated Moving Average)
- Linear Regression
- XGBoost Regressor

The primary objective was to forecast future demand values and identify the most effective forecasting approach based on predictive performance.

---

## 🎯 Objectives

- Analyze historical demand patterns.
- Generate lag-based features from time-series data.
- Build forecasting models using statistical and machine learning techniques.
- Compare forecasting performance using standard evaluation metrics.
- Visualize actual and predicted demand trends.
- Identify the most suitable forecasting model.

---

## 📂 Dataset Description

The dataset contains historical food demand information used for forecasting future orders.

### Features

| Feature | Description |
|----------|-------------|
| id | Unique record identifier |
| week | Week number |
| center_id | Distribution center identifier |
| meal_id | Meal identifier |
| checkout_price | Selling price |
| base_price | Original price |
| emailer_for_promotion | Promotion campaign flag |
| homepage_featured | Homepage feature flag |
| num_orders | Number of orders (Target Variable) |

### Target Variable

```text
num_orders
```

---

## 🔍 Data Exploration

The dataset was inspected and validated before model development.

### Performed Operations

- Dataset loading
- Dataset concatenation
- Dataset merging
- Column inspection
- Shape validation
- Missing value analysis

The training dataset contains historical order information, while the test dataset contains future observations without target values.

---

## 📈 Time-Series Generation

A synthetic time-series was generated to simulate realistic demand behavior containing trend, seasonality, and noise.

### Formula

```python
value = 50 + 0.5*time + sin(time/5)*10 + noise
```

### Characteristics

- Upward Trend
- Seasonal Pattern
- Random Noise

This generated series was used to evaluate forecasting performance under controlled conditions.

---

## ⚙️ Feature Engineering

To transform the time-series problem into a supervised learning task, lag-based features were created.

### Generated Features

```text
lag_1
lag_2
lag_3
```

### Example

| Current Value | Lag 1 | Lag 2 | Lag 3 |
|---------------|-------|-------|-------|
| 85 | 82 | 80 | 78 |

These lag features enable machine learning models to learn temporal dependencies from previous observations.

---

# 🤖 Model 1: ARIMA

ARIMA is a classical statistical forecasting model commonly used for univariate time-series prediction.

### Configuration

```python
ARIMA(order=(3,1,2))
```

### Parameters

- p = 3 (Auto Regression)
- d = 1 (Differencing)
- q = 2 (Moving Average)

The model was trained using historical demand values and evaluated on unseen observations.

---

## 📊 ARIMA Forecasting Results

The following figure shows the forecasting performance of the ARIMA model on the generated time-series data.

<img width="850" height="547" alt="image" src="https://github.com/user-attachments/assets/6d8d6193-0e29-4f7a-a715-f235cd488545" />


### Observation

The model failed to follow the increasing trend observed in the test period. Forecasts became overly smooth and gradually moved downward, resulting in poor forecasting performance.

### Performance

| Metric | Value |
|----------|----------:|
| Train RMSE | 7.4085 |
| Test RMSE | 14.7621 |
| R² Score | -2.3663 |

---

## 🔮 Future Forecasting Using ARIMA

After training, the model was used to predict future demand values for the next 10 time steps.

<img width="850" height="547" alt="image" src="https://github.com/user-attachments/assets/ff6851fb-3995-4a80-9f15-d4462cc11aa3" />


### Observation

The model predicted a gradual decline in future demand despite the presence of an increasing trend in the original series. This indicates an inability to capture the underlying temporal behavior.

---

## 📉 Actual vs Predicted Demand (ARIMA)

To evaluate forecasting accuracy, actual demand values were compared against ARIMA predictions.

<img width="860" height="547" alt="image" src="https://github.com/user-attachments/assets/c02fcaf2-df1c-426f-9a3c-f0f375eb2205" />

### Observation

A significant gap exists between actual and predicted values. The prediction curve remains smooth while actual demand continues to increase, indicating underfitting and poor generalization.

### Error Metrics

| Metric | Value |
|----------|----------:|
| RMSE | 14.7621 |
| MSE | 217.9186 |
| MAE | 11.1725 |
| R² Score | -2.3663 |

---

# 🤖 Model 2: Linear Regression

Linear Regression was trained using lag-based features.

The model learns the relationship between previous observations and future demand values.

### Advantages

- Simple and interpretable
- Fast training
- Effective for linear temporal relationships
- Low computational cost

---

# 🤖 Model 3: XGBoost

XGBoost is an ensemble machine learning algorithm based on gradient boosting decision trees.

### Advantages

- Captures non-linear relationships
- Handles complex patterns
- High predictive capability
- Robust against noise

---

# 📊 Model Comparison

The forecasting performance of all models was compared using RMSE and R² Score.

<img width="850" height="547" alt="image" src="https://github.com/user-attachments/assets/b8dbb078-4937-4abe-8c89-f7baee022ba3" />


### Results

| Model | RMSE | R² Score |
|---------|---------:|---------:|
| ARIMA | 14.7621 | -2.3663 |
| XGBoost | 6.9757 | 0.2483 |
| Linear Regression | **2.6212** | **0.8939** |

---

## 📌 Result Analysis

### ARIMA

- Produced the highest forecasting error.
- Failed to capture the upward trend.
- Generated a negative R² score.
- Demonstrated poor forecasting capability for the generated series.

### XGBoost

- Performed better than ARIMA.
- Captured some demand behavior.
- Struggled to model long-term trends accurately.

### Linear Regression

- Achieved the best performance.
- Lowest RMSE among all models.
- Highest R² score.
- Closely followed actual demand patterns.

---

## 🔑 Key Findings

- Lag-based features significantly improved forecasting accuracy.
- Simple machine learning models can outperform complex statistical models.
- Proper feature engineering had a major impact on predictive performance.
- Linear Regression proved highly effective for short-term demand forecasting.
- Model complexity does not always guarantee better forecasting results.

---

## ⚠️ Limitations

- Forecasting experiments were conducted on synthetic time-series data.
- Hyperparameter tuning was not performed.
- Seasonal ARIMA (SARIMA) was not evaluated.
- Deep learning forecasting models were not explored.

---

## 🚀 Future Improvements

- SARIMA for seasonal forecasting
- Prophet forecasting model
- LSTM-based forecasting
- GRU-based forecasting
- Hyperparameter optimization
- Real-world deployment using FastAPI
- Advanced feature engineering

---

## 🛠️ Technologies Used

### Programming Language

- Python

### Libraries

```text
Pandas
NumPy
Matplotlib
Scikit-Learn
Statsmodels
XGBoost
```

---

## 📁 Project Structure

```text
Time-Series-Demand-Forecasting/
│
├── data/
│   ├── train.csv
│   └── test.csv
│
├── images/
│   ├── arima_forecasting.png
│   ├── arima_future_forecast.png
│   ├── arima_actual_vs_predicted.png
│   └── model_comparison.png
│
├── notebooks/
│   └── Demand_Forecasting.ipynb
│
├── src/
│   └── forecasting.py
│
├── requirements.txt
├── README.md
└── LICENSE
```

---

## 📜 Conclusion

This project conducted a comparative analysis of statistical and machine learning approaches for demand forecasting.

Among all evaluated models, **Linear Regression achieved the strongest performance**, obtaining an RMSE of **2.62** and an R² Score of **0.89**.

The findings demonstrate that properly engineered lag-based features can significantly improve forecasting accuracy and, in some cases, outperform more complex forecasting techniques.

---

## 👨‍💻 Author

**Shuvo Biswas**

AI Engineer & Team Lead

### Areas of Interest

- Machine Learning
- Deep Learning
- Time-Series Forecasting
- NLP & LLM Applications
- RAG Systems
- AI Automation
- FastAPI Development

### Connect

- LinkedIn: [https://linkedin.com/in/your-profile](https://www.linkedin.com/in/shuvo-biswas-a5024b313/)
- GitHub:   [ https://github.com/your-username](https://github.com/Shuvo3128)

⭐ If you found this project useful, consider giving it a star.
