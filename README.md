# Finance & Economics Time-Series Analysis
**NYU Tandon Spring 2026 Data Science Bootcamp**

## Team
| Name | Email |
|------|-------|
| Hongtai Du | hd2609@nyu.edu |
| Kaiwen Lin | kl5975@nyu.edu |
| Josephine Odusanya | joo9964@nyu.edu |

## Overview
Analysis of daily financial market data (2000–2008) across three major indices — **Dow Jones, NASDAQ, and S&P 500** — alongside macroeconomic indicators including GDP growth, inflation, interest rates, and consumer metrics.

## Dataset
- **Source:** Finance & Economics Dataset (via Supabase)
- **Size:** 3,000 rows × 24 columns
- **Date range:** 2000-01-01 → 2008-03-18
- **Indices:** Dow Jones, NASDAQ, S&P 500

## Pipeline
1. **Data Ingestion & Cleaning** — Fetched from Supabase, cleaned dates, stripped whitespace, engineered `Daily Return (%)` and `Price Range` features
2. **SQL Integration** — Stored in SQLite; queried average metrics per index, yearly summaries, and top volatility days
3. **Time-Series Decomposition** — Monthly S&P 500 series decomposed into trend, seasonal, and residual components; ADF stationarity tests applied
4. **Modeling** — AR(2), MA(2), ARMA(2,2), ARIMA(1,1,1) fitted on 79-month train set, evaluated on 20-month test set
5. **Evaluation** — MAE, RMSE, MAPE computed; all models benchmarked against a Naive baseline

## Results
| Model | MAE | RMSE | MAPE |
|-------|-----|------|------|
| AR(2) | 240.47 | 310.42 | 8.16% |
| MA(2) | 240.29 | 310.32 | 8.16% |
| ARMA(2,2) | 258.74 | 329.64 | 8.81% |
| **ARIMA(1,1,1)** | **239.20** | **309.56** | **8.15%** |
| Naive Baseline | 594.00 | 650.80 | 19.08% |

**Best model: ARIMA(1,1,1)** — all models significantly outperformed the Naive baseline.

## Output Figures
| File | Description |
|------|-------------|
| `fig1_overview_sql.png` | Data overview + SQL insights |
| `fig2_decomposition.png` | Trend / seasonal / residual |
| `fig3_acf_pacf_ci.png` | ACF, PACF, confidence interval guide |
| `fig4_models_evaluation.png` | Forecasts + MAE/RMSE/MAPE |

## Tech Stack
`Python` · `Pandas` · `NumPy` · `Statsmodels` · `Matplotlib` · `SQLite` · `Supabase`

## Usage
```bash
# Open in Google Colab or run locally
jupyter notebook DSB2.ipynb
```
> Requires a Supabase connection for data ingestion. Update `SUPABASE_URL` and `SUPABASE_KEY` if needed.
