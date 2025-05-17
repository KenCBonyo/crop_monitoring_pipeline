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

## 📁 Project Structure

crop_monitoring_pipeline/
│
├── docker-compose.yaml # Main orchestration file
│
├── spark/
│ ├── jobs/ # PySpark scripts
│ ├── Dockerfile # Spark image with Sedona & Iceberg
│ └── requirements.txt # Python dependencies for Spark jobs
│
├── airflow/
│ ├── dags/ # Airflow DAGs
│ └── requirements.txt # Extra providers/plugins for Airflow
│
├── python_scripts/
│ ├── api_calls/ # Non-Spark scripts (e.g., API calls)
│ └── utils/ # Helper functions
│
├── postgres/
│ └── init.sql # Optional DB setup script
│
├── minio/ # Optional local S3 emulation
│
└── README.md # This file


---

## 🚀 Getting Started

### Prerequisites

- Docker Desktop installed
- Basic understanding of Docker, Spark, and Airflow

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/agri-pipeline.git 
cd crop_monitoring_pipeline
