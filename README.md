# 📊 Behavioral Signals & Market Volatility

**End-to-end financial analytics project using Python, SQL, PostgreSQL, and statistical testing to analyze 600K+ records across 498 companies.**

### 600K+ Records  ·  498 Companies  ·  127 Industries  ·  17 Statistical Tests

**Python · SQL · PostgreSQL · Flask · Plotly**

![Executive summary dashboard](images/project_summary.png)

---

## Key Finding

Of **17 relationships tested**, only **3 remained significant after Bonferroni correction**.

The strongest relationship was between the **Depression Index and market volatility**:

**r = 0.275 · 95% CI [0.196, 0.350] · p < 0.001**

> The behavioral signal was more strongly associated with **market uncertainty
> (volatility)** than with **market direction (prices or returns)**.

---

## What I Built

**4 Data Sources → Python Processing → PostgreSQL → Feature Engineering → Statistical Analysis → Flask Dashboard**

- Integrated and cleaned **600K+ multi-source records**
- Engineered returns, rolling volatility, and lagged time-series features
- Queried and analyzed data across **498 companies and 127 industries**
- Tested **17 relationships** with confidence intervals and Bonferroni correction
- Built an interactive **Flask + Plotly dashboard** for result exploration

---

## Key Results

![Correlation ranking](images/analysis/CORRELATION_IMPORTANCE_RANKING.png)

| Relationship | r | p-value | After Correction |
|---|---:|---:|:---:|
| Price Range (Volatility) ↔ Depression Index | **0.275** | 5.5e-11 | ✓ |
| S&P 500 Volatility ↔ Depression Index | **0.267** | 2.0e-10 | ✓ |
| S&P 500 Close ↔ Depression Index | 0.144 | 7.3e-04 | ✓* |
| Individual stock prices / volume ↔ Depression Index | 0.105–0.121 | 0.005–0.014 | — |
| News word count / rainfall | −0.072–0.077 | > 0.05 | — |

*The S&P 500 Close relationship involves trending series and should be
interpreted cautiously. See Limitations.
