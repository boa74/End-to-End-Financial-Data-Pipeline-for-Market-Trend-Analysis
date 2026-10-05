# 📊 End-to-End Financial Data Pipeline & Market Trend Analytics

> **An end-to-end analytics project integrating 600K+ financial and behavioral records to identify statistically robust relationships with market volatility.**

**Python · SQL · PostgreSQL · Flask · Plotly**

---

## 🎯 Project at a Glance

| 📦 Data Scale | 🏢 Market Coverage | 🧪 Statistical Tests | ✅ Robust Findings |
|:---:|:---:|:---:|:---:|
| **600K+ records** | **498 companies** | **17 relationships** | **3 significant** |
| 4 external data sources | 127 industries | Bonferroni controlled | after correction |

| 🗄️ Data Platform | 📊 Visualization | ⚙️ Analytics Workflow | 📈 Strongest Signal |
|:---:|:---:|:---:|:---:|
| **PostgreSQL** | **Flask + Plotly** | **Python + SQL** | **r = 0.275** |
| Integrated data store | Interactive dashboard | End-to-end pipeline | Depression Index ↔ Volatility |

![Executive summary dashboard](images/project_summary.png)

---

## 💡 Key Finding

The strongest and most robust relationship was between the
**Depression Index and market volatility**:

### **r = 0.275 · 95% CI [0.196, 0.350] · p < 0.001**

The behavioral signal was more strongly associated with **market uncertainty
(volatility)** than with **market direction (price levels or returns)**.

> **Statistical rigor:** 17 relationships were tested using a Bonferroni-adjusted
> significance threshold of α = 0.0029. Only 3 remained significant after correction.

---

## 🏗️ What I Built

**4 External Data Sources**  
↓  
**Python Data Processing & Cleaning**  
↓  
**PostgreSQL Data Store**  
↓  
**Feature Engineering**  
↓  
**Statistical Testing & Validation**  
↓  
**Flask + Plotly Interactive Dashboard**

## 📈 Key Results

![CorrelationDashboard](images/analysis/CORRELATION_IMPORTANCE_RANKING.png)

| Relationship | r | p-value | Bonferroni |
|---|---|---|---|
| Price Range (Volatility) ↔ Depression Index | 0.275 | 5.5e-11 | ✅ Pass |
| S&P 500 Volatility ↔ Depression Index | 0.267 | 2.0e-10 | ✅ Pass |
| S&P 500 Close ↔ Depression Index | 0.144 | 7.3e-04 | ✅ Pass * |
| Individual stock prices and volume ↔ Depression Index | 0.105 – 0.121 | 0.005 – 0.014 | ❌ Fail |
| Word count and rainfall relationships | −0.072 – 0.077 | > 0.05 | ❌ Not significant |

\* The S&P 500 Close relationship involves two trending series, so part of this correlation may reflect shared trends rather than a direct association (see Limitations).

**Key insight:** the depression signal relates to **uncertainty (volatility)** more than to **direction (price level or returns)**. S&P 500 returns showed no significant relationship with the depression index.

### Lag analysis
Lag windows from t+1 to t+3 were evaluated; the strongest relationships appeared at a 1–3 day lag, suggesting the signal may precede volatility changes. This is an exploratory observation, not a causal test.

### Industry-level patterns
Industry-level correlations with the depression index were small (|r| < 0.15). Consumer-facing industries (leisure products, publishing, restaurants) tended toward positive correlations and capital-intensive industries (copper, cargo transportation, homebuilding) toward negative ones. **These differences have not yet been formally tested** and should be read as descriptive.

### Alternative signals
- **News word count:** no meaningful relationship with the depression index (r = 0.006, 95% CI [−0.078, 0.089]) or with market variables
- **Rainfall:** no significant relationship with stock prices (r = −0.029, p = 0.50)

---

## ⚠️ Limitations

- **Trending series:** correlations between price levels and a slowly moving index can be inflated by shared trends. Volatility measures are less affected, which is one reason they are the more credible result.
- **Autocorrelation:** consecutive trading days are not independent, so the effective sample size is smaller than 551 and p-values are likely optimistic.
- **News text:** only headlines and first lines were processed due to computational constraints.
- **Weather alignment:** national average rainfall does not match where trading decisions are made.
- **Associative, not causal:** results describe co-movement, not cause and effect.

---

## 🔮 Future Work

- **Formally test industry differences** (regression with industry interaction terms, with multiple-comparison control)
- Use **autocorrelation-robust inference** (e.g., Newey–West standard errors) or differenced series
- Apply **Granger causality** tests to examine lead–lag direction
- Extend to volatility forecasting (e.g., GARCH, XGBoost)
- Pair region-specific trading data with localized weather

---

## 📊 Interactive Dashboard

A Flask dashboard supports exploration of time series, industry comparisons, lag effects, and statistical summaries.


The cloud version of this pipeline (EventBridge → Lambda → S3 → EC2 → RDS PostgreSQL, with a Streamlit front end) is documented in the companion repository: [Cloud-Based Data Pipeline & Analytics Platform (AWS)](https://github.com/boa74/Cloud-Based-Data-Pipeline-Analytics-Platform-AWS-)

---

## 🛠️ Tech Stack

Python (pandas, NumPy, SciPy) · PostgreSQL · Flask · Plotly

---

## 📁 Project Structure

```
.
├── src/              # data processing and analysis
├── flask/            # dashboard
├── config/
├── docs/
├── images/analysis/  # figures used in this README
└── README.md
```

---

## 📬 Contact

**Boa Kim** · M.S. Applied Analytics, Columbia University
GitHub: https://github.com/boa74 · LinkedIn: https://linkedin.com/in/boah-kim
