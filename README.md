# Spotify ETL Pipeline with AWS Lambda, Glue & Snowflake

An end-to-end data pipeline that extracts Spotify playlist data, transforms it using PySpark, and loads it into Snowflake for analytics.

## Features

- **Real-time data extraction** from Spotify API using AWS Lambda
- **Scalable data processing** with AWS Glue (PySpark)
- **Automated Snowflake ingestion** using Snowpipe
- **Partitioned storage** in S3 for optimized querying
- **Modular transformation logic** for albums, artists, and songs
- **Data quality checks** with PySpark validations
- **Time-based partitioning** for efficient data management

## Architecture Deep Dive

```mermaid
graph TD
    A[Spotify API] -->|OAuth2.0 API Calls| B[AWS Lambda]
    B -->|Raw JSON| C[S3 Raw Zone<br>/raw/to_process/]
    C -->|S3 Event Notification| D[AWS Glue Job]
    D -->|Spark Processing| E[Data Validation]
    E -->|Clean Data| F[S3 Processed Zone<br>/processed/albums/<br>/processed/artists/<br>/processed/songs/]
    F -->|Snowpipe Auto-Ingest| G[Snowflake<br>ANALYTICS.SPOTIFY]
    
