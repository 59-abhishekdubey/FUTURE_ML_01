# FUTURE_ML_01

Forecasting project using a notebook-centric ML pipeline with Ridge regression, achieving a **14.7% improvement** over baseline.

## Business Problem

Accurate demand/quantity forecasting is critical for inventory planning and resource allocation. This project builds an end-to-end forecasting pipeline to predict target values from historical transaction data, reducing error compared to naive baselines.

## Dataset

- **train.csv** -- Historical records with features and target variable
- **test.csv** -- Held-out set for generating submission predictions

## Approach

The entire pipeline lives in a single Jupyter notebook:

1. **Data Cleaning** -- Handling missing values, type conversions, outlier detection
2. **EDA** -- Distribution analysis, correlation heatmaps, time-series decomposition
3. **Feature Engineering** -- Encoding categoricals, scaling numericals, creating lag/rolling features
4. **Modeling** -- Ridge regression with cross-validated hyperparameter tuning
5. **Evaluation** -- WAPE metric on validation and test sets
6. **Error Analysis** -- Residual distributions, worst-case segment identification
7. **Recursive Forecasting** -- Multi-step ahead predictions
8. **Visualizations** -- Business-facing charts and summaries

## Model Performance

| Model             | WAPE    | vs Baseline |
|-------------------|---------|-------------|
| Baseline (mean)   | 0.2177  | --          |
| **Ridge (tuned)** | **0.1854** | **-14.7%** |

## How to Run

### 1. Install dependencies

```bash
python -m pip install -r requirements.txt
```

If using a virtual environment:

```bash
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
```

### 2. Run the notebook (VS Code — primary workflow)

1. Open `FUTURE_ML_01` in VS Code
2. Open `notebooks/01_store_sales_forecasting.ipynb`
3. When prompted, select the Python interpreter that has the required packages installed
4. Run cells from the VS Code notebook interface

> This is the intended workflow. A browser-based `jupyter notebook` server is not required.

### 3. Run the Streamlit dashboard

```bash
python -m streamlit run dashboard/app.py
```

Opens at `http://localhost:8501`.

> `app.py` lives inside `dashboard/`, so `python app.py` from the root will **not** work.
> On Windows, use `python -m streamlit` — the bare `streamlit` command may not be on PATH.

### Dataset

Place `train.csv` and `test.csv` in `data/raw/`.

### Submission

After running the full notebook, `submission.csv` is generated in the repository root.

## Project Structure

```
FUTURE_ML_01/
├── data/
│   ├── raw/            # Raw CSVs (gitignored)
│   ├── processed/      # Cleaned CSVs (gitignored)
│   └── README.md       # Dataset instructions
├── notebooks/          # Jupyter notebook pipeline
├── reports/
│   └── figures/        # Exported charts
├── dashboard/
│   └── app.py          # Streamlit dashboard
├── requirements.txt
├── .gitignore
└── README.md
```

## License

Specify your license here.
