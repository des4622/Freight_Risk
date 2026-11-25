# 🚢 Freight Rate Risk & Liquidity Stress-Test Dashboard

## 🎯 Business Objective
Supply chain volatility directly impacts corporate liquidity. This project builds an end-to-end risk analytics engine that monitors freight rate volatility (SCFI/BDI) and quantifies its downstream impact on working capital and liquidity runways. It directly addresses the need to oversee freight rate shifts, BAF surcharges, and financial KRIs (liquidity caps, DSO) in a volatile macro environment.

## 📊 Key Features & Methodology
1. **Data Pipeline & Synthetic Generation:** Integrates real Baltic Dry Index (BDI) data via `yfinance`. Uses an **Ornstein-Uhlenbeck (mean-reverting) stochastic process** to generate highly realistic synthetic SCFI and commercial "Buy vs. Sell" spread data, mimicking actual market equilibrium and volatility regimes.
2. **Risk Metrics Engine:** Calculates 30-day rolling annualized volatility and Z-scores to flag statistically abnormal rate spikes against corporate risk appetite limits.
3. **Liquidity Stress-Test Model:** Translates market shocks into financial KRI impacts. Models a mid-sized logistics entity's cash burn under 0%, 10%, and 30% freight cost shocks.
4. **The DSO Multiplier:** Introduces a "Compound Crisis" scenario, modeling how a 15-day deterioration in Days Sales Outstanding (DSO) traps working capital and accelerates liquidity depletion.
5. **Executive Dashboard:** Interactive Plotly visualizations for Board-level risk monitoring.

## 💡 Key Business Insights
- **Volatility Thresholds:** The model flags periods where SCFI volatility exceeds the 50% annualized risk appetite limit, triggering a review of spot-market exposure.
- **The Liquidity Cliff:** A 30% freight shock alone is manageable for a profitable firm. However, when combined with a 15-day DSO deterioration (delayed client payments), cash trapped in Accounts Receivable reduces the effective liquidity buffer by 42%, dropping the company's cash runway into the **CRITICAL zone (< 3 months)**.
- **Conclusion:** Monitoring freight rates in isolation is insufficient. Risk management must integrate market volatility with working capital metrics (DSO) to prevent liquidity crises.

## 🛠️ Tech Stack
- **Python**, `pandas`, `numpy` (Data manipulation & stochastic modeling)
- `yfinance` (Real-world index data extraction)
- `plotly` (Interactive executive risk dashboard)

## 🚀 How to Run
1. Clone this repository.
2. Install dependencies: `pip install pandas numpy yfinance plotly`
3. Run the notebooks in order:
   - `01_Data_Acquisition.ipynb` (Generates `freight_data.csv`)
   - `02_Stress_Test_Engine.ipynb` (Generates `stress_test_results.csv`)
   - `03_Dashboard.ipynb` (Generates interactive Plotly charts)
4. See `Freight_Risk_Project.pptx` for a visual overview of the risk insights.
