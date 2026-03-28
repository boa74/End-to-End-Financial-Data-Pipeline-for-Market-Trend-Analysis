# 📊 End-to-End Financial Data Pipeline for Market Sentiment & Volatility Analysis

## ⚡ TL;DR
- Built an end-to-end data pipeline integrating 600K+ multi-source time-series records  
- Combined financial, sentiment, and external data into a unified analytical dataset  
- Identified statistically significant relationships between public sentiment and market volatility  
- Developed models to estimate volatility using sentiment-driven features  
- Delivered insights through an interactive Flask dashboard  

---

## 🚀 Overview

Built an end-to-end data pipeline integrating multi-source time-series data (600K+ records) to analyze how public sentiment impacts market volatility.

This project combines data engineering, statistical analysis, and modeling to uncover patterns that support data-driven decision-making in financial markets.

---

## 🧠 Problem

Financial data is often fragmented across multiple sources, making it difficult to identify relationships between market behavior and external signals like public sentiment.

Traditional analysis focuses on price movements and overlooks behavioral factors that may influence volatility.

---

## 🛠️ Approach

### Data Engineering
- Built ETL pipelines to ingest, clean, and integrate multi-source datasets  
- Processed 600K+ time-series records from financial, sentiment, and external data  
- Designed PostgreSQL schema for structured storage  

### Feature Engineering & Analysis
- Engineered features including volatility metrics and sentiment indices  
- Conducted statistical analysis with significance testing  
- Performed time-series alignment and lag analysis  

### Modeling
- Built regression models to estimate market volatility  
- Evaluated feature importance to identify key drivers  

### Visualization
- Developed interactive dashboard using Flask and Plotly  
- Enabled real-time exploration of trends and correlations  

---

## 📊 Key Results

- Identified significant relationships between sentiment and market volatility  
- Found volatility metrics more strongly correlated than price levels  
- Discovered industry-specific sensitivity to sentiment signals  
- Demonstrated value of external data in financial analysis  

---

## 💡 Impact

- Shows how sentiment can act as a leading indicator of volatility  
- Provides a framework for integrating external data into financial pipelines  
- Bridges data engineering and data science for better decision-making  

---

## 🏗️ Architecture
Raw Data → ETL → Feature Engineering → Modeling → Dashboard

## 🧩 Key Components

- **ETL Pipeline**: `src/etl/merge_all_datasets.py`  
  → Integrates multiple time-series datasets into a unified format  

- **Analysis Module**: `src/analysis/time_series_depression_stock_analysis.py`  
  → Performs statistical analysis and correlation testing  

- **Database Loader**: `src/etl/export_to_postgres.py`  
  → Loads processed data into PostgreSQL  

- **Web Dashboard**: `flask/app.py`  
  → Serves interactive visualizations and analytics  

## 🌐 Demo : will update the video


Run locally:

cd flask  
python app.py  

Open: http://127.0.0.1:18502

## ⚙️ Tech Stack

- Python, SQL  
- Pandas, NumPy, SciPy  
- Flask  
- PostgreSQL  
- Plotly  

## 📁 Structure

├── flask/        # Dashboard  
├── src/          # ETL + analysis  
├── data/         # datasets  
├── config/       # DB schema  