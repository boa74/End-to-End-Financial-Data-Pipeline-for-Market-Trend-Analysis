# Behavioral Signals & Market Volatility

**Can alternative behavioral data help identify periods of elevated market uncertainty?**

Financial analysts and investors rely heavily on traditional market indicators
such as prices, returns, and trading volume. This project evaluates whether
public behavioral signals can provide **supplementary information about market
volatility** — and whether observed relationships remain credible after
controlling for statistical noise.

**Python · SQL · PostgreSQL · Flask · Plotly**

---

## Business Problem

Traditional market indicators describe what is happening in financial markets,
but alternative behavioral data may provide additional information about changes
in public attention or sentiment.

The analytical question was:

> **Can behavioral search data serve as a useful supplementary signal for
> identifying changes in market volatility?**

The analysis focused on three questions:

1. Is the behavioral signal associated with market activity?
2. Is the relationship stronger for **market volatility** than for
   **market direction**?
3. Which relationships remain statistically credible after controlling
   for multiple testing?

---

## Project at a Glance

| Data | Market Coverage | Analysis | Validated Results |
|:---:|:---:|:---:|:---:|
| **600K+ records** | **498 companies** | **17 relationships** | **3 significant** |
| 4 data sources | 127 industries | Statistical testing | After Bonferroni correction |

![Executive summary dashboard](images/project_summary.png)

---

## What I Built

**4 Data Sources → Python Processing → PostgreSQL → Feature Engineering → Statistical Analysis → Interactive Dashboard**

- Integrated and cleaned **600K+ records** from market, Google Trends,
  news, and weather data
- Stored and queried structured analytical data using **PostgreSQL / SQL**
- Engineered returns, price-range volatility, rolling volatility,
  and lagged time-series features
- Analyzed **498 companies across 127 industries**
- Tested **17 statistical relationships** with confidence intervals
  and multiple-comparison control
- Built an interactive **Flask + Plotly dashboard** for exploring results

---

## Key Finding

**Behavioral search data showed a stronger relationship with market volatility
than with market direction.**

Of the **17 relationships tested**, only **3 remained significant after
Bonferroni correction**.

The strongest relationship was between the Depression Index and
price-range volatility:

### **r = 0.275 · 95% CI [0.196, 0.350] · p < 0.001**

In contrast, relationships with individual stock prices, trading volume,
news word counts, and rainfall were weak or statistically unreliable.

### Decision Implication

The results suggest that behavioral search data may be more useful as a
**supplementary indicator of market uncertainty** than as a signal for
predicting whether prices will rise or fall.

The finding is associative and exploratory; it does **not** establish
causality or validate a trading strategy.

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

\* The S&P 500 Close relationship involves two trending series, so part of
the observed correlation may reflect shared trends rather than a direct
relationship.

---

## Deeper Analysis

### Lag Effects

Lag windows from `t+1` to `t+3` were evaluated. The strongest relationships
appeared at a 1–3 day lag, suggesting that changes in the behavioral signal
may precede changes in volatility.

This is an exploratory observation, not a causal test.

### Industry Patterns

Industry-level correlations with the Depression Index were generally small
(**|r| < 0.15**).

Consumer-facing industries such as leisure products, publishing, and
restaurants tended toward positive correlations, while several
capital-intensive industries such as copper, cargo transportation, and
homebuilding tended toward negative correlations.

These differences have not been formally tested and should be interpreted
as descriptive patterns.

### Alternative Signals

- **News word count:** no meaningful relationship with the Depression Index
  (`r = 0.006`, 95% CI `[−0.078, 0.089]`) or with market variables
- **Rainfall:** no significant relationship with stock prices
  (`r = −0.029`, `p = 0.50`)

---

## Methodology

### Data

| Source | Variable | Purpose |
|---|---|---|
| Google Trends | Depression Index (0–100) | Behavioral search signal |
| CC-News | Depression word count | Alternative behavioral signal |
| Market data | OHLC prices, volume, S&P 500 | Market measures |
| Weather | Average national rainfall | Alternative comparison signal |

The final analytical dataset covered **551 trading days from January 2017
through July 2018**, with 17+ engineered time-series features.

### Feature Engineering

Features included:

- Daily returns
- High-low price range as a volatility proxy
- 7-day rolling S&P 500 volatility
- Lagged behavioral signals (`t+1` to `t+3`)
- Industry-level market measures

### Statistical Testing

Pearson correlations were calculated with **95% confidence intervals using
Fisher z-transformation**.

Because 17 relationships were tested, Bonferroni correction was applied:

**Adjusted α = 0.05 / 17 = 0.0029**

This reduced the likelihood of interpreting chance correlations as
meaningful findings.

---

## Limitations

- **Trending series:** correlations between price levels and a slowly moving
  index may be inflated by shared trends. Volatility measures are less affected,
  making them the more credible result.

- **Autocorrelation:** consecutive trading days are not independent, so the
  effective sample size may be smaller than 551 and conventional p-values may
  be optimistic.

- **News data:** only headlines and first lines were processed due to
  computational constraints.

- **Weather alignment:** national average rainfall does not correspond directly
  to where trading decisions are made.

- **Association, not causation:** the analysis identifies statistical
  co-movement and should not be interpreted as evidence that behavioral
  signals cause changes in financial markets.

---

## Interactive Dashboard

The **Flask + Plotly dashboard** supports exploration of:

- Time-series patterns
- Correlation results
- Industry comparisons
- Lag effects
- Statistical summaries

The cloud implementation of the broader pipeline
(**EventBridge → Lambda → S3 → EC2 → RDS PostgreSQL → Streamlit**)
is documented separately:

[Cloud-Based Data Pipeline & Analytics Platform (AWS)](https://github.com/boa74/Cloud-Based-Data-Pipeline-Analytics-Platform-AWS-)

---

## Technical Details

**Analysis:** Python, pandas, NumPy, SciPy  
**Database:** SQL, PostgreSQL  
**Visualization:** Flask, Plotly  
**Methods:** Time-series feature engineering, Pearson correlation,
Fisher z confidence intervals, Bonferroni correction

### Repository Structure

```text
.
├── src/                  # Data processing and statistical analysis
├── flask/                # Interactive dashboard
├── config/               # Configuration
├── docs/                 # Documentation
├── images/
│   └── analysis/         # Analysis figures
└── README.md
