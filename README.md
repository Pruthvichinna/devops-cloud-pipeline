# 🚀 DevOps Cloud Deployment Pipeline using Jenkins, Docker, Kubernetes, Prometheus & Grafana

This project demonstrates a complete DevOps CI/CD pipeline to automate the building, testing, containerizing, and deployment of a Flask-based web application. It also includes real-time monitoring using Prometheus and visualization with Grafana — all running on a cloud-native Kubernetes environment such as GCP, AWS, or Azure.

---

## 🧠 Key Objectives

- Automate CI/CD using Jenkins
- Containerize the Flask app using Docker
- Deploy the app to a Kubernetes cluster
- Monitor infrastructure and app metrics using Prometheus
- Visualize data with Grafana dashboards

---

## 🧰 Tools and Technologies Used

| Tool         | Purpose                                  |
|--------------|------------------------------------------|
| GitHub       | Source control and webhook trigger       |
| Jenkins      | Orchestration of CI/CD pipeline          |
| Docker       | Containerization of applications         |
| Kubernetes   | Cluster orchestration and deployment     |
| Prometheus   | Monitoring services and metrics          |
| Grafana      | Dashboard and metric visualization       |
| Flask        | Python-based sample web app              |
| Cloud (GCP)  | Cloud environment to host infrastructure |

---

## 📁 Project Structure

```plaintext
devops-cloud-pipeline/
├── app/
│   ├── app.py               # Flask web app
│   ├── requirements.txt     # Python dependencies
│   └── Dockerfile           # Docker build instructions
│
├── jenkins/
│   └── Jenkinsfile          # CI/CD pipeline definition
│
├── k8s/
│   ├── deployment.yaml      # Kubernetes deployment config
│   └── service.yaml         # Kubernetes service definition
│
├── monitoring/
│   ├── prometheus.yaml      # Prometheus scrape config
│   └── grafana-dashboards/
│       └── dashboard.json   # Sample Grafana dashboard template
│
└── README.md                # Project documentation (this file)
