# Machine Learning Operations (MLOps)

![CI - Lint and Test](https://github.com/DastanZar/MLOps_Project/actions/workflows/ci-test.yml/badge.svg)
![Python](https://img.shields.io/badge/python-3.9-blue)
![MLflow](https://img.shields.io/badge/MLflow-2.13.2-orange)
![Docker](https://img.shields.io/badge/docker-ready-blue)
![Kubernetes](https://img.shields.io/badge/kubernetes-EKS-326CE5)

## MLOps maturity level 4

## Overview :
This project implements a robust MLOps pipeline, facilitating the continuous integration, continuous deployment, and monitoring of machine learning models. The infrastructure leverages AWS, Kubernetes, and various open-source tools to ensure scalability, reproducibility, and maintainability.



## Architecture :

![Architecture](https://github.com/Chandru-21/MLOps_Project/assets/64595758/123511be-fe66-424d-8776-513b908840fe)

## Key Features :

**Data Versioning** : DVC

**Continuous Integration(CI)** : Triggered through `main.yml`, builds Docker image, runs Pytest, pushes to AWS ECR.

**Experiment Tracking / Model Versioning** : MLflow

**Continuous Deployment(CD)** : Deploys FastAPI in AWS EKS (Kubernetes) for real-time and batch predictions.

**Continuous Monitoring(CM)** : Integrating the `/metrics` endpoint of FastAPI in Prometheus and visualizes in Grafana.

**Continuous Training(CT)** : Triggers code execution through GitHub Actions when new data is pushed to the remote DVC location.

**Drift Monitoring** : Uses a Streamlit app to monitor data drift, target drift, and data quality checks via EvidentlyAI.

## Quick Start (Local Development)

See [CONTRIBUTING.md](./CONTRIBUTING.md) for full setup instructions.

```bash
# Start the full local stack
docker-compose up --build
```

| Service | URL |
|---|---|
| FastAPI app | http://localhost:8005 |
| FastAPI docs | http://localhost:8005/docs |
| MLflow UI | http://localhost:5000 |
| Prometheus | http://localhost:9090 |
| Grafana | http://localhost:3000 |

## Data Monitoring :

**Data Drift Monitoring** :

![Data Drift](https://github.com/Chandru-21/MLOps_Project/assets/64595758/af0df23d-9980-4ee4-94c0-ddebdb923237)

**Data Quality checks** :

![Data Quality](https://github.com/Chandru-21/MLOps_Project/assets/64595758/c1c62d64-9b69-4ca7-ba45-45ae226a7620)

## Continuous Monitoring (CM)

**Exposing `/metrics` on FastAPI to be connected to Prometheus** :

![FastAPI Metrics](https://github.com/Chandru-21/MLOps_Project/assets/64595758/09b18b44-8cb1-4a86-9172-c79082cb77c8)

**FastAPI integrated into Prometheus** :

![FastAPI Prometheus](https://github.com/Chandru-21/MLOps_Project/assets/64595758/4b21c089-bef3-4e39-b5e1-04cb8e026345)

**Monitoring FastAPI methods on Grafana** :

![Grafana FastAPI](https://github.com/Chandru-21/MLOps_Project/assets/64595758/930f0a9a-352f-41f9-8106-9b6735af8ce4)

**Monitoring Kubernetes cluster resources on Grafana** :

![Grafana K8s](https://github.com/Chandru-21/MLOps_Project/assets/64595758/d046d9f9-1477-4975-9041-f4aa128bb0f3)
