# 🚀 Databricks Lakehouse Project (Medallion Architecture)

This project demonstrates a **Databricks-based data pipeline** using the **Medallion Architecture (Bronze → Silver → Gold)** with **notebook orchestration**.

---

## 📌 Overview

- Built on Databricks Lakehouse
- Uses multiple notebooks for ETL pipeline
- Orchestrated using a master notebook
- Follows industry-standard Medallion Architecture

---

## 🏗️ Architecture

```
Source Data
    ↓
Bronze Layer (Raw Data)
    ↓
Silver Layer (Cleaned Data)
    ↓
Gold Layer (Business Data)
    ↓
Reporting / Analytics
```

---

## 🥉 Bronze Layer

- Raw data ingestion
- Stores source data as-is
- Supports reprocessing

**Examples:**
- CSV / JSON ingestion
- API data load

---

## 🥈 Silver Layer

- Data cleaning and transformation
- Handles:
  - Null values
  - Duplicates
  - Data type corrections

**Purpose:**
- Improve data quality
- Prepare for analytics

---

## 🥇 Gold Layer

- Business-level data
- Aggregations and KPIs
- Used for reporting and dashboards

---

## ⚙️ Pipeline Orchestration

A **master notebook** triggers all other notebooks sequentially.

### Example:

```python
notebooks = [
    "/Workspace/ETL/step1_ingestion",
    "/Workspace/ETL/step2_cleaning",
    "/Workspace/ETL/step3_transform",
    "/Workspace/ETL/step4_validation",
    "/Workspace/ETL/step5_aggregation",
    "/Workspace/ETL/step6_publish"
]

for nb in notebooks:
    result = dbutils.notebook.run(nb, 0, {"run_id": "123"})
    print(f"{nb} finished with result: {result}")
```

---

## 🔄 Execution Flow

1. Master notebook starts
2. Executes notebooks one by one
3. Waits for each to complete
4. Captures result
5. Moves to next step

---

## 📂 Project Structure

```
lakehouse_01/
│
├── notebooks/
│   ├── bronze/
│   ├── silver/
│   ├── gold/
│   └── orchestration/
│
├── data/
├── configs/
└── README.md
```

---

## 🛠️ Tech Stack

- Databricks
- Apache Spark
- Delta Lake
- Python
- Spark SQL

---

## ✅ Key Features

- Modular notebook design
- Scalable ETL pipeline
- Parameterized execution
- Delta Lake support (ACID, Time Travel)
- Easy orchestration using master notebook

---

## 🚦 How to Run

1. Open Databricks workspace
2. Navigate to master notebook
3. Run the notebook
4. Monitor execution in Jobs UI

---

## ⚠️ Error Handling (Recommended)

```python
for nb in notebooks:
    try:
        result = dbutils.notebook.run(nb, 0, {"run_id": "123"})
        print(f"{nb} success: {result}")
    except Exception as e:
        print(f"{nb} failed: {str(e)}")
        break
```

---

## 📈 Future Improvements

- Parallel execution
- Alerts & monitoring
- CI/CD integration
- Data quality framework
- Streaming pipeline support

---

## 👨‍💻 Author

Sai Ram

---

## ⭐ If you like this project

Give it a star ⭐ on GitHub
