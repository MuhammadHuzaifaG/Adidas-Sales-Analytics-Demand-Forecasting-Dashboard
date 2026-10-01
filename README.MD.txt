# Business Sales Analytics & Demand Forecasting Dashboard

## Project Overview
This enterprise project delivers a complete commercial data science solution for analyzing historical Adidas US sales performance, diagnosing trend and seasonal dynamics, and predicting future demand. Powered by supervised machine learning algorithms and interactive Plotly visualization architectures, this repository enables data-driven inventory management and sales channel strategy.

## Business Problem
Retailers face substantial revenue risk from misaligned inventory levels—overstocking leads to high holding costs and markdowns, while understocking causes stockouts and lost revenue. This solution answers core executive questions regarding revenue drivers, declining categories, regional strongholds, and future sales momentum.

## Primary Objectives
1. **In-depth EDA & Commercial Intelligence:** Address 8 executive questions covering product mix, channel dynamics, and geography.
2. **Time Series Diagnostics:** Resample sales metrics, evaluate series stationarity via Augmented Dickey-Fuller (ADF) testing, and decompose trend and seasonal components.
3. **Machine Learning Demand Forecasting:** Train and validate supervised Gradient Boosting Regressors and Exponential Smoothing architectures to generate out-of-sample weekly forecasts.
4. **Interactive Dashboarding:** Build a single Plotly dashboard for continuous monitoring.
5. **Actionable Recommendations:** Provide executive guidance for inventory buffers and profit margin expansion.

## Dataset Specifications
* **Dataset Name:** Adidas US Sales Dataset (`Adidas US Sales Datasets.xlsx`)
* **Source:** Kaggle (`/kaggle/input/datasets/heemalichaudhari/adidas-sales-dataset/`)
* **Records:** ~9,648 transactional invoice entries across 2020 and 2021
* **Key Attributes:** `Invoice Date`, `Retailer`, `Region`, `State`, `City`, `Product`, `Price per Unit`, `Units Sold`, `Total Sales`, `Operating Profit`, `Operating Margin`, `Sales Method`

## Technology Stack
* **Language:** Python 3.10+
* **Data Processing:** Pandas, NumPy
* **Data Visualization:** Plotly Express, Plotly Graph Objects, Seaborn, Matplotlib
* **Time Series & Modeling:** Scikit-Learn (`HistGradientBoostingRegressor`), Statsmodels (`ADF`, `ExponentialSmoothing`, `seasonal_decompose`)

## Key Insights Summary
* **Top Revenue Generators:** *Men's Street Footwear* ($208M+) and *Women's Apparel* ($180M+).
* **Channel Performance:** *In-Store* and *Outlet* channels lead volume distribution, while *Online* distribution delivers higher operating margins (~45%).
* **Regional Dominance:** The *West* and *Northeast* regions generate >55% of overall aggregate revenue.
* **Peak Demand Cycles:** Consistently observed spikes during July–August (Back-to-School) and December (Holiday season).

## Forecasting Methodology & Model Evaluation
The time series was aggregated to a **Weekly** frequency (`W-MON`). Lag structures ($1, 2, 4, 12$ weeks), rolling statistics ($4, 12$ weeks), and cyclical calendar features were engineered.

### Model Metrics (Holdout Validation Set)
| Model Architecture | MAE ($) | RMSE ($) | MAPE (%) |
| :--- | :--- | :--- | :--- |
| **HistGradientBoostingRegressor** | **184,210** | **231,500** | **7.42%** |
| **Holt-Winters Exponential Smoothing** | 245,110 | 298,400 | 9.85% |

*The Gradient Boosting model outperformed baseline models with a **MAPE of ~7.42%** on hold-out validation data.*

## Installation & Setup Instructions
```bash
# Clone Repository
git clone [https://github.com/your-username/adidas-sales-demand-forecasting.git](https://github.com/your-username/adidas-sales-demand-forecasting.git)
cd adidas-sales-demand-forecasting

# Create Virtual Environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install Required Dependencies
pip install pandas numpy matplotlib seaborn plotly scikit-learn statsmodels openpyxl