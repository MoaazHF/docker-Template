# 🚀 Ultimate Full-Stack Docker Template (NestJS + React)

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![NestJS](https://img.shields.io/badge/nestjs-%23E0234E.svg?style=for-the-badge&logo=nestjs&logoColor=white)
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)

A production-ready, highly optimized **DevOps boilerplate** for building scalable Full-Stack applications. This template separates concerns by containerizing the Backend (NestJS), Frontend (React + Vite served by Nginx), and Database (PostgreSQL) into isolated, communicating services.

---

## 🧐 Why Use This Template?

Unlike standard "Hello World" setups, this template is engineered with **Best Practices** in mind:

### 1. ⚡ Blazing Fast Builds (Caching Strategy)
Uses advanced Docker **BuildKit caching** (`--mount=type=cache`) with `pnpm`.
- **The Result:** `npm install` runs once. Subsequent builds skip downloading packages entirely if `package.json` hasn't changed.
- **Build Time:** Reduced from minutes to seconds.

### 2. 🛡️ Enterprise-Grade Security
- **Non-Root User:** Runs applications as a restricted `app` user, not `root`, preventing container breakout attacks.
- **Production Optimization:** Multi-stage builds ensure only the necessary artifacts (dist folder) make it to the final image, keeping image sizes small (~100MB vs 1GB+).

### 3. 🚀 High-Performance Architecture
- **Frontend:** Served via **Nginx** (Alpine), which is 10x faster at serving static files than Node.js.
- **Backend:** Isolated NestJS instance connected directly to the database via internal Docker network.
- **Orchestration:** `depends_on` and `healthcheck` ensure services start in the correct order (DB -> Backend -> Frontend).

---

## 🎯 When to Use This?

This template is perfect for:
- **Startup MVPs:** Quickly launch a secure, scalable product.
- **Freelance Deliverables:** Hand over a professional, "dockerized" project that runs on any client server.
- **Graduation Projects:** Impress supervisors with a clean DevOps architecture.
- **Learning:** Understanding how Microservices communicate in a containerized environment.

---

## 🛠️ Project Structure

```bash
├── backend/                # NestJS Application
│   ├── Dockerfile          # Production Dockerfile (Node.js)
│   └── ...
├── frontend/               # React + Vite Application
│   ├── Dockerfile          # Production Dockerfile (Nginx)
│   ├── nginx.conf          # Nginx configuration
│   └── ...
├── docker-compose.yml      # Orchestration file
└── .env                    # Environment Variables (Not committed)
