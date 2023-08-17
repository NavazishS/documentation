# GitOps CI/CD Pipeline for Python Application deployment using Jenkins, ArgoCD, and Minikube.

## Prerequisites

- Jenkins Host (AWS EC2)
- ArgoCD
- Minikube
- Docker
- Git
- Python

## Overview

This repository provides a GitOps-style CI/CD pipeline for deploying a Python-based application using Jenkins, ArgoCD, and Minikube. The pipeline automates the build, test, and deployment process in a Kubernetes environment.

## Getting Started

Follow these steps to set up the CI/CD pipeline:

1. **Install Jenkins Plugins**:
   - Install all recommended plugins during Jenkins installation.
   - Install the 'docker-pipeline' plugin to run the Jenkins agent as a container.
   - Install the 'sonar-scanner' plugin for code analysis.

2. **Create a Jenkins Pipeline**:
   - Create a new pipeline job in Jenkins and configure it with your Git repository URL.
   - Add a Jenkinsfile to your Git repository to define the pipeline stages.

3. **Define Pipeline Stages**:
    - **Stage 1 - Build and Test**: Checkout source code from Git and build a Docker image for the Python application. Run unit tests using 'curl'.
    - **Stage 2 - Static Code Analysis**: Analyze code quality using SonarQube (not configured in current solution).
    - **Stage 3 - Build and Push Docker Image**: Build and push a Docker image to the repository.
    - **Stage 4 - Update Deployment File**: Update the deployment YAML with the new image tag and push changes to Git.
    - **Stage 5 - GitOps Deployment**: ArgoCD watches for changes and deploys the updated application to Minikube.

4. **Install Minikube on EC2**:
   - SSH into your EC2 instance and install Minikube.
   - Start Minikube using the appropriate driver.

5. **Set up ArgoCD**:
   - Install ArgoCD on your Kubernetes cluster.
   - Configure ArgoCD to track changes in Helm charts and Kubernetes manifests.

6. **Configure Jenkins Integration with ArgoCD**:
   - Add the Argo CD API token to Jenkins credentials.
   - Update the Jenkins pipeline to include the Argo CD deployment stage.

7. **Run the Jenkins Pipeline**:
   - Trigger the Jenkins pipeline to initiate the CI/CD process for the Python application.
   - Monitor the pipeline stages and address any issues that may arise.
