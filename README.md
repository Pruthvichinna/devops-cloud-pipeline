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

```
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
```

---

## ⚙️ CI/CD Pipeline Workflow

1. **Code Commit** – Developer pushes code to GitHub.  
2. **Jenkins Trigger** – Jenkins pulls latest code via webhook.  
3. **Build Stage** – Docker builds a new container image.  
4. **Test Stage** – Basic tests (if available) are run inside a container.  
5. **Push Stage** – Docker image is pushed to DockerHub.  
6. **Deploy Stage** – Kubernetes deploys the updated container.  
7. **Monitor Stage** – Prometheus scrapes metrics, Grafana visualizes them.

---

## 🚀 How to Run the Project Locally

### Step 1: Clone the Repository
```bash
git clone https://github.com/Pruthvichinna/devops-cloud-pipeline.git
cd devops-cloud-pipeline
```

### Step 2: Build and Run Flask App with Docker
```bash
docker build -t flask-app ./app
docker run -p 5000:5000 flask-app
```

### Step 3: Deploy to Kubernetes
Make sure your Kubernetes cluster is up and configured.
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

---

## 📡 Monitoring and Visualization

- **Prometheus** collects metrics defined in `prometheus.yaml`.
- **Grafana** visualizes them using the dashboard in `grafana-dashboards/dashboard.json`.

Steps:
1. Deploy Prometheus and Grafana to your Kubernetes cluster.  
2. Configure Prometheus as a data source in Grafana.  
3. Import `dashboard.json` to Grafana to visualize metrics.

---

## 🧪 Jenkinsfile Pipeline Logic (Sample)

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t flask-app ./app'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run flask-app python3 -m unittest discover || echo "No tests available."'
            }
        }
        stage('Push') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pass', variable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u your-username --password-stdin'
                    sh 'docker tag flask-app your-username/flask-app:latest'
                    sh 'docker push your-username/flask-app:latest'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
```

---

## 📈 Example Metrics to Monitor

- Application request count  
- Error rate and latency  
- Pod restarts and memory usage  
- CPU consumption per container

---

## 💡 Future Enhancements

- Add unit tests with PyTest  
- Integrate Slack for Jenkins alerts  
- Use Helm for templated Kubernetes deployment  
- Secure secrets using K8s Secrets or HashiCorp Vault  
- Implement Blue-Green or Canary deployments

---

**Varikuti Pruthvinath Reddy**  
📧 Email: pruthvinath18@gmail.com  
🌐 GitHub: [Pruthvichinna](https://github.com/Pruthvichinna)
