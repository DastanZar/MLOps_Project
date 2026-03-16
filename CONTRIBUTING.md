# Contributing to MLOps_Project

Thank you for your interest in this MLOps Loan Prediction project!

## Local Development Setup

### Prerequisites
- Python 3.9+
- Docker & Docker Compose
- Git
- AWS CLI (for cloud deployment only)

### 1. Clone the Repository

```bash
git clone https://github.com/Chandru-21/MLOps_Project.git
cd MLOps_Project
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Environment Variables

```bash
cp .env.example .env
# Edit .env with your actual values
```

### 5. Run MLflow Server Locally

```bash
mlflow server --host 0.0.0.0 --port 5000 --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./mlruns
```

### 6. Run the FastAPI Application

```bash
uvicorn main:app --host 0.0.0.0 --port 8005 --reload
```

Access the API docs at: http://localhost:8005/docs

### 7. Run Tests

```bash
pytest tests/ -v
```

### 8. Run with Docker Compose (Full Stack)

```bash
docker-compose up -d
```

This starts:
- FastAPI app at http://localhost:8005
- MLflow at http://localhost:5000
- Prometheus at http://localhost:9090
- Grafana at http://localhost:3000 (admin/grafana)

## Project Structure

```
MLOps_Project/
├── .dvc/                    # DVC configuration for data versioning
├── .github/workflows/       # CI/CD GitHub Actions workflows
├── drift_monitoring/        # Streamlit app for data/target drift (EvidentlyAI)
├── monitoring/              # Prometheus configuration
├── prediction_model/        # Core ML model: training, config, preprocessing
│   ├── config.py            # Project configuration (paths, features, model params)
│   ├── predict.py           # Inference functions
│   ├── pipeline/            # Training pipeline
│   └── processing/          # Data preprocessing transforms
├── tests/                   # Pytest test suite
├── main.py                  # FastAPI application entry point
├── Dockerfile               # Container definition
├── docker-compose.yml       # Local full-stack orchestration
├── deployment.yml           # Kubernetes Deployment manifest
├── service.yml              # Kubernetes Service manifest
└── requirements.txt         # Python dependencies
```

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Health check |
| `/prediction_api` | POST | Single prediction via JSON |
| `/prediction_ui` | POST | Single prediction via form params |
| `/batch_prediction` | POST | Batch prediction via CSV upload |
| `/metrics` | GET | Prometheus metrics endpoint |
