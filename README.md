# Sales Forecasting (in progress)

Forecasting daily store sales using naive and seasonal-naive baselines, ETS and SARIMA, evaluated with a time-based backtest (WAPE, bias, MASE). Built in Python with pandas, statsmodels.

Data: Kaggle "Store Item Demand Forecasting Challenge" (train.csv, not included; download it from Kaggle and place it next to the notebook).

## Findings
- Daily sales show an upward trend, a strong weekly pattern (Sunday highest, Monday lowest) and a strong yearly cycle (peak in July, low in January).
- Differencing (d=1, D=1, period 7) makes the series stationary (ADF p = 0.0000 after differencing).
- ACF and PACF suggest SARIMA(0,1,1)(0,1,1,7) as a starting point.
- Naive and seasonal-naive baselines both over-forecast by about 20% on the December holdout, because sales fall from late November while the baselines keep the earlier level. They serve as benchmarks for the models.
- On a single 28-day December holdout, ETS reached a WAPE of 5.7%, against about 20% for the naive and seasonal-naive baselines.
- Limitation: the models use a 7-day period, so the yearly cycle is not modelled. Results will be confirmed with a rolling backtest.
