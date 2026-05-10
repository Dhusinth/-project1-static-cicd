# Project 1 - Static Website CI/CD Pipeline

## What this project does
This project automatically builds and deploys a static website 
whenever code is pushed to GitHub.

## Tools Used
- AWS EC2
- Jenkins
- Docker
- Nginx
- GitHub

## How the pipeline works
1. **Checkout** - Jenkins fetches the latest code from GitHub
2. **Build** - Code is built into a Docker image
3. **Push** - Docker image is tagged and pushed to Docker Hub 
   using stored credentials
4. **Deploy** - Running container is stopped and restarted 
   with the latest image

## How to run
1. Launch EC2 instance and install Jenkins and Docker
2. Add Docker Hub credentials to Jenkins
3. Create a pipeline job pointing to this repo
4. Push code to GitHub to trigger the pipeline automatically
5. Configure GitHub webhook pointing to http://<EC2-IP>:8080/github-webhook/
