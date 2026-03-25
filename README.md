# DevOps Project 1 — Dockerized Multi-Service App with CI/CD

## Overview

A containerized multi-service web application with automated CI/CD pipeline.

## Architecture

- **Frontend**: Nginx serving static HTML
- **Backend**: Python Flask REST API
- **Orchestration**: Docker Compose
- **CI/CD**: Jenkins Pipeline triggered via GitHub webhook

## Tech Stack

- Docker & Docker Compose
- Jenkins
- GitHub (webhook integration)
- Python (Flask)
- Nginx

## How to Run Locally

\`\`\`bash
docker compose up --build
\`\`\`

- Frontend: http://localhost:8080
- Backend: http://localhost:5000

## CI/CD Pipeline Stages

1. Checkout source code
2. Build Docker images
3. Run backend health tests
4. Deploy services
5. Verify deployment

## Author

Kashmitha Madushan — DevOps Engineer (Intern)
This project is licensed under the MIT License — see the LICENSE file for details.
