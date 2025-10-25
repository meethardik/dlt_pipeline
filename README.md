# DLT Pipeline – Rapidly Evolving Schema (Azure Databricks)

This repository demonstrates a Delta Live Tables (DLT) pipeline for handling data sources whose schemas change multiple times per day.

## Structure
- `dlt_new_source.py` – Main DLT script (Bronze → Silver → Gold)
- `pipeline_settings.json` – DLT pipeline configuration (for Databricks UI/API)
- `schema_drift_monitor.py` – Job script for Slack-based schema drift alerts
- `uc_sql_bootstrap.sql` – Optional SQL bootstrap for column mapping + grants

## Setup Steps
1. Update the CONFIG section in `dlt_new_source.py` with your catalog/schema and ADLS paths.
2. Create a secret scope `notify` with a Slack webhook key `slack_webhook`.
3. In Databricks → Delta Live Tables → Create Pipeline → paste `pipeline_settings.json`.
4. Upload this repo to GitHub or to DBFS (`/Repos/<your-repo>/dlt_pipeline`).
5. Optionally schedule `schema_drift_monitor.py` as a Databricks Job every 30–60 minutes.

## License
MIT License.
