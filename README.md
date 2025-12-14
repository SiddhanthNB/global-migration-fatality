# Global Migration Fatality Analysis

This repository holds a single notebook that explores global migration incidents from 2014–2025 using the Missing Migrants Project data. The work examines temporal and regional fatality patterns and builds models to flag high-risk weeks.

## Contents
- `main.ipynb`: full analysis, visuals, and modeling workflow.
- `data/Missing_Migrants_Global_Figures_allData.csv`: raw dataset used by the notebook.
- `requirements.txt`: Python dependencies to run the notebook.

## Setup
1) Install Python 3.10+.
2) Create and activate a virtual environment: `python -m venv .venv && source .venv/bin/activate` (on Windows use `Scripts\\activate`).
3) Install dependencies: `pip install -r requirements.txt`.

## How to run
- Launch Jupyter: `jupyter notebook`, then open `main.ipynb`.
- Ensure the dataset stays at `data/Missing_Migrants_Global_Figures_allData.csv` or update the data-loading cell path.
- Run the notebook top to bottom for a clean, reproducible run.

## Notebook flow
- Load and clean the Missing Migrants dataset: filter to migration incidents, standardize labels, rename columns, and handle missing values.
- Exploratory analysis: temporal trends, route and region hotspots, cause-of-death mix, COVID-19 effects, seasonal heatmaps, and geospatial bubble maps.
- Feature engineering: weekly aggregation by region, full time grid with zero-fill, binary high-risk flag (75th percentile threshold), lag features, and rolling statistics.
- Modeling: target encoding for categories, SMOTE for class balance, time-based split (train to 2022, test 2023–2025), baseline SARIMAX/XGBoost/Random Forest, then RandomizedSearchCV to tune Random Forest.
- Results: Random Forest chosen for stable performance; key features are regional indicators and recent history; risk peaks in the Mediterranean and summer months.

## Notes
- The notebook writes no new files; outputs are inline plots and metrics.
- If you extend the analysis, keep the same data path and rerun all cells after changes to maintain reproducibility.
