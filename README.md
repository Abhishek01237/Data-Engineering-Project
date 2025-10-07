# Databricks Medallion Architecture Pipeline

An end-to-end data engineering pipeline built entirely on Databricks, following the Medallion Architecture (Bronze–Silver–Gold) design pattern.
This project demonstrates scalable, maintainable, and production-ready Delta Lake pipelines using Databricks Autoloader, Delta Live Tables (DLT), and PySpark.

 **Goal**: To design a robust and automated data pipeline that ingests raw data, applies transformations, and delivers enriched analytical datasets — the modern lakehouse way.

 **Dataset**

The project uses simulated transactional and dimensional datasets representing a retail/sales scenario ( customers, orders, products, and sales).
These datasets are processed through three medallion layers to illustrate incremental data refinement and business-ready analytics.

🛠️ Tech Stack
Layer	Tools / Tech
Ingestion	Databricks Autoloader
Transformation	Delta Live Tables (DLT), PySpark
Storage	Delta Lake (Bronze, Silver, Gold)
Orchestration	Databricks Workflows
Compute	Databricks Cluster (SQL + Spark)
🧩 Architecture Overview
            ┌────────────────────────────────────────┐
            │              Source Data               │
            │     (Raw files, JSON, CSV, etc.)       │
            └────────────────────────────────────────┘
                              │
                              ▼
                ┌────────────────────────────┐
                │  Bronze Layer (Raw Zone)   │
                │  → Data Ingested via       │
                │    Databricks Autoloader   │
                └────────────────────────────┘
                              │
                              ▼
                ┌────────────────────────────┐
                │  Silver Layer (Clean Zone) │
                │  → Delta Live Tables (DLT) │
                │  → Data validation & joins │
                └────────────────────────────┘
                              │
                              ▼
                ┌────────────────────────────┐
                │  Gold Layer (Enriched Zone)│
                │  → Business logic & SCDs   │
                │  → Aggregations & lookups  │
                └────────────────────────────┘
                              │
                              ▼
                   📊 Analytics / BI Layer

⚙️ Pipeline Stages
1. Ingestion – Bronze Layer

Used Databricks Autoloader for incremental data ingestion from cloud storage.

Automatically detects and processes new files.

Writes data in Delta format for schema evolution and reliability.

2. Transformation – Silver Layer

Built with Delta Live Tables (DLT) for declarative, fault-tolerant transformations.

Applied cleaning, normalization, and standardization logic.

Managed schema enforcement and data quality at scale.

3. Enrichment – Gold Layer

Developed business-ready tables with joins, lookups, and aggregations.

Implemented Slowly Changing Dimensions (SCD Type 2) to maintain historical accuracy.

Created curated datasets for downstream analytics and dashboards.

📘 Key Learnings

Designed and implemented the Medallion Architecture using native Databricks capabilities.

Leveraged Autoloader for efficient, incremental ingestion.

Automated transformation logic through DLT pipelines.

Applied data modeling and SCD concepts using PySpark.

Created an extendable framework for enterprise-grade data processing.

🚀 Future Enhancements

Integrate with Unity Catalog for governance and lineage.

Schedule and monitor jobs via Databricks Workflows.

Expose Gold datasets to Power BI or Tableau for analytics.

Add CI/CD automation for DLT pipelines using GitHub Actions.

📄 Repository Structure
databricks-medallion-architecture/
│
├── notebooks/
│   ├── bronze_ingestion_autoloader.ipynb
│   ├── silver_dlt_transformation.ipynb
│   └── gold_enrichment_scd.ipynb
│
├── configs/
│   ├── autoloader_config.json
│   └── dlt_pipeline_settings.json
│
├── resources/
│   └── sample_data/
│
└── README.md


💡 Inspired by the Databricks Lakehouse paradigm, this project showcases a clean, modular, and production-friendly way to build modern data pipelines with minimal overhead.
