# Tick-Volume-VPIN-Model + MT5 Data Cleaner


**Complete Jupyter Notebook implementation** accompanying the dissertation  
**Author:** Luccas Endringer  
**Institution:** London Metropolitan University  
**Dissertation:** Estimating Order Flow Toxicity in CFD Markets – A VPIN-Based Approach Using Tick Volume (December 2025)

---

### Overview

This single Jupyter Notebook (`Tick-VPIN-MT5-Cleaner+Model.ipynb`) contains the **entire end-to-end Python pipeline** used to produce all empirical results in the dissertation.

It processes raw high-frequency tick data exported from **MetaTrader 5 (MT5)** for two CFD instruments from **Hantec Markets**:
- **Gold (XAUUSD)** → `GC_HTC_Updated.csv`
- **NASDAQ 100 (NAS100/US100)** → `NQ_HTC_Updated.csv`

The notebook performs:
- Data cleaning and timezone-aware filtering to regular NASDAQ trading hours (09:30–16:00 ET)
- Mid-price construction
- Deterministic tick-rule trade classification with carry-forward for neutral ticks
- Dynamic volume-bucket construction (~50 buckets per day using **tick volume** as proxy)
- VPIN calculation (rolling absolute order imbalance)
- Bucket-level metrics: absolute return (volatility proxy) and average spread
- Outlier removal (> 3 standard deviations)
- Descriptive statistics and correlations
- OLS regressions (VPIN → contemporaneous volatility, with and without controls)
- Publication-ready plots (regression scatters, histograms, boxplots)

Everything is fully reproducible and matches the methodology, tables, and figures presented in the dissertation.

---

### Key Features

- Handles **raw MT5 tick format** (`<DATE>`, `<TIME>`, `<BID>`, `<ASK>`, etc.)
- Robust cleaning with linear interpolation handling (already applied in the dissertation)
- Exact replication of the dissertation’s **deterministic mid-price classification** (no BVC)
- Bucket calibration and VPIN computation as described in Chapter 3
- Outlier-filtered regressions and descriptive statistics (Chapter 4)
- Generates all CSV outputs used in the dissertation results section

---

### Repository Structure (recommended)
