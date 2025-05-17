# 🌾 Crop Monitoring Data Pipeline

> A scalable and optimized geospatial data pipeline using Apache Spark (with Sedona), Iceberg, Docker, Airflow, and AWS S3 (or MinIO). Designed for efficient crop monitoring via LST, GDD, and Sentinel-2 indices.

---

## 🧩 Overview

This project is designed to:

1. Retrieve **polygon boundaries** from a PostgreSQL database.
2. Fetch **Land Surface Temperature (LST)** data from the Visual Crossing API.
3. Calculate **Growing Degree Days (GDD)** for crop stage estimation.
4. Query **Sentinel-2 indices** (e.g., NDVI, NDWI) via CropHelp API based on crop stages.
5. Store all results in **Iceberg tables** for scalable analytics.
6. Orchestrate the workflow using **Apache Airflow**.
7. Containerized with **Docker Compose** for easy deployment and scaling.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **PySpark + Sedona** | Distributed processing of geospatial data |
| **Iceberg** | High-performance table format stored in S3/MinIO |
| **Airflow** | Workflow orchestration and scheduling |
| **PostgreSQL** | Source of polygon and metadata |
| **MinIO** | Local S3-compatible storage (dev/test alternative to AWS S3) |
| **Docker / Docker Compose** | Containerization and service orchestration |

---
---

## 🚀 Getting Started

### Prerequisites

- Docker Desktop installed
- Basic understanding of Docker, Spark, and Airflow
- git clone https://github.com/KenCBonyo/crop_monitoring_pipeline.git
- cd crop_monitoring_pipeline


### 1. Clone the repo


## 📁 Project Structure
---
```bash
crop_monitoring_pipeline/
│
├── docker-compose.yaml              # Main orchestration file (Docker services)
│
├── spark/                           # Spark-related files
│   ├── jobs/                        # PySpark scripts (e.g., extract_polygons.py)
│   ├── Dockerfile                   # Custom Spark image with Sedona & Iceberg
│   └── requirements.txt             # Python dependencies for Spark jobs
│
├── airflow/                         # Apache Airflow configuration
│   ├── dags/                        # DAG definitions (e.g., main_pipeline_dag.py)
│   └── requirements.txt             # Extra providers/plugins for Airflow (e.g., Postgres, HTTP)
│
├── python_scripts/                  # Non-Spark logic
│   ├── api_calls/                   # Scripts for external APIs (e.g., Visual Crossing, CropHelp)
│   └── utils/                       # Helper functions and shared utilities
│
├── postgres/                        # PostgreSQL

---

DATA LAYER (external)                # Not stored in the repo
│
├── HDFS                             # Distributed file system (Hadoop cluster)
├── S3 / MinIO                         # Cloud/object storage (Iceberg tables, Parquet files)
├── PostgreSQL (EC2)                 # Source of polygons and metadata
└── Local disk (optional dev env)    # For testing with small datasets
