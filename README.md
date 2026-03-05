# SARIMA Forecasting — San Francisco Airport Passenger Traffic

This project was part of the Time Series & Forecasting Class at FCUP Porto.

Analysis and forecasting of monthly passenger traffic at San Francisco 
International Airport from 1999 to 2020. The project covers the full 
time series modelling workflow: exploratory analysis, stationarity 
transformation, SARIMA model identification and selection, and 
comparative evaluation of forecasting approaches.

Accurate passenger volume forecasting is essential for operational 
planning, resource allocation, and decision-making in the aviation 
sector — making this a practically motivated forecasting problem with 
a rich, real-world dataset.

## Dataset

Monthly passenger traffic at San Francisco International Airport, 
1999–2020. The dataset exhibits strong seasonality and an upward 
trend, interrupted by the COVID-19 pandemic in 2020.

## Project structure

### 1 — Exploratory data analysis
- Visualisation of the raw time series
- Identification of trend, seasonality, and structural breaks
- Autocorrelation Function (ACF) and Partial Autocorrelation Function 
  (PACF) analysis

### 2 — Stationarity transformation
- Box-Cox transformation to stabilise variance
- Seasonal differencing (lag 12) to remove seasonal component
- First-order differencing to remove trend
- Verification of stationarity after transformation

### 3 — SARIMA model identification & selection
Three candidate models identified and evaluated:

| Model | Selection method |
|-------|-----------------|
| SARIMA(0,1,0)×(3,1,1)₁₂ | Manual — residual diagnostics & coefficient analysis |
| SARIMA(0,1,1)×(3,1,1)₁₂ | Manual — residual diagnostics & coefficient analysis |
| SARIMA(0,1,1)×(2,0,2)₁₂ | Automated — lowest AIC |

Model evaluation based on:
- Residual diagnostics
- Autocorrelation Function of residuals
- Information Criteria (AIC)

### 4 — Forecasting & comparative evaluation
Three forecasting schemes compared across all candidate models:
- **Fixed scheme** — model estimated once on training data
- **Recursive scheme** — model re-estimated as each new observation 
  is added
- **Rolling window scheme** — model estimated on a fixed-size moving 
  window

## Key findings

- Strong seasonality and upward trend confirmed in EDA; SARIMA 
  methodology validated as appropriate
- SARIMA(0,1,0)×(3,1,1)₁₂ produced the best forecast under the 
  fixed scheme
- Recursive and rolling window schemes showed lower accuracy
- Relative RMSE ranged from 2.4% to 3.2% across models — strong 
  performance under normal conditions
- All actual values fell within 95% confidence intervals across all 
  models
- Residuals showed significant autocorrelation at lag 12 across all 
  models, suggesting remaining seasonal structure
- COVID-19 caused a complete structural break in 2020, making that 
  period impossible to model accurately — a fundamental limitation 
  of any SARIMA approach under unexpected disruption events

## Repository structure

| File | Contents |
|------|----------|
| `Group06_final report.pdf` | Report including full analysis: EDA, transformation, model selection, forecasting |
| `Group06_Notebook.ipynb` | Notebook for the full analysis |
| `Air_Traffic_Passenger_Statistics_20241115.csv` | Data |
