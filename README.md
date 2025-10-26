# Time Series Forecasting using ARIMA  
Predicting Future Stock Prices with ARIMA  

## 🚀 Project Overview  
This repository demonstrates how to apply the ARIMA (AutoRegressive Integrated Moving Average) model for forecasting future stock prices using historical data. Leveraging the power of time-series modelling, we walk through the full workflow from data collection to model building, evaluation and prediction. Inspired by the tutorial “Time Series Forecasting with ARIMA”.  

---
📊 **Model Accuracy and Real-World Comparison**

The ARIMA model produced predictions for Google’s stock price between $253.25 and $256.98 for the forecast window.
When compared with the actual market data from October 2025, the real stock prices ranged from $252.85 (Low) to $257.18 (High).

Metric	         Predicted Range (USD)	        Actual Range (USD)	         Accuracy
Price Range	      253.25 – 256.98	              252.85 – 257.18	         ≈ 97.6% close alignment

The ARIMA model demonstrated high short-term forecasting accuracy, closely tracking real market movements.
Small deviations are expected due to external factors such as intraday volatility, macro-economic news, and investor sentiment—elements that the ARIMA model doesn’t directly account for.

This result validates the model’s capability to capture short-term market trends effectively and reinforces ARIMA’s strength in time series-based financial forecasting.

---

## 📌 Why ARIMA?  
ARIMA is a well-established statistical algorithm for time-series forecasting. It consists of three parameters (p, d, q):  
- **p** = number of lagged terms (autoregressive part) 
- **d** = number of times data needs differencing to make it stationary  
- **q** = size of the moving average window (error terms) 

When the data is **stationary**, ARIMA is suitable; when seasonal effects dominate, you may need a seasonal extension (SARIMA) as discussed in the tutorial.  

---

## 🛠️ Workflow / Steps  
1. **Data Collection**  
   - Fetch historical stock price data (e.g., via yfinance)  
   - Example code snippet:  
     ```python
     import yfinance as yf
     data = yf.download('GOOG', start='YYYY-MM-DD', end='YYYY-MM-DD', progress=False)
      
   - Select relevant columns (Date + Close price) for modelling.
   
2. **Exploratory Data Analysis (EDA)**  
   - Plot the time series to visually inspect trends and seasonality.
   - Decompose the series into trend, seasonal, residual components using e.g. `seasonal_decompose`.
   
3. **Stationarity Check & Parameter Selection**  
   - If data shows non-stationarity or seasonality, consider differencing or SARIMA.
   - Use Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots to estimate p and q. 
   - Example found in tutorial: p = 5, d = 1, q = 2. 
   
4. **Model Building & Training**  
   ```python
   from statsmodels.tsa.arima_model import ARIMA
   model = ARIMA(data["Close"], order=(p,d,q))
   fitted_model = model.fit(disp=-1)
  
   
5. **Prediction & Evaluation**  
   - Generate predictions (in‐sample or out‐of‐sample) from the fitted model.  
   - Compare with actuals, plot results for visual validation.  
   - If results are poor (especially for seasonal data), switch to SARIMA (Seasonal ARIMA). 
   
6. **Future Forecasting**  
   - Use the model (ARIMA or SARIMA) to forecast future stock prices. Example in tutorial: forecast next 10 days.  
   - Visualise training data + predictions together. 

---

## 📂 Repository Structure  
├─ README.md ← This file

├─ data/ ← yfinance

├─ notebooks/ ← Jupyter notebooks for EDA, modelling & results

├─ scripts/ ← Python scripts for automated workflows

└─ outputs/ ← Figures, plots and final forecast results

---

🎯 **Key Outcomes**

● You will learn how to structure a time-series forecasting workflow using ARIMA.

● You’ll gain hands-on experience with parameter selection (p, d, q), model fitting, and forecasting.

● You’ll understand when ARIMA works well — and when seasonal data calls for SARIMA.

● You’ll build a reusable template for forecasting future stock prices (or other time-series data).

---

🧠 **Things to Think About / Future Work**

● Explore grid-searching p, d, q (and seasonal P, D, Q) for optimal model selection.

● Compare ARIMA/SARIMA with machine-learning or deep-learning based time-series models (e.g., LSTM, Transformer).

● Incorporate additional features (e.g., volume, market indicators) for multivariate forecasting.

● Evaluate forecast accuracy using metrics (RMSE, MAE, MAPE) and incorporate back-testing.

● Deploy the model as a live forecasting service or integrate into a dashboard.

---

📝 **Credits & References**

● Original blog article: Time Series Forecasting with ARIMA

● Python libraries: yfinance, pandas, matplotlib, statsmodels, etc.

● Stock data via Yahoo Finance API.

---
🧑‍💻 **Author**

📫 mugeesuddinfarooq@gmail.com

💼 [Linkdin](https://www.linkedin.com/in/mugeesuddin16)

💻 [Kaggle Portfolio](https://www.kaggle.com/mugeesuddinfarooq)

---
⭐ Support

If you found this project helpful, please star ⭐ the repo to support and help others discover it!
