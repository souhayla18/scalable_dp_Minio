# Scalable Data Engineering Pipeline with Kafka, Craft, Spark, and Docker

## Overview
This project implements a robust data engineering pipeline for ingesting, processing, and storing data, utilizing AWS Lambda, Craft (for Kafka management), Apache Spark, and Docker for containerized deployment. The pipeline supports both real-time and batch data processing needs.

## Architecture
![Data Engineering Pipeline Architecture](images/minioArch.jpg)

## Key Components

1. **Data Ingestion**:
   - **Python Scripts / API / File Loader**: Supports ingestion from various sources.
   - **AWS Lambda**: Event-driven functions listen for new data and trigger ingestion in real time.

2. **Data Stream Management**:
   - **Kafka**: Manages data streaming to ensure consistent data flow.
   - **Craft (Kafka Metadata Manager)**: Acts as a zookeeper-like manager, handling metadata, data cataloging, and stream coordination.
   - **Schema Registry**: Maintains schema consistency across data consumers.
   - **Control Center**: Provides a dashboard for managing Kafka and Craft streams.

3. **Data Processing**:
   - **Apache Spark**: Processes data through stages:
     - **Bronze Layer**: Raw data.
     - **Silver Layer**: Structured, cleaned data.
     - **Gold Layer**: Aggregated data for analytics and reporting.

4. **Data Serving**:
   - **Cassandra**: Stores processed data, optimizing it for fast querying and analysis.
   - **Slack**: Sends real-time updates and alerts to team members.

5. **Containerization with Docker**:
   - **Docker**: Containers are used to package and deploy services across the pipeline consistently, making it easy to manage dependencies, scale services, and deploy on various environments.

## Data Flow Architecture

1. **Data Ingestion**:
   - Data is ingested using **Python scripts**, API calls, or file loaders.
   - **AWS Lambda** listens for events, triggering ingestion for real-time data capture.

2. **Data Stream Management with Kafka and Craft**:
   - **Kafka** manages data streaming, ensuring seamless data flow.
   - **Craft** (a zookeeper-like metadata manager) coordinates data streams and handles data cataloging.
   - **Schema Registry** enforces schema consistency across consumers.
   - **Control Center** enables visibility into the data streams.

3. **Data Processing with Spark**:
   - **Bronze Layer**: Raw data.
   - **Silver Layer**: Cleaned and enriched data.
   - **Gold Layer**: Aggregated, analytics-ready data.

4. **Data Serving**:
   - **Cassandra** is used for fast querying of structured data.
   - **Slack** notifies the team with real-time insights.

5. **Containerization with Docker**:
   - Docker containers encapsulate services like **Kafka**, **Craft**, **Spark**, and **Cassandra**, ensuring consistent environments and simplified deployment.

## Benefits
- **Scalability**: Kafka, Craft, and Docker ensure efficient scaling of data flows and services.
- **Reliability**: AWS Lambda and Kafka provide robust data streaming.
- **Flexibility**: The modular, containerized design allows for easy integration of new data sources.
- **Performance**: Layered processing and optimized querying enhance performance.

## Future Enhancements
- **Machine Learning**: Integrate models for advanced predictive analytics.
- **Real-Time Expansion**: Further enhance real-time capabilities.
- **Data Governance**: Implement policies for data quality and security.
- **Advanced Analytics**: Apply data mining and machine learning for deeper insights.

## Repository Structure

```plaintext
data-engineering-pipeline/
├── README.md                 # Project overview
├── src/                      # Source code
│   ├── ingestion/            # Python scripts, API calls, file loaders
│   ├── streaming/            # Kafka and Craft configuration
│   ├── processing/           # Spark scripts (bronze, silver, gold layers)
│   ├── serving/              # Cassandra and Slack integration
│   └── utils/                # Helper functions
├── dags/                     # Airflow DAGs
├── config/                   # Kafka, Craft, schema registry settings
├── docker/                   # Dockerfiles and Docker Compose for containerized setup
├── images/                   # Project images (e.g., architecture.png)
└── docs/                     # Additional documentation
