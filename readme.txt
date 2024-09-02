# Node.js Application: Containerization and Deployment with Podman, Kubernetes, GitHub Actions, and SonarQube

## Overview

This project showcases the process of containerizing a Node.js application using Podman, deploying it to a Kubernetes cluster, and integrating GitHub Actions and SonarQube for continuous integration and code quality monitoring.

## Objectives

- **Containerize** a Node.js application using Podman.
- **Deploy** the containerized application to a Kubernetes cluster.
- **Set up** a CI/CD pipeline using GitHub Actions.
- **Integrate** SonarQube for code quality and vulnerability analysis.

## Prerequisites

- **Podman**: Ensure Podman is installed on your local machine. Follow the [Podman installation guide](https://podman.io/getting-started/installation).
- **Kubernetes Cluster**: Have Minikube or OpenShift set up and configured. See [Minikube installation](https://minikube.sigs.k8s.io/docs/start/) or [OpenShift installation](https://docs.openshift.com/container-platform/latest/installing/index.html) for guidance.
- **GitHub Account**: Create a GitHub account for version control and CI/CD.
- **SonarQube**: Set up an instance of SonarQube for code quality analysis. Refer to the [SonarQube documentation](https://docs.sonarqube.org/latest/setup/get-started-2/) for installation and setup.
- **Node.js Application**: This guide assumes you have a basic Node.js application. If not, a sample Node.js app can be found [here](https://github.com/nodejs/node/tree/main/examples).

## Project Structure

- `Dockerfile`: The Dockerfile used to build the Node.js application container image.
- `k8s/`: Directory containing Kubernetes manifests for deployment.
- `.github/workflows/`: Directory with GitHub Actions workflows for CI/CD.
- `sonar-project.properties`: Configuration file for SonarQube analysis.

## Getting Started

### 1. Build and Run the Container

1. **Create Dockerfile**

   Here's a basic `Dockerfile` for a Node.js application:

   ```dockerfile
   # Use the official Node.js image as a base
   FROM node:18

   # Set the working directory
   WORKDIR /usr/src/app

   # Copy package.json and package-lock.json
   COPY package*.json ./

   # Install dependencies
   RUN npm install

   # Copy the rest of the application code
   COPY . .

   # Expose port 3000
   EXPOSE 3000

   # Start the application
   CMD [ "node", "app.js" ]
