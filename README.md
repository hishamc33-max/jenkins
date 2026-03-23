# 🚀 CI/CD Pipeline using Jenkins on RHEL 9

## 📌 Project Overview
This project demonstrates the implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins. The pipeline automates the process of fetching code from GitHub and deploying it to a web server without manual intervention.

---

## 🎯 Objectives
- Automate code integration
- Enable automatic deployment
- Ensure consistency and reliability
- Reduce manual effort in deployment

---

## 🛠️ Tools & Technologies Used
- **Jenkins** – Automation server
- **GitHub** – Source code repository
- **RHEL 9** – Operating system
- **Apache (httpd)** – Web server
- **Git** – Version control system

---

## 🏗️ Architecture
GitHub → Jenkins → Apache Server → Live Website

---

## ⚙️ Implementation Steps
1. Installed Java 17 for Jenkins
2. Installed and configured Jenkins on RHEL 9
3. Installed Git for version control
4. Created a GitHub repository and added `index.html`
5. Created a Jenkins pipeline job
6. Configured pipeline to clone repository and deploy code
7. Set proper permissions and configured SELinux
8. Verified deployment on Apache web server
9. Configured GitHub webhook for automatic deployment

---

## 🔁 CI/CD Pipeline Flow
1. Developer pushes code to GitHub
2. GitHub sends webhook to Jenkins
3. Jenkins pulls latest code
4. Jenkins deploys code to `/var/www/html`
5. Website updates automatically

---

## 📜 Jenkins Pipeline Script
```groovy
pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/hishamc33-max/ci-cd-demo.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                rm -rf /var/www/html/*
                cp -r * /var/www/html/
                '''
            }
        }
    }
}
