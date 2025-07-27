# Spotify ETL Pipeline with AWS Lambda, Glue & Snowflake

![ETL Pipeline](https://img.shields.io/badge/ETL-Pipeline-blue) 
![AWS](https://img.shields.io/badge/AWS-Lambda%20%7C%20Glue%20%7C%20S3-orange)
![Snowflake](https://img.shields.io/badge/Snowflake-Data%20Warehouse-blue)

An end-to-end data pipeline that extracts Spotify playlist data, transforms it using PySpark, and loads it into Snowflake for analytics.

## 🚀 Features

- **Real-time data extraction** from Spotify API using AWS Lambda
- **Scalable data processing** with AWS Glue (PySpark)
- **Automated Snowflake ingestion** using Snowpipe
- **Partitioned storage** in S3 for optimized querying
- **Modular transformation logic** for albums, artists, and songs

## 📊 Architecture

```mermaid
graph LR
    A[Spotify API] -->|Extract| B[AWS Lambda]
    B -->|Raw JSON| C[S3 Raw Zone]
    C -->|Trigger| D[AWS Glue Job]
    D -->|Transformed Data| E[S3 Processed Zone]
    E -->|Auto-Ingest| F[Snowflake via Snowpipe]
    F --> G[Analytics/BI Tools]
