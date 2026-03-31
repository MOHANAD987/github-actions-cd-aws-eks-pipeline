# 🚀 CI/CD Pipeline using GitHub Actions, Docker & AWS EKS

<p align="center">

  <img src="https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-blue?logo=githubactions&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Kubernetes-EKS-326CE5?logo=kubernetes&logoColor=white" />
  <img src="https://img.shields.io/badge/AWS-Cloud-FF9900?logo=amazonaws&logoColor=white" />
  <img src="https://img.shields.io/badge/Java-Maven-red?logo=apachemaven&logoColor=white" />
  <img src="https://img.shields.io/github/actions/workflow/status/YOUR_USERNAME/YOUR_REPO/cd.yml?label=Build&logo=githubactions" />

</p>


---


## 📌 Project Description

This project demonstrates how to build a **complete CI/CD pipeline** using **GitHub Actions** to automate:

- 🔨 Building a Java application  
- 🐳 Creating a Docker image  
- 📦 Pushing the image to Docker Hub  
- ☸️ Deploying the application to Kubernetes (AWS EKS)  


---


## ⭐ Project Value

This project reflects the practical implementation of modern DevOps concepts and demonstrates:

- Full automation of the deployment process  
- Use of Kubernetes in a cloud environment  
- Integration between GitHub, Docker, and AWS  
- Production-ready deployment practices  


---


## 🎯 Project Objectives

- Implement CI/CD in a real-world scenario  
- Automate build and deployment processes  
- Deploy applications on Kubernetes  
- Gain hands-on experience in DevOps and Cloud  


---


## ⚙️ How the Pipeline Works

When code is pushed to the `main` branch, the workflow runs automatically:

### Steps:

1. 📥 Checkout the code  
2. 🔨 Build the application using Maven  
3. 🐳 Build a Docker image  
4. 📦 Push the image to Docker Hub  
5. 🔐 Configure AWS credentials  
6. ☸️ Connect to EKS cluster  
7. 🚀 Deploy the application to Kubernetes  


---



## ⚡ Workflow File

📍 Path:
.github/workflows/cd.yml


```yaml
name: cd workflow

on:
  push:
    branches:
      - main

jobs:
  cd-workflow:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Build app
        run: mvn clean package

      - name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_PASSWORD }}

      - name: Build & Push Image
        uses: docker/build-push-action@v3
        with:
          push: true
          tags: ${{ secrets.DOCKERHUB_USERNAME }}/java-app:latest

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1

      - name: Update kubeconfig
        run: aws eks update-kubeconfig --region us-east-1 --name eks

      - name: Deploy to Kubernetes
        run: kubectl apply -f ./k8s/deployment.yaml
```


---


## 🛠️ Technologies Used

- GitHub Actions  
- Docker  
- Kubernetes (EKS)  
- AWS  
- Java  
- Maven  


---


## 🚀 Quick Start

### 1️⃣ Clone the Project

```bash
git clone https://github.com/MOHANAD987/github-actions-cd-aws-eks-pipeline.git
cd github-actions-cd-aws-eks-pipeline
````


---


### 2️⃣ Run the Application Locally

```bash
mvn clean package
```


---


### 3️⃣ Trigger the Pipeline

```bash
git add .
git commit -m "trigger pipeline"
git push origin main
```


---


## 🐳 Docker Image

```bash
${{ secrets.DOCKERHUB_USERNAME }}/java-app:latest
```


---


## ☸️ Kubernetes Commands


### Deploy the Application

```bash
kubectl apply -f ./k8s/deployment.yaml
```


### Verify Deployment

```bash
kubectl get pods
kubectl get deployments
kubectl get nodes
```


---


## 📂 Project Structure

```text
project/
│
├── .github/workflows/cd.yml
├── k8s/
│   └── deployment.yaml
├── src/
├── Dockerfile
├── pom.xml
├── README.md
├── LICENSE
│
├── screenshots/
├── diagrams/
│   └── architecture.png
```



---



## 📸 Screenshots

🔗 [Open Screenshots Folder](./screenshots/)


---


## 📊 System Architecture Diagrams

🔗 [Open Diagrams Folder](./diagrams/)


---


## ❗ Common Issues

### 🔴 Forbidden Error

```bash
User is forbidden
```


✔ Solution:

* Add IAM user to EKS access
* Grant:

```bash
AmazonEKSClusterAdminPolicy
```


---


### 🔴 Authentication Error

```bash
aws eks update-kubeconfig --region us-east-1 --name <cluster-name>
```


---


## 📚 What I Learned

* Designing CI/CD pipelines using GitHub Actions
* Managing Docker images
* Deploying applications on Kubernetes
* Working with AWS EKS
* Automating the full application lifecycle


---


## 📈 Future Improvements

* Add Helm charts
* Use Terraform for infrastructure provisioning
* Implement monitoring (Prometheus + Grafana)
* Apply Blue/Green deployment strategy


---


## 👨‍💻 Developer

Mohannad Faisal
DevOps & Cloud Engineer


---


## 📄 License

This project is licensed under the MIT License.


---


## ⭐ Support the Project

If you like this project, don’t forget to give it a ⭐ on GitHub!

```
```







