# 📊 Time Series Analysis: Depression Index & Market Volatility

> Exploring the relationship between depression-related public signals and stock market volatility across industries.

## 🧠 About This Project

This project started with a question:

**Is there a relationship between depression-related signals and stock market behavior?**

Previous research has explored relationships between human emotion and financial markets. I wanted to extend this idea by combining several different types of data — Google Trends, news, stock market data, and weather — and examining whether meaningful patterns could be found across them.

Rather than building a stock prediction model, my goal was to explore these relationships statistically, examine differences across industries and time, and understand which signals were worth investigating further.

---

## ❓ Research Questions

I focused on three main questions:

1. Is the depression index associated with stock market volatility?
2. Does the relationship change when time lags are considered?
3. Do different industries show different relationships with depression-related signals?

I also explored whether depression-related news and rainfall showed meaningful relationships with market behavior.

---

## 📦 Data

The project combines multiple data sources:

* **Google Trends** — search interest related to "depression"
* **CC News** — depression-related news content
* **Yahoo Finance / S&P 500 data** — historical stock market data
* **Weather data** — rainfall measurements across the United States

The main analysis covers:

* **2017-01-01 to 2018-07-05**
* **551 daily observations**
* **274K+ individual stock-day records**
* **100+ industries**

One challenge was that these datasets were collected at different temporal and geographic levels. Aligning them became an important part of the analysis.

---

## 🔧 Data Preparation

The datasets were aligned by date and combined into a daily time-series dataset.

Some important preprocessing steps included:

* Aggregating individual stock records into daily market measures
* Converting weekly Google Trends observations to daily observations using forward filling
* Calculating stock price range as a volatility proxy
* Using 7-day S&P 500 volatility
* Aggregating state-level rainfall into a national average
* Grouping companies by industry for industry-level comparisons

This process also revealed an important limitation: aggregating variables at the national level can remove regional differences that may be meaningful.

---

## 🔬 Statistical Analysis

I used Pearson correlation analysis to examine relationships between the depression index and several market variables.

| Market Measure           | Correlation (r) | Statistical Result |
| ------------------------ | --------------: | ------------------ |
| Price Range (Volatility) |      **0.2745** | p < 0.001          |
| S&P 500 Volatility       |      **0.2668** | p < 0.001          |
| S&P 500 Close            |      **0.1436** | p < 0.001          |

The strongest relationships appeared in **volatility-related measures rather than price level**.

However, these correlations are still relatively small.

For example:

* Price Range ↔ Depression Index: **R² ≈ 7.5%**
* S&P 500 Volatility ↔ Depression Index: **R² ≈ 7.1%**
* S&P 500 Close ↔ Depression Index: **R² ≈ 2.1%**

This means that even the strongest observed relationship explains only a limited portion of the variation in market behavior.

---

## 🧪 Multiple Testing: Bonferroni Correction

Because I tested multiple relationships, I also needed to consider the possibility of finding statistically significant results simply by chance.

A total of **17 correlations** were tested.

Using a standard significance level of:

```text
α = 0.05
```

the Bonferroni-adjusted threshold becomes:

```text
0.05 / 17 = 0.00294
```

After applying this stricter threshold, three relationships remained statistically significant:

* Price Range (Volatility) ↔ Depression Index
* S&P 500 Volatility ↔ Depression Index
* S&P 500 Close ↔ Depression Index

This helped distinguish relationships that remained statistically significant under multiple testing from weaker correlations that appeared significant under the original threshold.

At the same time, statistical significance does not mean the relationships are strong or causal. The effect sizes remain relatively small.

---

## ⏱️ Lag Analysis

I also explored whether the relationship changed when the depression signal and market variables were shifted across time.

Some of the stronger relationships appeared around a **1–3 day lag**.

This suggested that timing may matter when comparing behavioral signals with financial market activity.

However, I do not interpret this result as evidence that depression-related signals can predict future stock volatility.

More formal time-series methods would be needed to determine whether the lag contains meaningful predictive information rather than simply reflecting correlation across time.

---

## 🏭 Industry-Level Analysis

The relationship was not consistent across industries.

Some consumer-oriented industries showed positive correlations with the depression-related signal, including:

* Leisure Products
* Publishing
* Restaurants

Other industries showed negative relationships, including:

* Copper
* Cargo Ground Transportation
* Homebuilding

These patterns led me to consider whether industries more closely connected to consumer behavior and discretionary spending may respond differently to emotional or behavioral signals.

However, these industry-level results are exploratory. Additional statistical testing would be needed before concluding that one type of industry is systematically more sensitive than another.

---

## 📰 News Data

The CC News data did not show a strong or consistent relationship with stock market behavior or the other variables.

This may partly be a data-design issue.

The news dataset covered a broad range of sources, and the analysis relied on depression-related word counts rather than a detailed interpretation of the full content of each article.

Therefore, the result does not necessarily mean that news sentiment has no relationship with market behavior.

Instead, the variable I constructed from this dataset may have been too broad or noisy to capture that relationship effectively.

This was an important lesson from the project:

> **More data does not necessarily create a better signal. How a variable is defined matters.**

---

## 🌧️ Weather Analysis

Rainfall showed very small correlations with the other variables in the current analysis.

For example, the correlation between rainfall and stock close price was approximately:

```text
r = -0.029
```

and rainfall relationships were generally below:

```text
|r| = 0.04
```

One major limitation is how rainfall was aggregated.

Weather is highly regional, but I averaged rainfall measurements across the United States. A national average may remove meaningful local variation.

Therefore, I would not interpret this result as evidence that weather has no relationship with behavior or financial activity.

Instead, a more appropriate analysis might compare:

```text
Regional Weather
        +
Regional Search Behavior
        +
Socioeconomic Conditions
        +
Relevant Economic / Market Activity
        ↓
More Focused Analysis
```

---

## 💭 My Interpretation

The results suggest that there is **some association between the depression index and market volatility**.

The fact that the strongest volatility relationships remained statistically significant after the Bonferroni correction makes them worth further investigation.

However, the effect sizes are relatively small.

Market behavior is influenced by many factors, and relationships involving depression-related behavior may also differ depending on:

* Geographic location
* Time period
* Industry
* Economic conditions
* Socioeconomic characteristics
* Other external events

For this reason, I do not interpret the results as evidence that depression causes market volatility or as a trading signal.

Instead, I see the findings as an indication that behavioral signals may contain information related to market uncertainty, but that the analysis needs to be more focused to understand where and under what conditions the relationship is meaningful.

---

## ⚠️ Limitations

Several limitations are important when interpreting this project.

**Correlation is not causation.**
The analysis identifies statistical associations but does not establish causal relationships.

**The effect sizes are small.**
Even the strongest relationships explain less than 8% of the observed variance.

**Geographic aggregation is broad.**
National-level weather and behavioral signals may hide important state or regional differences.

**The analysis period is limited.**
The main dataset covers 2017–2018, so the relationships may differ during recessions, crises, or other market environments.

**Time-series dependence requires further analysis.**
Daily observations are not necessarily independent, so correlation analysis alone cannot fully describe temporal relationships.

**Industry findings are exploratory.**
Observed differences across industries require additional statistical testing.

---

## 📊 Interactive Dashboard

I built a Flask-based dashboard to explore the results visually.

The dashboard includes:

* Time-series visualization
* Industry comparisons
* Lag analysis
* Statistical summaries

🎥 Demo: https://youtu.be/dxp3GlqZcoo

---

## 🛠️ Tech Stack

* Python
* pandas
* NumPy
* SciPy
* Flask
* Plotly
* PostgreSQL

---

## 📁 Project Structure

```bash
.
├── src/
├── flask/
├── data/
├── images/
├── config/
├── docs/
└── README.md
```

---

## 🔮 Future Work

The next step would be to narrow the scope rather than simply add more variables.

I would like to explore:

* State- or region-level behavioral signals
* Localized weather data
* Socioeconomic variables
* More focused industry or company groups
* Different economic periods
* More formal time-series regression
* Statistical testing of industry differences
* Multiple-testing corrections for expanded analyses

A more geographically and economically focused dataset may help determine whether the relationships observed at the national level become stronger, weaker, or disappear entirely.

---

## 📌 What I Learned

The most useful part of this project was learning that finding a statistically significant relationship is only the beginning of the analysis.

The depression index showed a measurable relationship with volatility in this dataset, while news and rainfall did not behave as I originally expected.

Understanding those differences required looking beyond the correlation itself and thinking about how each variable was defined, aggregated, and aligned.

It also changed how I think about statistical significance. A small p-value can provide evidence that a relationship is unlikely to be explained by random variation under the test assumptions, but it does not tell me whether the relationship is large, causal, or useful in practice.

For me, the next question is not simply whether a relationship is statistically significant, but **where, when, and under what conditions that relationship actually matters.**

---

## 📬 Contact

**Boa Kim**
M.S. Applied Analytics, Columbia University

GitHub: https://github.com/boa74
LinkedIn: https://linkedin.com/in/boah-kim
