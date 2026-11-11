# NYC Building Check

NYC Building Check is a portfolio project in development that helps renters investigate a building before signing a lease. The first version focuses on one question: **Do city records show recurring pest issues at this address?**

## What the app will show

- A building timeline with reported pest complaints and HPD-issued violations.
- An explainable concern score based on recency, recurrence, and violation severity, with links to the records behind it.
- A 90-day forecast of a newly issued pest violation, once the model has been evaluated on held-out dates.

## Forecasting experiment

Can the timing and recurrence of past reports improve predictions over a historical recurrence rate? The plan is to compare a baseline with a Bayesian time-to-event model in PyMC and evaluate probability calibration on later records. The forecast concerns a **recorded HPD violation**, which also depends on reporting and inspections.

## Stack

Python and `uv.lock` for a reproducible environment, Streamlit for the demo, FastAPI for building reports, and Airflow with AWS S3 for scheduled data refreshes.

## Local setup

Once the app and lockfile are checked in, run these commands from the repository root:

```bash
uv sync --locked
uv run --locked streamlit run app.py
```

## Data sources

- [NYC Open Data: Housing Maintenance Code Complaints and Problems](https://data.cityofnewyork.us/d/ygpa-z7cr)
- [NYC Open Data: Housing Maintenance Code Violations](https://data.cityofnewyork.us/d/wvxf-dwi5)
