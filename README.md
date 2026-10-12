# 🚀 Taskwave

**A production-inspired distributed task queue built with React, Node.js, Express, Redis, PostgreSQL, Docker, and background workers.**

Taskwave demonstrates how modern backend systems process long-running tasks asynchronously using a distributed architecture. Instead of executing expensive operations during an HTTP request, jobs are queued in Redis and processed independently by worker services, improving scalability, reliability, and responsiveness.

---

## ✨ Features

* 🔐 JWT Authentication
* 📋 Create and manage background jobs
* ⚡ Priority-based job scheduling
* 🔄 Automatic retry mechanism for failed jobs
* 📊 Real-time job status updates
* 👷 Separate worker service for asynchronous processing
* 📧 Email processing
* 📁 Data export (CSV)
* 🖼️ Image resize processing
* 🌐 Webhook processing
* 🐳 Dockerized multi-service architecture
* 🗄️ PostgreSQL for persistent storage
* ⚡ Redis as the distributed message queue

---

## 🏗️ Architecture

```text
                 React Frontend
                        │
                        ▼
                 Express REST API
                        │
         Stores Job Metadata (PostgreSQL)
                        │
                        ▼
                  Redis Queue
                        │
            ┌───────────┴───────────┐
            ▼                       ▼
      Worker Service         Worker Service
            │
            ▼
   Email / Image Resize /
   Data Export / Webhooks
```

---

## 🛠️ Tech Stack

### Frontend

* React
* Vite
* Tailwind CSS

### Backend

* Node.js
* Express.js
* JWT Authentication

### Database

* PostgreSQL

### Queue

* Redis

### Worker

* Node.js Background Worker

### DevOps

* Docker
* Docker Compose

---

## 📂 Project Structure

```text
taskwave/
│
├── apps/
│   ├── api/
│   ├── worker/
│   └── frontend/
│
├── docker-compose.yml
├── schema.sql
└── README.md
```

---

## ⚙️ Getting Started

### Clone the repository

```bash
git clone https://github.com/<your-username>/taskwave.git
cd taskwave
```

### Install dependencies

```bash
npm install
npm install --prefix apps/api
npm install --prefix apps/worker
npm install --prefix apps/frontend
```

### Configure environment variables

Create the required `.env` files for:

* API
* Worker
* Frontend

---

### Run with Docker

```bash
docker compose up --build
```

---

### Run without Docker

Start each service separately.

API

```bash
npm run dev --prefix apps/api
```

Worker

```bash
npm run dev --prefix apps/worker
```

Frontend

```bash
npm run dev --prefix apps/frontend
```

---

## 📌 Supported Job Types

| Job Type     | Description                          |
| ------------ | ------------------------------------ |
| Email        | Sends email asynchronously           |
| Image Resize | Resizes uploaded images              |
| Data Export  | Generates CSV exports                |
| Webhook      | Sends HTTP requests to external APIs |

---

## 🔄 Job Lifecycle

```text
Created
   │
   ▼
Queued
   │
   ▼
Processing
   │
   ├────────► Failed
   │             │
   │             ▼
   │         Retry Queue
   │
   ▼
Completed
```

---

## 📈 Why Asynchronous Processing?

Instead of blocking the user while expensive tasks execute:

```
User Request
      │
      ▼
API stores job
      │
      ▼
Returns response immediately
      │
      ▼
Worker processes job later
```

Benefits:

* Better scalability
* Faster API responses
* Improved reliability
* Independent workers
* Retry support
* Fault tolerance

---

## 🚀 Future Improvements

* Dead Letter Queue (DLQ)
* Scheduled jobs
* Delayed execution
* Multiple worker instances
* Queue monitoring dashboard
* Rate limiting
* Prometheus metrics
* Kubernetes deployment
* Role-based access control
* WebSocket-based live updates

---

## 📸 Screenshots

*Add screenshots of the dashboard, job creation, worker logs, and completed jobs.*

---

## 👨‍💻 Author

**Amit Kumar**

* GitHub: https://github.com/amitkr-dev
* LinkedIn: https://www.linkedin.com/in/amitkumar7824

---

## 📄 License

This project is licensed under the MIT License.
