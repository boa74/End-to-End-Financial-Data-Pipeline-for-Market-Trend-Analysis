# 📊 Time Series Analysis: Depression Index & Market Volatility

> Exploring whether depression-related public signals are associated with stock market volatility — and how these relationships vary across time and industries.

![Project Summary](images/project_summary.png)

## 🔍 Key Findings

- Depression-related search interest showed a **modest positive association with market volatility** (`r ≈ 0.27`).
- The strongest relationships remained statistically significant after **Bonferroni correction**, but explained only about **7% of observed variance**.
- Stronger relationships appeared around a **1–3 day lag**, although this does not establish predictive power.
- Industry patterns differed: **Leisure Products, Publishing, and Restaurants** showed positive relationships, while **Copper, Cargo Ground Transportation, and Homebuilding** showed negative relationships.
- News and rainfall showed **weak or inconsistent relationships**.

## 🎯 Project Overview

This project combines **Google Trends, news, stock market, and weather data** to investigate whether depression-related behavioral signals are associated with market activity.

Rather than building a stock prediction model, the goal was to understand:

1. Whether depression-related signals are associated with market volatility
2. Whether those relationships change across time lags
3. Whether patterns differ across industries

### Dataset at a Glance

**551 days** · **274K+ stock-day records** · **100+ industries** · **4 data sources**

## 🔬 Analysis

The analysis followed four main steps:

**Data Preparation**  
Date alignment → aggregation → volatility measures

**Statistical Testing**  
Pearson correlation → Bonferroni correction

**Time Analysis**  
Lag comparison

**Industry Analysis**  
Comparison across 100+ industries

## 📈 Main Results

| Market Measure | Correlation (r) | Explained Variance |
|---|---:|---:|
| Price Range (Volatility) | **0.2745** | 7.5% |
| S&P 500 Volatility | **0.2668** | 7.1% |
| S&P 500 Close | **0.1436** | 2.1% |

The results suggest a measurable relationship between the depression index and market volatility, but the **effect sizes are small**.

Statistical significance therefore should not be interpreted as evidence of a strong or causal relationship.

### ⏱️ Lag Analysis

Some stronger relationships appeared around a **1–3 day lag**.

This suggests timing may matter, but more formal time-series methods would be required to determine whether the pattern contains predictive information.

### 🏭 Industry Differences

The relationship was not consistent across industries.

**Positive relationships**
- Leisure Products
- Publishing
- Restaurants

**Negative relationships**
- Copper
- Cargo Ground Transportation
- Homebuilding

These findings are exploratory and require additional statistical testing before concluding that particular types of industries are systematically more sensitive.

## ⚠️ Limitations

- Correlation does not establish causation
- Strongest relationships explain less than 8% of variance
- National aggregation may hide regional differences
- Analysis covers only 2017–2018
- Daily observations introduce time-series dependence
- Industry findings require additional testing

## 💡 Key Takeaway

> **Finding statistical significance is only the beginning. The more useful question is where, when, and under what conditions a relationship actually matters.**

## 📊 Interactive Dashboard

The Flask dashboard includes:

- Time-series visualization
- Industry comparisons
- Lag analysis
- Statistical summaries

## 🛠️ Tech Stack

**Python · pandas · NumPy · SciPy · Flask · Plotly · PostgreSQL**

## 🔮 Future Work

- Regional behavioral and weather signals
- Socioeconomic variables
- More focused industry groups
- Different economic periods
- Formal time-series regression
- Statistical testing of industry differences