# volatility-forecasting

Volatility forecasting is important for risk management, VaR, and portfolio allocation. This project implements hybrid CNN-LSTM and LSTM deep learning models, alongside a traditional GARCH(1,1) model, to forecast 5-day realized volatility using historical daily price data spanning approximately 40 years.  
The deep learning models are evaluated using a 60/20/20 train–test–out-of-sample split, with a strong focus on generalization and out-of-sample forecasting performance. For comparability, the GARCH(1,1) model is trained on the 60% training portion, and forecasting is conducted using a sliding window approach.  
All model pipelines are fully modular and include data preprocessing, training, evaluation, and forecasting components. While the deep learning models are not necessarily intended to outperform traditional models like GARCH on a basic dataset, this project demonstrates how deep learning can be applied to financial time series in a structured, reproducible way. Incorporating richer or higher-frequency features may significantly enhance the forecasting accuracy of the deep learning models.

## Results Summary

The models were trained to forecast 5-day realized volatility using historical daily price data over a 40-year period.  
Evaluation was conducted on the final 20% of the data (out-of-sample), simulating a real-world forecasting scenario.

### CNN-LSTM Performance (7 reruns):
- **MAE**: 0.00695 ± 0.00053  
- **RMSE**: 0.00881 ± 0.00041  
- **MSE**:  0.0000809 ± 0.0000084

The best (reproducible) run achieved:
- **MAE**: 0.00643  
- **RMSE**: 0.00868
- **MSE**: 0.000075

### LSTM Performance (7 reruns):
- **MAE**:   
- **RMSE**:  
- **MSE**: 

The best (reproducible) run achieved:
- **MAE**:   
- **RMSE**: 
- **MSE**:
- 
## GARCH(1,1) Performance:
- **MAE**:   
- **RMSE**:   
- **MSE**:  

### Interpretation:
While GARCH remains a strong baseline for volatility modeling with daily data, the CNN-LSTM model demonstrated competitive performance and stability across multiple training runs.  
This reinforces that deep learning can be a viable alternative for volatility forecasting — especially when richer features or higher-frequency data are introduced.


