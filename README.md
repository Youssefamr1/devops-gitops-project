# DevOps GitOps Platform on OpenShift & AWS

## Overview

This project demonstrates a complete CI/CD and GitOps workflow using Docker, Jenkins, Helm, ArgoCD, OpenShift, Prometheus, Grafana, and AWS.

The goal of the project is to automate application deployment from source code changes all the way to production deployment while following GitOps principles.

---

## Architecture

Developer
|
GitHub
|
Jenkins
|
Docker Build
|
Docker Hub
|
Update Helm Values
|
Git Push
|
ArgoCD
|
OpenShift
|
Application
|
Prometheus
|
Grafana

---

## Technologies Used

* Docker
* OpenShift
* Kubernetes
* Helm
* Jenkins
* ArgoCD
* Prometheus
* Grafana
* AWS
* GitHub

---

## Project Components

### Application

A simple web application running inside an Nginx container.

### Docker

The application is containerized using Docker and pushed to Docker Hub.

### OpenShift

The application is deployed on OpenShift using Kubernetes resources.

### Helm

Helm is used to manage application deployments through reusable templates and values files.

### Jenkins

Jenkins is responsible for:

* Pulling source code from GitHub
* Building Docker images
* Pushing images to Docker Hub
* Updating Helm values

### ArgoCD

ArgoCD continuously monitors the Git repository and automatically synchronizes changes to the OpenShift cluster.

### Monitoring

Prometheus collects metrics from the cluster and application.

Grafana visualizes:

* CPU Usage
* Memory Usage
* Pod Metrics
* Container Metrics

---

## CI/CD Workflow

1. Developer pushes code to GitHub.
2. Jenkins pipeline is triggered.
3. Jenkins builds a Docker image.
4. Jenkins pushes the image to Docker Hub.
5. Jenkins updates Helm values with the new image tag.
6. Jenkins pushes the updated configuration to GitHub.
7. ArgoCD detects the change.
8. ArgoCD synchronizes the OpenShift cluster.
9. The new application version is deployed automatically.

---

## GitOps Workflow

Git is the single source of truth.

Any change made to the desired state in Git is automatically applied to the OpenShift cluster through ArgoCD.

---

## Monitoring

The platform includes monitoring using Prometheus and Grafana.

Available dashboards:

* CPU Utilization
* Memory Utilization
* Pod Status
* Container Metrics
* Application Health

---

## AWS Infrastructure

AWS resources used:

* VPC
* Public Subnet
* Private Subnet
* EC2
* Security Groups
* IAM Roles

Jenkins can be hosted on AWS EC2 to provide a highly available CI/CD environment.

---

## Project Structure

devops-gitops-project/

app/

* Dockerfile
* index.html

helm/

* devops-chart/

jenkins/

* Jenkinsfile

argocd/

* application.yaml

docs/

* architecture.png
* jenkins.png
* openshift.png
* grafana.png

README.md

---

## Challenges Faced

### OpenShift Security Context

While deploying the application on OpenShift, the default Nginx image failed due to OpenShift's non-root security model.

Error:

Permission denied while creating Nginx temporary directories.

Solution:

Used nginxinc/nginx-unprivileged image to support OpenShift's random UID security requirements.

---

## Key Learnings

* Containerization using Docker
* Kubernetes and OpenShift deployments
* Helm chart management
* Jenkins CI pipelines
* GitOps using ArgoCD
* Monitoring with Prometheus and Grafana
* AWS infrastructure basics
* OpenShift security best practices

---

## Future Enhancements

* SonarQube Integration
* Trivy Security Scanning
* Horizontal Pod Autoscaler (HPA)
* Multi-Environment Deployment (Dev/Test/Prod)
* Blue/Green Deployment Strategy
* Secrets Management
* Nexus Repository Integration
