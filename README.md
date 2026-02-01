# COVID-19 data analytics dashboard
UKHSA dashboard on hospital bed occupancy vs test positivity rate in England

This project is an interactive COVID-19 analytics dashboard built to analyse and visualise the relationship between hospital bed occupancy and COVID-19 test positivity rates in England. The dashboard ingests data from the UK Health Security Agency (UKHSA) API and presents trends through time-series and comparative visualisations.

The project focuses on end-to-end data handling from API communication and data wrangling to visual analytics and user interaction. Simulating how real-world public data can be transformed into decision-support insights.

Key features:
- Live API integration with UKHSA public health data
- Resilient data architecture using local JSON snapshots as a fallback
- Structured data wrangling and time-series transformation using Pandas
- Interactive visualisations for exploratory analysis
- User-controlled dashboard elements (scaling, time windows, refresh)

# Data Sources
UK Health Security Agency (UKHSA) COVID-19 Dashboard including hospital beds occupied by COVID-19 patients and COVID-19 test positivity rate (7-day rolling average)
Data is accessed via the UKHSA public API and cached locally to ensure dashboard availability during API downtime.

System Architecture
1. API Communication Layer
A custom APIwrapper class was implemented to manage communication with the UKHSA API.
Key responsibilities include constructing API requests, handling rate limiting to prevent access bans, managing timestamps, providing a clean interface for future data extensions. The dashboard has mirrors real-world constraints when working with external data providers.

2. Data Storage & Resilience
To ensure robustness, the dashboard has loads local JSON snapshots when the API is unavailable, allows users to manually refresh data via a dashboard button and separates raw data ingestion from downstream analysis. Which has reflects production style thinking around data availability and fault tolerance.

3. Data Wrangling & Transformation
Raw JSON responses are transformed into structured Pandas DataFrames through dedicated wrangling functions of date parsing and standardisation, dataset merging across multiple sources, using time-series datasets for plotting and filtering and rolling-average calculations


Potential Improvements
- Automate scheduled data refreshes
- Add regional or demographic breakdowns
- Deploy as a lightweight web application
- Implement authentication and access control
- Improve performance for larger datasets
