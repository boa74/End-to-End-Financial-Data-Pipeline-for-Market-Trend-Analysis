# 📊 Time Series Analysis: Depression Index & Market Volatility

> Exploring whether depression-related behavioral signals contain useful information about stock market volatility.

## 🔑 Main Finding

**Depression-related search activity showed a modest but statistically significant relationship with market volatility (`r ≈ 0.27`), with stronger patterns appearing around a 1–3 day lag and varying across industries.**

The relationship was stronger for **volatility than for stock price levels**, suggesting that behavioral signals may be more useful for understanding **market uncertainty and risk** than market direction.

While the results do not establish predictive power, they suggest that behavioral data could be explored as a **supplementary signal for volatility forecasting and market-risk monitoring** alongside traditional financial indicators.

![Project Summary](images/project_summary.png)

## 🎯 Project Overview

Financial markets are influenced not only by economic fundamentals, but also by uncertainty, sentiment, and human behavior.

This project explores whether **alternative behavioral and environmental signals** — including depression-related Google search activity, news coverage, and weather — show measurable relationships with stock market behavior.

Rather than building a stock prediction model, the goal was to investigate whether these signals contain information that could potentially complement traditional financial indicators in areas such as **market monitoring, volatility analysis, and risk assessment**.

I focused on three main questions:

1. Is the depression index associated with stock market volatility?
2. Does the relationship change when time lags are considered?
3. Do different industries show different relationships with depression-related signals?

I also explored whether depression-related news and rainfall showed meaningful relationships with market behavior.

---

## 🔍 Key Findings & Business Implications

### 1. Behavioral signals showed a measurable relationship with market volatility

Depression-related search interest showed a modest positive relationship with market volatility.

| Market Measure | Correlation (r) | Explained Variance |
|---|---:|---:|
| Price Range (Volatility) | **0.2745** | **7.5%** |
| S&P 500 Volatility | **0.2668** | **7.1%** |
| S&P 500 Close | **0.1436** | **2.1%** |

The strongest relationships appeared in **volatility measures rather than market price levels**.

After applying Bonferroni correction for multiple testing, all three relationships remained statistically significant.

However, the effect sizes were relatively small. Even the strongest relationship explained less than 8% of observed variation.

**Business implication:** Behavioral data such as search activity may provide a **supplementary signal for market-risk and volatility monitoring**, particularly when combined with traditional financial indicators rather than used independently.

---

### 2. Timing may contain useful information

Lag analysis showed that some of the stronger relationships appeared around a **1–3 day lag**.

This suggests that behavioral signals and financial market activity may not move simultaneously.

However, correlation at a lag does **not** establish forecasting ability.

**Business implication:** The observed timing patterns provide a reason to test behavioral indicators as additional features in more formal **volatility forecasting or early-warning models**.

---

### 3. The relationship varies across industries

The relationship between the depression index and market behavior was not consistent across industries.

Examples of **positive relationships** included:

- Leisure Products
- Publishing
- Restaurants

Examples of **negative relationships** included:

- Copper
- Cargo Ground Transportation
- Homebuilding

These results are exploratory and require additional statistical testing before concluding that particular industries are systematically more sensitive to behavioral signals.

**Business implication:** Alternative behavioral signals may be more informative when analyzed at the **industry or segment level** rather than across the entire market, potentially supporting more targeted sector monitoring and risk analysis.

---

### 4. More data does not necessarily mean a better signal

Depression-related news and rainfall showed much weaker or less consistent relationships with market behavior.

This may partly reflect how the variables were constructed.

For example, weather is highly regional, but rainfall was aggregated into a national average. This may remove meaningful geographic variation.

Similarly, the news variable relied on broad depression-related word counts rather than detailed contextual or sentiment analysis.

**Business implication:** The usefulness of alternative data depends heavily on **how the signal is defined, aggregated, and aligned with the business problem**.

A weak result does not necessarily mean the underlying data source has no value — it may indicate that a more targeted feature design is needed.

---

## 💡 Overall Takeaway

This project provides preliminary evidence that **behavioral signals such as depression-related search activity may contain information related to market volatility**.

The results are not strong enough to support a standalone trading or prediction strategy. Instead, they point toward a more practical analytical question:

> **Can alternative behavioral signals add measurable predictive value beyond traditional financial indicators?**

Testing that question would require combining these signals with traditional market, economic, and regional variables in a formal forecasting framework.

The broader lesson from the project is that finding statistical significance is only the beginning.

The more useful question is:

> **Where, when, and under what conditions does a relationship actually matter?**

---

## 📦 Data

The project combines four different data sources:

| Data Source | Signal |
|---|---|
| **Google Trends** | Search interest related to "depression" |
| **CC News** | Depression-related news content |
| **Yahoo Finance / S&P 500** | Historical stock market data |
| **Weather Data** | Rainfall measurements across the United States |

### Dataset at a Glance

- **2017-01-01 to 2018-07-05**
- **551 daily observations**
- **274K+ individual stock-day records**
- **100+ industries**

One of the main challenges was that these datasets were collected at different temporal and geographic levels.

Aligning them became an important part of the analysis.

---

## 🔧 Data Preparation

The datasets were aligned by date and combined into a daily time-series dataset.

Key preprocessing steps included:

- Aggregating individual stock records into daily market measures
- Converting weekly Google Trends observations to daily observations using forward filling
- Calculating stock price range as a volatility proxy
- Using 7-day S&P 500 volatility
- Aggregating state-level rainfall into a national average
- Grouping companies by industry for industry-level comparisons

This process also revealed an important analytical limitation:

> **Aggregation can simplify analysis while simultaneously removing meaningful variation.**

This became particularly important when interpreting the weather and industry results.

---

## 🔬 Statistical Analysis

I used **Pearson correlation analysis** to examine relationships between the depression index and market variables.

The strongest relationships were:

| Market Measure | Correlation (r) | Statistical Result |
|---|---:|---|
| Price Range (Volatility) | **0.2745** | p < 0.001 |
| S&P 500 Volatility | **0.2668** | p < 0.001 |
| S&P 500 Close | **0.1436** | p < 0.001 |

The strongest associations appeared in volatility-related measures rather than price level.

### Effect Size

Statistical significance does not necessarily imply practical importance.

The corresponding explained variance was:

- Price Range ↔ Depression Index: **R² ≈ 7.5%**
- S&P 500 Volatility ↔ Depression Index: **R² ≈ 7.1%**
- S&P 500 Close ↔ Depression Index: **R² ≈ 2.1%**

Therefore, even the strongest observed relationship explains only a limited portion of market behavior.

---

## 🧪 Multiple Testing: Bonferroni Correction

Because multiple relationships were tested, I also considered the possibility of obtaining statistically significant results simply by chance.

A total of **17 correlations** were tested.

Using:

```text
α = 0.05
```

the Bonferroni-adjusted threshold becomes:

```text
0.05 / 17 = 0.00294
```

After applying this stricter threshold, three relationships remained statistically significant:

- Price Range (Volatility) ↔ Depression Index
- S&P 500 Volatility ↔ Depression Index
- S&P 500 Close ↔ Depression Index

This helped distinguish relationships that remained statistically significant under multiple testing from weaker results.

At the same time:

> **Statistical significance does not mean the relationship is strong, causal, or useful for prediction.**

---

## ⏱️ Lag Analysis

I also explored whether the relationship changed when depression-related signals and market variables were shifted across time.

Some stronger relationships appeared around a **1–3 day lag**.

This suggests that timing may matter when comparing behavioral signals with financial market activity.

However, I do **not** interpret this result as evidence that depression-related signals predict future stock volatility.

More formal time-series methods would be required to determine whether the lag contains meaningful predictive information rather than simply reflecting correlation across time.

---

## 🏭 Industry-Level Analysis

The relationship was not consistent across industries.

Some industries showed positive correlations with the depression-related signal, including:

- **Leisure Products**
- **Publishing**
- **Restaurants**

Other industries showed negative relationships, including:

- **Copper**
- **Cargo Ground Transportation**
- **Homebuilding**

These differences suggest that market-wide aggregation may hide meaningful industry-level patterns.

However, these findings remain exploratory.

Additional statistical testing would be required before concluding that particular categories of industries are systematically more sensitive to behavioral signals.

---

## 📰 News Analysis

The CC News data did not show a strong or consistent relationship with stock market behavior or the other variables.

This may partly be a **data-design issue**.

The dataset covered a broad range of sources, while the analysis relied on depression-related word counts rather than detailed interpretation of the content of each article.

Therefore, the result does not necessarily mean that news sentiment has no relationship with market behavior.

Instead, the variable constructed from the dataset may have been too broad or noisy to capture that relationship effectively.

> **More data does not necessarily create a better signal. How a variable is defined matters.**

---

## 🌧️ Weather Analysis

Rainfall showed very small correlations with the other variables.

For example:

```text
Rainfall ↔ Stock Close: r ≈ -0.029
```

Rainfall relationships were generally below:

```text
|r| = 0.04
```

A major limitation is geographic aggregation.

Weather is highly regional, but rainfall measurements were averaged across the United States. A national average may remove meaningful local variation.

Therefore, I would not interpret this result as evidence that weather has no relationship with behavior or financial activity.

A more focused analysis could instead examine:

```text
Regional Weather
        +
Regional Search Behavior
        +
Socioeconomic Conditions
        +
Relevant Economic / Market Activity
        ↓
More Focused Market Analysis
```

---

## ⚠️ Limitations

Several limitations are important when interpreting the results:

- **Correlation is not causation.** The analysis identifies statistical associations but does not establish causal relationships.
- **Effect sizes are small.** Even the strongest relationships explain less than 8% of observed variance.
- **Geographic aggregation is broad.** National-level signals may hide important regional differences.
- **The analysis period is limited.** The primary dataset covers 2017–2018.
- **Daily observations are temporally dependent.** Correlation analysis alone cannot fully characterize time-series relationships.
- **Industry findings are exploratory.** Additional testing is required before generalizing industry-level differences.
- **Lag correlation does not establish predictive ability.** Formal forecasting models and out-of-sample testing would be required.

---

## 📊 Interactive Analytics Dashboard

I built a **Flask + Plotly interactive dashboard** to explore the results visually.

The dashboard includes:

- Time-series visualization
- Industry comparisons
- Lag analysis
- Statistical summaries

---

## 🛠️ Tech Stack

- **Python**
- **pandas**
- **NumPy**
- **SciPy**
- **Flask**
- **Plotly**
- **PostgreSQL**

---

## 📁 Project Structure

```text
.
├── src/
├── flask/
├── data/
├── images/
│   └── project_summary.png
├── config/
├── docs/
└── README.md
```

---

## 🔮 Future Work

The next step would be to **narrow and deepen the analysis rather than simply add more variables**.

Potential extensions include:

- State- or region-level behavioral signals
- Localized weather data
- Socioeconomic variables
- More focused industry or company groups
- Different economic environments
- Formal time-series regression
- Out-of-sample forecasting
- Testing whether behavioral signals improve forecasts beyond traditional market indicators
- Statistical testing of industry differences
- Multiple-testing corrections for expanded analyses

A particularly useful next step would be to compare:

```text
Traditional Market Indicators
            ↓
      Baseline Model

Traditional Indicators
          +
Behavioral Signals
          ↓
     Extended Model

            ↓
Does the behavioral data improve
out-of-sample volatility forecasts?
```

This would move the project from identifying **statistical associations** toward measuring whether alternative behavioral data provides **incremental predictive value**.

---

## 📌 What I Learned

The most useful lesson from this project was that finding a statistically significant relationship is only the beginning of the analysis.

The depression index showed a measurable relationship with volatility, while news and rainfall did not behave as originally expected.

Understanding those differences required looking beyond correlation and considering how each variable was **defined, aggregated, and aligned**.

It also changed how I think about statistical significance.

A small p-value can provide evidence that a relationship is unlikely to be explained by random variation under the test assumptions, but it does not tell us whether that relationship is **large, causal, predictive, or useful in practice**.

For me, the more important analytical question became:

> **Where, when, and under what conditions does this relationship actually matter?**

---

## 📬 Contact

**Boa Kim**  
M.S. Applied Analytics, Columbia University

**GitHub:** [github.com/boa74](https://github.com/boa74)  
**LinkedIn:** [linkedin.com/in/boah-kim](https://linkedin.com/in/boah-kim)