# DigitalXC Data Analyst Coding Challenge – End-to-End Solution

This repository presents a complete solution to the Data Analyst challenge provided by DigitalXC. It includes end-to-end data engineering and analytics pipeline development using:

- Apache Airflow
- DBT (Data Build Tool)
- PostgreSQL
- Apache Superset

---

## 📂 Repository Structure


---

## 🛠 Tech Stack Used

- **PostgreSQL** for data storage.
- **DBT** for data transformation and modeling.
- **Apache Airflow** to orchestrate the pipeline.
- **Apache Superset** for building interactive dashboards.

---

## 🧱 DBT Models

- `stg_cleaned_tickets.sql`: Cleans and formats the raw data.
- `dim_date_parts.sql`: Extracts Year, Month, Day from the Created Date.
- `fct_avg_resolution.sql`: Calculates average resolution time by Category and Priority.
- `fct_closure_rate.sql`: Computes closure rate by Assigned Group.
- `fct_monthly_summary.sql`: Summarizes monthly metrics.

✔️ Detailed SQL code and logic are included in the `1. Data Cleaning & Transformation (DBT).docx`.

---

## 🗂 Airflow DAG

The DAG named `itsm_pipeline.py` is responsible for:
1. Ingesting CSV into PostgreSQL.
2. Running DBT models.
3. Validating transformation completion.

⏱ The DAG is scheduled to run **daily** (`@daily`).

📄 DAG code and explanation provided in `2. Workflow Orchestration (Apache Airflow).docx`.

---

## 📊 Superset Dashboard

Built in Apache Superset and exported as `dashboard_export.json`, the dashboard includes:
- **Line Chart** – Daily ticket volume trends.
- **Bar Chart** – Avg. resolution time by category.
- **Pie Chart** – Closure rate by assigned group.
- **Table** – Ticket backlog by priority.
- **Filters** – Week, Category, Priority.

📄 See `3. Dashboard & Visualisation (Superset).docx` for layout and explanation.

---

## 🚀 How to Run Locally

### 1. PostgreSQL
- Create a DB `itsm`
- Load `ticket_dump.csv` into a table `raw_tickets`

### 2. DBT
```bash
cd dbt_project
dbt run

