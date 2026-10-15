# Spain-Cardiovascular-Clinical-Trial-Operations-Analytics
An end-to-end clinical trial analytics solution analyzing **3,081 cardiovascular clinical trials in Spain** sourced from ClinicalTrials.gov. This project combines upstream SQL data engineering in SQLite with an interactive two-page Power BI dashboard to evaluate trial timelines, patient enrollment scale, funding distribution, and geographic research concentration.

---

## Dashboard Overview & Key Visualizations

### Page 1: Executive Summary
![Executive Summary](Cardio_Trials_SS/Page1_Executive_Summary.png)

* **Key Performance Indicators (KPIs):** `Total Trials` (3K), `Total Enrollment Target` (20M), and `Avg Duration` (47 Months).
* **Average Duration by Phase:** Bar chart analyzing study timelines across development phases.
* **Trial Status Breakdown:** Donut chart evaluating study completion and active recruiting statuses.
* **Sponsor Distribution:** Proportional breakdown of funding bodies (Industry vs. Non-Profit/Gov).

---

### Page 2: Time & Geographic Distribution
![Time & Geographic Distribution](Cardio_Trials_SS/Page2_Trends.png)

* **Clinical Trial Initiation Trend:** Area chart capturing study initiation momentum over time with date hierarchy drill-down.
* **Patient Enrollment Target:** Scale distribution across clinical phases.
* **Status Pipeline Breakdown:** Operational view of current active vs. completed studies.
* **Clinical Trial Distribution:** Geographic concentration visual highlighting top Spanish medical hubs.
* **Sponsor Filter:** Interactive slicer for dynamic filtering by funder type (Industry, NIH, Network, etc.).

---

### Project Architecture & Data Pipeline

```text
[ ClinicalTrials.gov (3,081 Rows) ]
               │
               ▼
   [ SQLite Data Ingestion ]
               │
               ├──> Step 1: Data Cleaning & Duration Calculation (Julianday)
               ├──> Step 2: Operational SQL Queries & Aggregations
               └──> Step 3: Location Engineering (Regex & Pattern Matching)
               │
               ▼
     [ Power BI Data Model ]
               │
               ├──> Star Schema: Fact Table linked 1-to-1 with Dimension Table (`location`)
               └──> Core DAX Measures (`_Key Metrics`)
               │
               ▼
[ Interactive 2-Page Power BI Executive Dashboard ]
