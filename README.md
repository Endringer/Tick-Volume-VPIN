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

How to Run

Place your raw MT5 export files in data/raw/:
GC_HTC_Updated.csv
NQ_HTC_Updated.csv

Open the notebook in Jupyter Lab / VS Code / Jupyter Notebook.
Run the cells in order (they are already numbered sequentially):
GC HTC pipeline (cleaning → classification → VPIN → regressions → plots)
NQ HTC pipeline (same steps)


All output files are automatically saved in the results/ folder:

*_final_cleaned.csv
*_buckets_50_per_day.csv
*_buckets_with_metrics.csv
*_descriptive_stats_buckets_filtered.csv
*_correlation_matrix_buckets_filtered.csv
*_ols_model*.txt and *_model2_coefficients_filtered.csv
Regression plots, histograms, boxplots (.png)


Main Outputs Generated
Gold (GC)

gc_vpin_regression_volatility_no_outliers.png
gchc_ols_model1_summary_filtered.txt / gchc_ols_model2_summary_filtered.txt

NASDAQ (NQ)

nqhtc_vpin_absreturn_model2_scatter_filtered.png
nqhtc_ols_model1_summary_filtered.txt / nqhtc_ols_model2_summary_filtered.txt

All descriptive statistics and correlation matrices used in the dissertation tables are also exported.

Dissertation Reference
This notebook exactly reproduces the methodology, results, and figures from:
Endringer, L. (2025). Estimating Order Flow Toxicity in CFD Markets: A VPIN-Based Approach Using Tick Volume.
London Metropolitan University, FE6P04S Dissertation.
If you use or adapt this code in your research, please cite the dissertation.

License
MIT License. Feel free to use, modify, and extend. Attribution to the original dissertation is appreciated.

Questions / Contact

Author: Luccas Endringer
GitHub Issues: Open an issue if you encounter any problems running the notebook
Academic use: Contact via university email or the dissertation repository


Happy running!
Your tick-volume VPIN pipeline is now fully documented and ready for publication. 📈
