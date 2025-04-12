# Volatility-Forecasting

Volatility forecasting is important for risk management, Value-at-Risk (VaR), and portfolio allocation.  
This project implements hybrid CNN-LSTM and LSTM deep learning models, alongside a traditional GARCH(1,1) model, to forecast 5-day realized volatility using historical daily **Apple (AAPL)** stock price data spanning approximately 40 years.

The deep learning models are evaluated using a 60/20/20 train–test–out-of-sample split, with a strong focus on generalization and out-of-sample forecasting performance. For comparability, the GARCH(1,1) model is trained on the 60% training portion, and forecasting is conducted using a sliding window approach.

All model pipelines are fully modular and include data preprocessing, training, evaluation, and forecasting components.  
While the deep learning models may not necessarily outperform traditional models like GARCH on a basic dataset, this project demonstrates how deep learning can be applied to financial time series in a structured, reproducible way. Incorporating richer or higher-frequency features may significantly enhance the forecasting accuracy of the deep learning models.

## Results Summary

The models were trained to forecast 5-day realized volatility using historical daily price data over a 40-year period.  
Evaluation was conducted on the final 20% of the data (out-of-sample), simulating a real-world forecasting scenario.

The deep learning models also use bidirectional LSTM layers to better capture past and future dependencies in the time series:
- The **LSTM model** uses a single Bidirectional LSTM layer  
- The **CNN-LSTM model** uses two stacked Bidirectional LSTM layers after the convolutional layer

### CNN-LSTM Performance (Average over 7 Reruns):
- **MAE**: 0.006953 ± 0.00056  
- **RMSE**: 0.00895 ± 0.00041 
- **MSE**:  0.0000803 ± 0.0000081

**The best (reproducible) run achieved:**
- **MAE**: 0.00643  
- **RMSE**: 0.00868
- **MSE**: 0.000075

### LSTM Performance (Average over 7 Reruns):
- **MAE**: 0.006957 ± 0.000498   
- **RMSE**: 0.008968 ± 0.000356  
- **MSE**: 0.0000804 ± 0.0000067 

**The best (reproducible) run achieved:**
- **MAE**: 0.006367   
- **RMSE**: 0.008622 
- **MSE**: 0.000074
  
### GARCH(1,1) Performance:
- **MAE**: 0.006928   
- **RMSE**: 0.000075   
- **MSE**: 0.008639  

## Interpretation:
While GARCH remains a strong baseline for volatility modeling using daily data, the deep learning models demonstrated **competitive and stable** performance across multiple training runs.  
This highlights that deep learning can be a viable tool for volatility forecasting — especially when richer features and higher-frequency data are introduced.

## Feature Engineering

The models are trained using multivariate inputs, with features engineered to capture price action, volatility dynamics, and technical indicators. Each input sequence includes the following:
- **Log return** and its **lags** (1-day, 2-day)
- **Squared returns** and **z-scored returns** (to capture volatility intensity)
- **Price shock** for detecting large return spikes
- **Relative Strength Index (RSI)** for momentum signals
- **Log volume change** and **log high-low range**
- **Rolling volatility** over 5, 7, and 21 days
- The target variable is the **5-day forward realized volatility**
