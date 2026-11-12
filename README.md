# UK Pharmaceutical Data Quality & Compliance Analytics

## Executive summary

This project simulates a UK pharmaceutical manufacturing
reporting environment for a fictional company, Britwell Pharma Ltd.

I built a reproducible SQL and Python workflow to identify missing,
duplicate, and inconsistent batch records. The outputs support
Excel-based QA review and Power BI reporting.

The data is synthetic. This project demonstrates analytical
controls and governance concepts, not validated GMP compliance.

## Business problem

QA and operations teams need reliable batch records to monitor
manufacturing performance and prioritize investigation.

The project assesses record completeness, duplicate batch IDs,
status validity, date consistency, yield validity, and agreement
between reported yield and batch quantities.

## Tools

- SQL: SQLite validation view
- Python: pandas, NumPy, sqlite3
- Excel: QA scorecard and investigation log
- Power BI: interactive quality dashboard
- GitHub: version control and documentation

## Dataset

The test dataset contains:

- 40 synthetic source records
- 38 distinct batch IDs
- Five fictional UK sites
- Six generic medicine names
- Deliberately injected data-quality issues

No real patient, company, or manufacturing data is included.

## Workflow

```text
Synthetic CSV
    ↓
SQLite staging table
    ↓
SQL validation view
    ↓
Python review and anomaly outputs
    ↓
Excel QA workbook and Power BI dashboard
```

## Key results

- 40 source records assessed.
- 11 records failed at least one validation rule.
- Invalid record rate: 27.50%.
- 4 records belonged to duplicate batch-ID groups.
- 12 individual rule failures were identified.
- 29 records passed validation.

A single record may fail more than one rule.

## Dashboard

![Data quality dashboard](images/data_quality_dashboard.png)

![Manufacturing dashboard](images/manufacturing_dashboard.png)

![Excel scorecard](images/excel_scorecard.png)

## Recommendations

- Review duplicate batch identifiers before reporting batch counts.
- Investigate yield values that disagree with batch quantities.
- Introduce a conditional release-date check for released batches.
- Separate data-quality issues from manufacturing rejection analysis.

## Limitations

- All data is synthetic.
- The 40-row dataset is designed to test controls, not establish
  operational trends.
- Validation thresholds are illustrative.
- IQR anomalies are investigation signals, not confirmed defects.
- The project is not a validated pharmaceutical system and does
  not establish regulatory compliance.

## How to run

1. Install dependencies:

```bash
python -m pip install -r requirements.txt
```

2. Place the synthetic CSV in:

```text
data/raw/uk_pharma_medicine_batches.csv
```

3. Run the pipeline:

```bash
python python/run_pipeline.py
```

4. Open:

```text
excel/britwell_qa_report.xlsx
```

5. Import processed CSVs into Power BI.
