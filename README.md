# 📊 Time Series Analysis: Depression Index & Market Volatility

> **Behavioral Signals & Financial Markets (2017–2024)**  
> Investigating how human emotional states relate to market volatility across industries

---

## ⚡ TL;DR
- Analyzed **600K+ multi-source time-series records**
- Found **statistically significant correlations (p < 0.001)** between depression index and market volatility  
- Identified **lag effects (1–3 days)** where sentiment precedes volatility  
- Observed **industry-level variation** in sensitivity to behavioral signals  
- Built an interactive Flask dashboard for exploration  

---

## 🧠 Problem

Traditional financial models rely heavily on price-based indicators.

However, behavioral finance suggests that **human emotion and sentiment** may influence market dynamics.

This project investigates:

> **Does a depression index (derived from public signals) influence market volatility?**  
> **Do these effects vary across industries?**

---

## 📦 Data

- Depression index (news + Google Trends)  
- S&P 500 market data  
- 498 stocks across 12 industries  
- External signals (weather, trends)  

👉 Final dataset:
- **551 daily observations (2017–2024)**  
- **17+ engineered time-series features**

---

## 🧪 Time Series Analysis

### Feature Engineering
- Lag features (t-1, t-2, t-3)  
- Rolling statistics (volatility, mean)  
- Sentiment momentum indicators  

---

### Statistical Results

| Metric | Correlation | Significance |
|--------|------------|-------------|
| Market Volatility | **0.275** | **p < 0.001** |
| S&P 500 Volatility | **0.267** | **p < 0.001** |
| Trading Volume | 0.211 | p < 0.001 |
| Price Level | 0.144 | p < 0.001 |
| Weather Impact | ~0.04 | Not significant |

👉 **Key Insight:**  
Depression signals correlate more strongly with **market volatility (uncertainty)** than price levels.

---

### Lag Effect Analysis

- Strongest relationships observed at **1–3 day lag**
- Suggests sentiment signals may **precede volatility changes**

---

### Industry-Level Analysis

Observed variation in correlation strength across industries, suggesting differing sensitivity to behavioral signals.

**More Sensitive Industries**
- Leisure products  
- Publishing  
- Restaurants / consumer-facing sectors  

**Less Sensitive or Negative Response**
- Copper  
- Cargo ground transportation  
- Homebuilding / infrastructure-heavy sectors  

👉 Interpretation: consumer-facing and discretionary sectors appear more sensitive to emotional signals than capital-intensive or infrastructure-heavy sectors.

---

## 📈 Key Insights

- Emotional signals show **statistically significant relationships with volatility**  
- Market behavior reflects **uncertainty more than direction**  
- Behavioral effects vary across industries  
- Consumer-facing sectors appear more sensitive than infrastructure-heavy sectors  
- Weather variables were not significant in the current setup, likely due to geographic mismatch between localized weather data and broader market signals  

---

## 📊 Interactive Dashboard

A Flask-based dashboard enables exploration of results:

- Time-series visualization  
- Industry comparison  
- Lag-based volatility analysis  
- Statistical summaries  

🎥 Demo: https://youtu.be/dxp3GlqZcoo  

---

## 🛠️ Tech Stack

- Python (pandas, NumPy, SciPy)  
- Flask  
- Plotly  
- PostgreSQL  

---

## 📁 Project Structure

```bash
.
├── src/                  # Data processing & analysis
├── flask/                # Interactive dashboard
├── data/                 # Processed datasets
├── reports/              # Analysis outputs
├── config/               # SQL schemas & queries
├── docs/                 # Documentation
└── README.md
```

👉 Organized to separate data processing, analysis, and visualization for clarity and scalability.

---

## 🔧 Data Pipeline (Supporting)

- Multi-source ingestion  
- Data cleaning & normalization  
- Feature engineering  
- PostgreSQL storage  

👉 Focus: **analysis over infrastructure**

---

## 🔮 Future Work

- Extend predictive modeling (XGBoost, ARIMA) for volatility forecasting  
- Incorporate real-time sentiment data pipelines  
- Apply causal inference techniques (e.g., Granger causality)  
- Conduct formal statistical testing across industries (e.g., ANOVA, regression with interaction terms) to validate whether observed differences are statistically significant  
- Incorporate region-specific trading data alongside localized weather signals to evaluate potential environmental effects on market behavior  

---

## 📌 Takeaway

This project demonstrates:

- Time-series analysis with real-world data  
- Statistical validation (correlation, p-values)  
- Behavioral finance insights  
- End-to-end analytical workflow  
- Interactive data storytelling  
