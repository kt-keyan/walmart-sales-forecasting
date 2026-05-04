# 🛒 Walmart Weekly Sales Forecasting using SARIMAX

A store-level weekly sales forecasting project built on the Walmart Retail Dataset. Uses SARIMAX time series modelling to forecast 12 weeks of future sales, with full EDA, seasonal decomposition, and two forecast evaluation modes.

---

## Problem Statement

Predict weekly sales for individual Walmart stores using historical data and external factors (CPI, unemployment, temperature, fuel price) to support inventory planning and business decisions.

---

## Dataset

- **File**: `Walmart.csv`
- **Records**: 6,435 weekly entries across 45 stores
- **Features**: Store, Date, Weekly_Sales, Holiday_Flag, Temperature, Fuel_Price, CPI, Unemployment

---

## Workflow

### 1. Data Loading & EDA
- Loaded dataset with 6,435 records across 45 stores
- Identified top and bottom performing stores by average weekly sales
- Measured holiday vs non-holiday sales premium
- Analysed correlation between CPI, unemployment, temperature, fuel price and weekly sales

### 2. Store Selection & Aggregation
- Filtered data for any selected store (1–45)
- Aggregated weekly sales by date for time series analysis

### 3. Seasonal Decomposition
- Decomposed sales into Trend, Seasonality, and Residuals (additive model, period=12)
- Confirmed clear seasonal patterns in weekly sales

### 4. Store Comparison (2012)
- Compared selected store against Store 5 for the 2012 calendar year
- Visualised sales divergence and shared seasonal behaviour

### 5. SARIMAX Model Training
- Fitted SARIMAX(4,4,3)(1,1,0,52) — 52-week seasonal period to capture yearly cycles
- Reviewed model summary and diagnostic plots (residual normality, autocorrelation)

### 6. One-Step Ahead Forecast
- Forecast from 2012-07-27 using actual observed values at each step
- Evaluated using **MSE**

### 7. Dynamic Forecast
- Forecast from same start date using model's own predictions (no actual data used)
- More realistic simulation of real future forecasting
- Evaluated using **RMSE** and total absolute residual

### 8. 12-Week Ahead Forecast
- Forecast 12 weeks beyond the last data point with 95% confidence intervals
- Printed week-by-week predicted sales with upper and lower bounds

---

## Output

- Top/bottom store performance ranked and visualised
- Holiday sales premium quantified
- External factor correlations plotted for all four features
- Seasonal decomposition showing trend and yearly cycle
- One-step ahead and dynamic forecasts compared against actual values
- 12-week forward forecast with confidence intervals

---

## Model Evaluation

| Metric | Mode | Description |
|--------|------|-------------|
| MSE | One-step ahead | Uses actual values at each step — lower error |
| RMSE | Dynamic | Uses predicted values forward — realistic future simulation |

---

## Key Learnings

- External factors like CPI and unemployment influence weekly sales but vary by store
- Holiday weeks consistently drive higher sales — seasonal models must account for this
- One-step ahead forecasting is more accurate; dynamic forecasting is more realistic
- Confidence intervals widen over the forecast horizon — uncertainty grows with time

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas | Data loading, aggregation, date indexing |
| statsmodels | Seasonal decomposition & SARIMAX |
| NumPy | Error metric computation |
| Matplotlib | All visualisations |

---

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/kt-keyan/walmart-sales-forecasting.git
cd walmart-sales-forecasting

# 2. Install dependencies
pip install pandas numpy matplotlib statsmodels

# 3. Place Walmart.csv in the project folder

# 4. Run the notebook
jupyter notebook walmart_sales_forecasting.ipynb
```

---

## Project Structure

```
walmart-sales-forecasting/
│
├── walmart_sales_forecasting.ipynb   # Main forecasting notebook
├── Walmart.csv                       # Dataset
├── store_performance.png             # Top/bottom store chart
├── factor_correlations.png           # EDA correlation plots
├── seasonal_decomposition.png        # Decomposition plot
├── store_comparison_2012.png         # Store vs Store 2012
├── one_step_forecast.png             # One-step ahead forecast
├── dynamic_forecast.png              # Dynamic forecast
├── 12week_forecast.png               # Final 12-week forecast
└── README.md
```

---

## Author

**Karthikeyan K**
B.Tech — AI & Data Science, Annai Mira College of Engineering and Technology
📧 karthikeyank00118@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/karthi-keyan-3b44a32a8/) | [GitHub](https://github.com/kt-keyan)
