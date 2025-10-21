# Optiver — Trading at the Close (Baseline Project)

This repository contains a clean, verified baseline solution for the Kaggle competition **Optiver — Trading at the Close**.  
The notebook builds a fully reproducible pipeline for generating a valid submission file using a simple but solid statistical baseline:

**Predict the mean `target` per `stock_id` (parsed from `row_id`).**

Although the competition is closed, this project serves as a learning and portfolio example in quantitative finance, time-series modeling, and Kaggle pipeline engineering.

---
# Optiver — Trading at the Close (Baseline)

A clean, verified **baseline solution** for the Kaggle competition **Optiver — Trading at the Close**.  
This notebook builds a fully reproducible pipeline that generates a valid submission using a simple but solid approach:

## Features
- Automatic Kaggle path detection (`train.csv`, `sample_submission.csv`)
- Defensive CSV writer (avoids PermissionError)
- Data validation for schema, row count, and column order
- Baseline model: mean `target` per `stock_id` (fallback to global mean)
- Optional validation using last `date_id` values
- Submission verifier for clean `submission_verified.csv`

---

## Model Logic

1. Load training data: `train.csv`
2. Compute per-stock average:
   ```python
   global_mean = train['target'].mean()
   per_id = train.groupby('stock_id')['target'].mean()

## Quickstart (Kaggle)

1. Open the notebook in **Kaggle Code** and **attach** the *Optiver — Trading at the Close* dataset.
2. Run all cells. You should see:
   - “`submission_verified.csv` passes checks ✅”
3. In the right panel, **Submit to Competition** → select `submission_verified.csv`.

> Since the competition is closed, you might not receive a live score, but the pipeline and file are valid.

---

## Quickstart (Local)

Install dependencies and open the notebook:

```bash
pip install -r requirements.txt
# start Jupyter or VS Code to run the notebook locally
