# Where Does the Apparent Advantage of Machine Learning in Profitability Forecasting Come From?

**Evidence from Greek Private Firms and a Measurement-Error Experiment**

MSc Thesis in Financial Technology (Fintech) · National and Kapodistrian University of Athens · 2026
Author: Sofia Antonakou

---

## Overview

This repository contains the analysis code for the thesis. The study forecasts next-year return on assets (ROA) for 2,000 Greek private firms (20,000 firm-years, 2016–2025). The financial data were extracted automatically from statements filed with the General Commercial Registry of Greece (ΓΕΜΗ).

The thesis asks where the advantage of machine-learning models over a persistence benchmark comes from: from information in the financial ratios, from the firm's own profit history, or from errors in automatically extracted data.

## Main findings

1. **ROA level.** Once a model has up to five years of the firm's own ROA history, financial ratios add nothing measurable. The difference in mean absolute error is −0.0003 (95% interval −0.0011 to +0.0004), which is inside the pre-set equivalence margin of 0.003.
2. **Probability of a loss.** Ratios add a small gain of 0.0087 in AUC. It is positive in five of six forecast years.
3. **Data quality.** An error-injection experiment shows that the advantage of history-based models over Persistence grows with noise in lagged ROA. A standard balance sheet identity check catches distorted total assets but misses errors in net profit.

## Repository contents

| Notebook | Purpose |
|---|---|
| `ml_profitability_notebook.ipynb` | Main analysis: feature sets, benchmark hierarchy, nested rolling-origin evaluation, firm-clustered bootstrap, loss classifiers and the error-injection experiment |
| `sector_region_analysis.ipynb` | Descriptive analysis of the reporting population and the panel by legal form, region and sector |

## Methods at a glance

- Benchmark ladder: training mean → Persistence → AR(1) → models on the firm's own ROA history → models with financial ratios
- Models: XGBoost (squared and pseudo-Huber loss), random forest, ridge regression
- Nested rolling-origin evaluation over six forecast years (9,803 firm-years)
- Paired bootstrap clustered by firm (2,000 draws) with equivalence margins (0.003 MAE, 0.005 RMSE, 0.01 AUC)
- Error-injection experiment calibrated on a manual audit of 50 filings

## Data availability

The panel is built from filings and registry metadata published by ΓΕΜΗ under its [Open Data terms of use](https://opendata.businessportal.gr/license/). **Neither the underlying filings nor the constructed panel are included in this repository**, so the notebooks are shared for transparency and cannot be run end to end without the data. The derived data and the `thesis_tables` notebook are available from the author upon request.

## Citation

If you refer to this work, please cite the thesis:

> Antonakou, S. (2026) *Where Does the Apparent Advantage of Machine Learning in Profitability Forecasting Come From? Evidence from Greek Private Firms and a Measurement-Error Experiment*. MSc thesis, National and Kapodistrian University of Athens.

## License

© 2026 Sofia Antonakou. All rights reserved. The code is published for reading and verification of the thesis results. Please contact the author before reusing it.
