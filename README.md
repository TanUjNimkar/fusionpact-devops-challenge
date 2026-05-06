Markdown

# 🔥 Fusionpact DevOps Challenge — Complete Solution

**Status:** ✅ Deployed on AWS | ✅ CI/CD Active | ✅ Monitoring Live  
**Submitted by:** Tanuj Nimkar  

---

## 🌐 LIVE DEMO (AWS EC2)

> **Public IP:** `13.201.95.39` (ap-south-1 Mumbai)

| Service | URL | Status |
|---------|-----|--------|
| **Frontend** | http://13.201.95.39:8080/Devops_Intern.html | ✅ Live |
| **Backend API** | http://13.201.95.39:8000 | ✅ Live |
| **Metrics (/metrics)** | http://13.201.95.39:8000/metrics | ✅ Live |
| **Prometheus** | http://13.201.95.39:9090 | ✅ Live |
| **Grafana Dashboard** | http://13.201.95.39:3000 | ✅ Live |

### 📸 Cloud Verification Screenshots

**Backend API Running on Public IP:**
![Backend API](images/backend-api.png)

**Prometheus Metrics Output:**
![Metrics](images/metrics.png)

---

## 📋 What This Project Does

Transforms a basic two-tier app (HTML frontend + Python FastAPI backend) into production-ready DevOps stack:

1. **Containerization:** Docker + Docker Compose (4 services)
2. **Data Persistence:** Volumes survive restarts (tested & proved)
3. **Monitoring:** Prometheus scrapes `/metrics` → Grafana shows real-time dashboards
4. **CI/CD:** GitHub Actions auto-tests every push (all 5 services checked)
5. **Cloud:** Deployed live on AWS EC2 public instance

---

## 🛠 Tech Stack Used

Frontend → Nginx (Alpine) Port: 8080
Backend → Python/FastAPI Port: 8000
Monitoring → Prometheus + Grafana Port: 9090, 3000
Orchestration → Docker Compose v2
CI/CD → GitHub Actions (Ubuntu runner)
Cloud → AWS EC2 t2.micro (Free Tier)

text


---

## 📁 Project Structure

fusionpact-devops-challenge/
│
├── .github/workflows/
│ └── main.yml ← CI/CD Pipeline
│
├── backend/
│ ├── Dockerfile ← FastAPI image
│ ├── requirements.txt ← Dependencies
│ └── app/
│ └── main.py ← Code with /metrics endpoint
│
├── frontend/
│ ├── Dockerfile ← Nginx image
│ └── Devops_Intern.html ← Landing page
│
├── monitoring/
│ └── prometheus.yml ← Scrape config
│
├── images/ ← Documentation screenshots
│ ├── backend-api.png
│ ├── metrics.png
│ ├── grafana-dashboard.png
│ ├── cicd-success.png
│ └── aws-security.png
│
├── docker-compose.yml ← All services + volume
└── README.md ← This file

text


---

## ☁️ Cloud Deployment (AWS)

**Infrastructure:** Amazon Web Services  
**Region:** ap-south-1 (Mumbai)  
**Instance:** t2.micro (Free Tier eligible)

**AWS Security Group Configuration:**
![Security Group](images/aws-security.png)

**Deployment Steps:**
```bash
# Connect via SSH
ssh -i "key.pem" ubuntu@ec2-13-201-95-39.ap-south-1.compute.amazonaws.com

# Install Docker
sudo apt update && sudo apt install docker.io docker-compose-v2 -y

# Deploy app
git clone https://github.com/TanUjNimkar/fusionpact-devops-challenge.git
cd fusionpact-devops-challenge
docker compose up -d --build

🚀 Local Quick Start

Bash

git clone https://github.com/TanUjNimkar/fusionpact-devops-challenge.git
cd fusionpact-devops-challenge

docker compose up --build -d

# Access locally:
# Frontend:   http://localhost:8080/Devops_Intern.html
# Backend:    http://localhost:8000
# Metrics:    http://localhost:8000/metrics
# Prometheus: http://localhost:9090
# Grafana:    http://localhost:3000 (admin/admin)

docker compose down  # Stop when done

📊 Level 2 — Monitoring Setup
Prometheus Configuration

    Scrape Interval: Every 5 seconds
    Target: backend:8000/metrics
    Captures: Request counts, CPU, Memory, Latency histograms

Grafana Dashboard

Real-time visualizations created:

Grafana Dashboard

Panels included:

    Stat/Gauge views: Large numbers showing request counts (44, 342 visible)
    Bar Charts: Distribution comparison (green=healthy, red=high volume /metrics traffic)
    Pie/Donut charts: Status code breakdowns (80% / 10% / 10% split)
    Time Series: Real-time trend lines

Data Source: Prometheus (auto-discovered via Docker network at http://prometheus:9090)
🔁 Level 3 — CI/CD Automation

Trigger: Push to main branch

Pipeline Workflow:
✅ Checkout code
✅ Build Docker images (4 containers)
✅ Start all services (15s bootup delay)
✅ Test Backend API (curl localhost:8000)
✅ Test Metrics (curl localhost:8000/metrics)
✅ Test Frontend (curl localhost:8080)
✅ Test Prometheus (curl localhost:9090)
✅ Test Grafana (curl localhost:3000)
✅ Cleanup (runs always even if failure)

Latest Result:

CI/CD Success

GitHub Actions "update ci cd pipeline with service checks" — Success in 1m 14s
💾 Data Persistence Proof

Method: Named volume backend_data mounted at /app/app/data

Test:

Bash

# Inside running container
docker exec -it backend-1 sh
cd app/data
echo "hello devops" > test.txt
ls   # Shows: info.txt test.txt
exit

# Destroy everything
docker compose down

# Restart fresh
docker compose up

# Check again
docker exec -it backend-1 sh
cd app/data
ls   # STILL SHOWS: info.txt test.txt ✅

Result: Data survives container destruction.
⚠️ Challenges Faced

    FastAPI Path Error: Used main:app instead of app.main:app (nested folder structure)
    YAML Indentation: Accidentally put services under volumes: block (30 min debug!)
    Docker PATH (Windows): System restart needed after install
    SSH Permissions: Windows ACL fix required (icacls)
    Grafana Empty Graphs: Needed to generate traffic first before metrics appeared
    CI/CD Timing: Increased sleep from 5s→15s for slow-starting monitoring containers

✅ Requirements Checklist
Criteria	Status	Evidence
Containerization	✅ Done	Dockerfiles in repo
docker-compose.yml	✅ Done	Volumes + 4 services
Data Persistence	✅ Proved	test.txt survives restart
Cloud Deployment	✅ Done	AWS EC2 @ 13.201.95.39
Publicly Accessible	✅ Verified	All URLs open via public IP
Prometheus Scraping	✅ Working	Targets show UP
Grafana Dashboards	✅ Created	Gauges, Bars, Pies, Tables
CI/CD Pipeline	✅ Running	2 successful workflow runs
📧 Submission Info

Repository: https://github.com/TanUjNimkar/fusionpact-devops-challenge
SOP Document: Attached PDF (separate email attachment)
Contact: vaishali.yadav@fusionpact.com

Build Date: May 6, 2026
Candidate: Tanuj NImkar