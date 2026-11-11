# Spain Energy Market Analytics

A data science and machine learning portfolio project analyzing the dynamics of the Spanish wholesale electricity market. This project focuses on the economic impact of renewable energy penetration (Merit Order Effect), market regime identification, and predictive price modeling.

## Tech Stack
* **Language:** Python 3.10+
* **Data Processing:** Pandas, NumPy, SQLite
* **Machine Learning:** Scikit-Learn (K-Means, Random Forest)
* **Statistical Analysis:** Statsmodels, SciPy
* **Data Visualization:** Matplotlib, Seaborn

## Project Structure

### 1. Statistical Analysis (`01_merit_order_effect.ipynb`)
Investigates the "Merit Order Effect" and price cannibalization caused by renewable energy sources.
* **Methods:** Pearson correlation, Ordinary Least Squares (OLS) regression.
* **Findings:** Confirmed a strong inverse correlation (-0.78) between renewable share and market price. The model explains 60.3% of price variance with an RMSE of 51.10 €/MWh.

### 2. Unsupervised Learning (`02_daily_clustering.ipynb`)
Identifies underlying market regimes by clustering 24-hour renewable generation profiles.
* **Methods:** Time-series normalization, K-Means clustering.
* **Regimes Identified:** 
  * *High Solar (Maximum Peak):* Drives midday prices near zero but suffers from steep evening ramps.
  * *High Wind (Strong Baseline):* Consistent 24/7 generation that depresses the overall base price.
  * *Low Renewable Output:* High reliance on fossil fuels, resulting in extreme price spikes and volatility.

### 3. Predictive Modeling (`03_price_forecasting.ipynb`)
Forecasts hourly clearing prices based exclusively on weather generation and temporal seasonality.
* **Methods:** Chronological splitting, Random Forest Regressor, Feature Importance analysis.
* **Performance:** Achieved an R² of 0.650 and a MAE of 40.39 €/MWh. Implemented WAPE (23.69%) to robustly handle the mathematical anomaly of 0 €/MWh clearing prices. 
* **Key Drivers:** Solar generation is the dominant predictive feature, heavily outweighing wind generation and daily demand cycles.

## How to Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/felixkiefer3/spain-energy-market-analytics.git
   cd spain-energy-analytics
   ```
2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run Jupyter Notebook to explore the analysis:
   ```bash
   jupyter notebook
   ```