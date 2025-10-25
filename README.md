# Jenkins CI/CD Internship Task2: Hello World App

## Project Overview

This project demonstrates a **basic CI/CD pipeline** using **Jenkins** and **Docker**.  
The pipeline automates the following steps whenever new code is pushed to GitHub:

1. Checkout code from GitHub  
2. Build a Docker image of the application  
3. Run tests (if defined)  
4. Deploy the application in a Docker container  

The app is a simple **Node.js "Hello World"** application.

---

## Application Details

- App Entry Point: `app.js`  
- Port: `4000`  
- Docker Image Name: `jenkins-hello-world`  
- Docker Container Name: `jenkins-hello-world`  

---

## How to Run Locally

1. Build Docker Image:
docker build -t jenkins-hello-world .

Run Docker Container:
docker run -d -p 4000:4000 --name jenkins-hello-world jenkins-hello-world

Access the App:
Open your browser at http://<your-ec2-public-ip>:4000

GitHub & Jenkins Setup
GitHub Repo:
Public repository containing Dockerfile, app.js, package.json.

Jenkins Job Configuration:

Pipeline script from SCM (Git)

Branch: main

Script Path: Jenkinsfile

Build Trigger: Poll SCM (* * * * *)

Whenever a commit is pushed, Jenkins detects it (via Poll SCM) and runs the pipeline automatically.

Notes
The pipeline stops and removes any old container before deploying the new one.

The app runs on port 4000, as required.

Tests are optional; if no test is defined, the stage is skipped.

Author
Intern: Bharat
Task: DevOps Internship – Jenkins CI/CD Pipeline
