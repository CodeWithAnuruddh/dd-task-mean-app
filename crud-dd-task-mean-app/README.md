# DevOps Project Highlights - MEAN DD CRUD Application

This document summarizes a complete end-to-end DevOps delivery for a full-stack MEAN application, fully pushed to GitHub with containerization, cloud deployment, CI/CD automation, and reverse proxy setup.

## Project Repository

- GitHub: `https://github.com/CodeWithAnuruddh/dd-task-mean-app`

## Live Deployment

- Application URL: `http://13.232.115.247:3200/`
- Backend API: `http://13.232.115.247:5000/api/tutorials`

## What Was Delivered

- Full MEAN application codebase (frontend + backend)
- Dockerized backend and frontend services
- MongoDB containerized with persistent volume
- Multi-service orchestration with Docker Compose
- AWS EC2 (Ubuntu 22.04) deployment
- Jenkins-based CI/CD pipeline
- Nginx SPA routing support for Angular
- End-to-end automated deployment on code push
- Documentation and screenshot evidence in repository

## Containerization Architecture

### Backend Container

- Base image: `node:22-alpine`
- Production dependency install: `npm install --production`
- Startup command: `node server.js`
- Exposed Host port: `5000`

### Frontend Container

- Multi-stage Docker build
- Build stage: `node:18-alpine`
- Runtime stage: `nginx:alpine`
- Angular build served from `/usr/share/nginx/html`
- Exposed port: `80`
- Exposed Host Port: `3200`

## Docker Compose Topology

- `mongo` (`mongo:6`) with `mongo-data` volume
- `backend` image: `apsingh566/ddtask-backend:latest` (`5000:8080`)
- `frontend` image: `apsingh566/ddtask-frontend:latest` (`3200:80`)
- Shared custom bridge network: `app-network`

## Cloud Environment

- Platform: AWS EC2
- Instance: `t2.medium`
- OS: Ubuntu 22.04
- Installed services: Docker, Docker Compose, Jenkins
- Database runtime: MongoDB container
- Web serving: Nginx in frontend container

## CI/CD Automation (Jenkins)

### Pipeline Stages Implemented

1. Checkout code from `main` branch
2. Build backend Docker image
3. Build frontend Docker image
4. Push both images to Docker Hub
5. Pull latest images on VM
6. Restart stack with Docker Compose
7. Cleanup old Docker images

### Deployment Behavior

Every push to GitHub triggers automated build and deployment, resulting in updated running containers with no manual intervention.

## Evidence Included in GitHub

- Jenkins pipeline run screenshots
- Docker build and push logs
- Docker Hub image screenshots
- Running container snapshots
- Working application UI
- AWS EC2 infrastructure proof
- Nginx setup/config screenshots

## Operational Readiness Notes

- Fully containerized stack
- Persistent MongoDB storage configured
- SPA routing handled correctly
- Reverse-proxy-ready architecture
- CI/CD-driven repeatable deployments

## Author

Anuruddh Pratap Singh  
DevOps Discover Dollar Assignment - 2026

