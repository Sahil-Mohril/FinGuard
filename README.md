FinGuard — Real-Time Financial Fraud Detection Platform

FinGuard is a real-time financial fraud detection pipeline built on Databricks, combining streaming and batch data sources to detect fraudulent transactions as they happen. It leverages PySpark Structured Streaming, Delta Lake, Lakeflow Declarative Pipelines, Unity Catalog, and Lakeflow Jobs to deliver a governed, production-grade lakehouse architecture with real-time alerting and dashboards.

Architecture Overview

<img width="1447" height="736" alt="Gemini_Generated_Image_l8x6wnl8x6wnl8x6" src="https://github.com/user-attachments/assets/4081590a-7fd5-4b28-80d1-578e0e03f7ec" />

The pipeline follows a Medallion (Bronze → Silver → Gold) architecture on Delta Lake, with dedicated layers for ingestion, processing, orchestration, governance, and consumption.

1. Data Sources
Streaming Sources
Kafka — real-time transaction event stream
Streaming Files (JSON) — file-based streaming data
Batch Source
PostgreSQL — historical/reference data (e.g., customer, account master data)
2. Ingestion
Streaming Ingestion: Spark Structured Streaming + Auto Loader for scalable, schema-evolving ingestion of streaming sources
Batch Ingestion: Lakeflow Connect for reliable batch ingestion from PostgreSQL
3. Data Processing (Core Pipeline)
Lakeflow Declarative Pipelines (built on Apache Spark) to define and manage transformation logic declaratively
Stream-Stream Join — correlates events across multiple real-time streams
Stream-Static Join — enriches streaming transactions with reference/dimension data
Fraud Detection — applies rules/ML logic to flag suspicious transactions in real time
Delta Lake Medallion Layers:
Bronze — raw ingested data
Silver — cleaned, joined, and enriched data
Gold — aggregated, business-ready data for consumption
4. Orchestration
Lakeflow Jobs — orchestrates and schedules the end-to-end pipeline, coordinating ingestion, processing, and downstream delivery
5. Governance
Unity Catalog — centralized data governance, access control, lineage, and auditing across all layers
6. Consumption
Realtime Alerts — instant notifications for detected fraudulent activity
Dashboard — visual monitoring and analytics for fraud trends and system health
Tech Stack
Category	Tools/Technologies
Streaming	Kafka, Spark Structured Streaming, Auto Loader
Batch Ingestion	Lakeflow Connect, PostgreSQL
Processing	PySpark, Lakeflow Declarative Pipelines
Storage	Delta Lake (Bronze/Silver/Gold)
Orchestration	Lakeflow Jobs
Governance	Unity Catalog
Platform	Databricks
Consumption	Real-time alerting, Dashboards
Key Features
End-to-end real-time fraud detection combining streaming and batch data
Stream-stream and stream-static joins for contextual transaction enrichment
Medallion architecture ensuring data quality and reliability at each stage
Centralized governance and access control via Unity Catalog
Automated orchestration and monitoring via Lakeflow Jobs
Real-time alerting and dashboarding for fraud analysts
Project Status

Author
Sahil Mohril
