🔥 Fusionpact DevOps Challenge — Complete Solution

Status: ✅ Deployed on AWS | ✅ CI/CD Active | ✅ Monitoring Live  
Submitted by: Tanuj Nimkar  

---

## 🌐 LIVE DEMO (AWS EC2)

Public IP: 13.201.95.39 (ap-south-1 Mumbai)

| Service | URL | Status |
|---------|-----|--------|
| Frontend | http://13.201.95.39:8080/Devops_Intern.html | ✅ Live |
| Backend API | http://13.201.95.39:8000 | ✅ Live |
| Metrics (/metrics) | http://13.201.95.39:8000/metrics | ✅ Live |
| Prometheus | http://13.201.95.39:9090 | ✅ Live |
| Grafana Dashboard | http://13.201.95.39:3000 | ✅ Live |

---

## 📋 What This Project Does

This takes a basic two-tier app (HTML frontend + Python FastAPI backend) and turns it into a full production-ready DevOps stack:

1. Containerization: Docker + Docker Compose (4 services running together)
2. Data Persistence: Docker volumes survive container restarts (tested & proved)
3. Monitoring: Prometheus scrapes backend /metrics → Grafana shows real-time dashboards
4. CI/CD: GitHub Actions auto-tests every push (Backend, Frontend, Prometheus, Grafana checks)
5. Cloud: Deployed live on AWS EC2 public instance

---

## 🛠 Tech Stack Used

Frontend    → Nginx (Alpine container)        Port: 8080
Backend     → Python/FastAPI                   Port: 8000 
Monitoring  → Prometheus + Grafana             Port: 9090, 3000
Orchestration → Docker Compose v2
CI/CD       → GitHub Actions (Ubuntu runner)
Cloud       → AWS EC2 t2.micro (Free Tier)

---

## 📁 Project Structure

fusionpact-devops-challenge/
│
├── .github/workflows/
│   └── main.yml                    ← CI/CD Pipeline definition
│
├── backend/
│   ├── Dockerfile                  ← Builds FastAPI image
│   ├── requirements.txt            ← pip dependencies
│   └── app/
│       └── main.py                 ← API code with /metrics endpoint
│
├── frontend/
│   ├── Dockerfile                  ← Builds Nginx image
│   └── Devops_Intern.html          ← Landing page HTML
│
├── monitoring/
│   └── prometheus.yml              ← Scrape configuration
│
├── docker-compose.yml              ← Orchestrates all services + volume
└── README.md                       ← You are here :)

---

## 🚀 How to Run This Locally

git clone https://github.com/TanUjNimkar/fusionpact-devops-challenge.git
cd fusionpact-devops-challenge

# Start everything
docker compose up --build --d

# Open in browser (localhost versions):
# Frontend:   http://localhost:8080/Devops_Intern.html
# Backend:    http://localhost:8000
# Metrics:    http://localhost:8000/metrics
# Prometheus: http://localhost:9090
# Grafana:    http://localhost:3000 (login: admin/admin)

# Stop when done
docker compose down

---

## ☁️ Cloud Deployment Details

Platform: Amazon Web Services (AWS)
Region: ap-south-1 (Mumbai)
Instance Type: t2.micro (Free Tier eligible)
Security Group: Ports opened for 8080, 3000, 9090, 8000, 22

How deployed:
1. Launched Ubuntu 22.04 LTS EC2 instance
2. Connected via SSH key pair authentication
3. Installed Docker: sudo apt install docker.io docker-compose-v2
4. Cloned repo: git clone https://github.com/TanUjNimkar/fusionpact-devops-challenge.git
5. Ran: docker compose up -d --build
6. Verified all services accessible via public IP 13.201.95.39

---

## 📊 Level 2 – Monitoring Setup

Prometheus Configuration (monitoring/prometheus.yml):
- Scrape interval: Every 5 seconds
- Target: backend:8000 (/metrics endpoint)
- Captures: Request counts, CPU usage, Memory consumption, Latency histograms

Grafana Dashboard:
- Data Source: Prometheus (auto-discovered via docker network)
- Panels created:
  - Stat/Gauge views: Large number displays (44, 342 request counts visible)
  - Bar Charts: Request distribution comparison
  - Time Series: Real-time metric graphs
  - Pie/Donut charts: Status code breakdowns (80% / 10% / 10% split)

---

## 🔁 Level 3 – CI/CD Automation

Trigger: Every push to main branch automatically runs tests

Pipeline Steps:
✅ Checkout code
✅ Build Docker images (Backend + Frontend + Monitoring stack)
✅ Start all containers (wait 15 seconds for bootup)
✅ Test Backend API (curl localhost:8000)
✅ Test Metrics Endpoint (curl localhost:8000/metrics)
✅ Test Frontend Page (curl localhost:8080)
✅ Test Prometheus (curl localhost:9090)
✅ Test Grafana Dashboard (curl localhost:3000)
✅ Cleanup containers (always runs even if failure)

---

## 💾 Data Persistence Proof

Method: Docker named volume (backend_data) mounted at /app/app/data inside backend container

Test conducted:
1. Executed into running container → navigated to /app/app/data
2. Created test file: echo "hello devops" > test.txt
3. Verified file existed: ls showed test.txt present
4. Destroyed all containers: docker compose down
5. Restarted fresh: docker compose up
6. Checked again: File still persisted! Volume works correctly.

---

## ⚠️ Challenges Faced & Solutions

1. FastAPI Import Path Error
   - Tried: uvicorn main:app → Failed (module not found)
   - Fix: uvicorn app.main:app (code is nested in app/ folder)

2. YAML Indentation Disaster
   - Accidentally placed services under volumes: block in docker-compose.yml
   - Fixed by checking indentation carefully (YAML is strict!)

3. Docker PATH Issue (Windows)
   - After installing Docker Desktop, docker command not recognized
   - Fixed by restarting system

4. SSH Permissions (AWS)
   - Got Bad permissions error on Windows when using .pem file
   - Fixed using icacls command

5. Grafana Empty Graphs Initially
   - Dashboard showed no data at first
   - Had to generate traffic first (refreshed /metrics multiple times), then data appeared

6. CI/CD Timing
   - First pipeline failed with only 5-second sleep (containers not ready yet)
   - Increased to 15 seconds + added Grafana/Prometheus specific health checks

---

## ✅ Requirements Checklist

Requirement                           Status   Evidence
Containerization (Dockerfiles)        ✅ Done    In repo
docker-compose.yml                     ✅ Done    With volumes + monitoring
Data Persistence                       ✅ Proved  test.txt survives restart
Cloud Deployment                      ✅ Done    AWS EC2 @ 13.201.95.39
Publicly Accessible                    ✅ Done    All 5 URLs open via public IP
Prometheus Scraping                   ✅ Working Targets show UP
Grafana Dashboards                    ✅ Created Multiple visualization types
CI/CD Pipeline                        ✅ Running 2 successful workflows in Actions

---

## 📧 Submission Info

GitHub Repository: https://github.com/TanUjNimkar/fusionpact-devops-challenge
SOP Document: Attached separately as PDF
Email Sent To: vaishali.yadav@fusionpact.com
Google Form: Submitted

---

Build Date:6th May 2026
Candidate: Tanuj NImkar