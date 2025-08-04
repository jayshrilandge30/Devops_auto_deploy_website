# 🚀 Automated Website Deployment using Jenkins, Docker & Git

This project demonstrates how to implement a **CI/CD pipeline** that automates the deployment of a static website using **Jenkins**, **Docker**, and **GitHub** on **Ubuntu servers**. Whenever new code is pushed to GitHub, Jenkins automatically builds a Docker image and redeploys the website container — achieving true Continuous Integration and Continuous Delivery (CI/CD).

---

## 📌 Table of Contents

- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Architecture](#architecture)
- [Setup & Configuration](#setup--configuration)
  - [Developer Instance](#1-developer-instance)
  - [Dockerfile Creation](#2-create-dockerfile)
  - [Git Setup & Push](#3-git-setup--push)
  - [Jenkins Master Setup](#4-jenkins-master-setup)
  - [Webhook Configuration](#5-webhook-configuration)
  - [Jenkins Job Configuration](#6-jenkins-job-configuration)
  - [Accessing the Deployed Website](#7-access-deployed-website)
  - [Website Updates](#8-website-updates)
  - [Jenkins Agent Node (Optional)](#9-jenkins-agent-node-optional)
- [Outputs](#outputs)
- [Summary](#summary)

---

## 🧠 Project Overview

This CI/CD project automates the process of deploying a static website from GitHub using Jenkins and Docker. The automation ensures that any changes pushed to the GitHub repo are built into a Docker container and deployed instantly via Jenkins, minimizing manual intervention and increasing deployment speed.

---

## 🛠 Technologies Used

- Ubuntu Server 24.04 LTS (AMI)
- Git & GitHub
- Jenkins
- Docker
- Apache Web Server
- Webhook integration

---

## 🗂 Architecture

<div align="center">
  <img src="images/screenshot26.png" alt="Architecture Diagram" width="100%">
  <p><strong>Automated Deployment Architecture</strong></p>
</div>

---

## ⚙️ Setup & Configuration

### 1️⃣ Developer Instance

```bash
cd /root
wget https://github.com/technext/arsha/archive/refs/heads/main.zip -O arsha.zip
apt install unzip -y
unzip arsha.zip
cd arsha-main
```

<div align="center">
  <img src="images/screenshot1.png" alt="Dev Instance" width="100%">
  <p><strong>Dev Server Instance</strong></p>
</div>

---

### 2️⃣ Create Dockerfile

```dockerfile
FROM ubuntu
RUN apt-get update -y
RUN apt-get install -y apache2
COPY . /var/www/html
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```

<div align="center">
  <img src="images/screenshot2.png" alt="Dockerfile" width="100%">
  <p><strong>Dockerfile Setup for Website Deployment</strong></p>
</div>

---

### 3️⃣ Git Setup & Push

```bash
apt install git -y
git init
git add *
git commit -m "Initial commit - Devops Website"
git remote add origin https://github.com/jayshrilandge30/Devops_auto_deploy_website.git
git push -u origin master
```

<div align="center">
  <img src="images/screenshot3.png" alt="Git Push" width="100%">
  <p><strong>Git Push Command Output</strong></p>
</div>

<div align="center">
  <img src="images/screenshot4.png" alt="GitHub Repo Push" width="100%">
  <p><strong>Remote Repository with Pushed Code</strong></p>
</div>

---

### 4️⃣ Jenkins Master Setup

```bash
apt update -y && apt upgrade -y
apt install openjdk-17-jdk -y
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
apt update -y
apt install jenkins -y
systemctl enable jenkins
systemctl start jenkins
```

<div align="center">
  <img src="images/screenshot5.png" alt="Jenkins Master Setup" width="100%">
  <p><strong>Jenkins Master Instance</strong></p>
</div>

<div align="center">
  <img src="images/screenshot6.png" alt="Sudo Access" width="100%">
  <p><strong>Sudo Access for Jenkins User</strong></p>
</div>

---

### 5️⃣ Webhook Configuration

GitHub → Settings → Webhooks:

```
http://<Jenkins-Master-IP>:8080/github-webhook/
```

<div align="center">
  <img src="images/screenshot9.png" alt="GitHub Webhook" width="100%">
  <p><strong>GitHub Webhook Configuration</strong></p>
</div>

---

### 6️⃣ Jenkins Job Configuration

```bash
sudo docker rm -f container1 || true
sudo docker build -t webserver-image .
sudo docker run -itd --name container1 -p 5000:80 webserver-image
```

<div align="center">
  <img src="images/screenshot10.png" alt="Jenkins Job Setup" width="100%">
  <p><strong>Jenkins Job Setup & Console Output</strong></p>
</div>

---

### 7️⃣ Access Deployed Website

```
http://<Jenkins-Master-Public-IP>:5000
```

<div align="center">
  <img src="images/screenshot11.png" alt="Website Output" width="100%">
  <p><strong>Website Deployed via Jenkins & Docker</strong></p>
</div>

---

### 8️⃣ Website Updates

```bash
vim index.html
git add *
git commit -m "Updated index.html"
git push origin master
```

<div align="center">
  <img src="images/screenshot12.png" alt="Updated Website" width="100%">
  <p><strong>Website Content Updated & Rebuilt</strong></p>
</div>

---

### 9️⃣ Jenkins Agent Node (Optional)

<div align="center">
  <img src="images/screenshot14.png" alt="Jenkins Agent Connected" width="100%">
  <p><strong>Jenkins Agent Node Connected</strong></p>
</div>

---

## 📸 Outputs

<div align="center">
  <img src="images/screenshot19.png" alt="Dashboard" width="100%">
  <p><strong>Jenkins Dashboard with Job Status</strong></p>

  <img src="images/screenshot20.png" alt="Build Console Output" width="100%">
  <p><strong>Build Logs from Console Output</strong></p>

  <img src="images/screenshot21.png" alt="Watch Video Button" width="100%">
  <p><strong>Website Output – Watch Video Button</strong></p>

  <img src="images/screenshot23.png" alt="Contact Form" width="100%">
  <p><strong>Website Contact Form</strong></p>

  <img src="images/screenshot25.png" alt="Portfolio Section" width="100%">
  <p><strong>Website Portfolio Section</strong></p>
</div>

---

## ✅ Summary

- ✅ Downloaded and customized a Bootstrap website template.
- ✅ Used Git and GitHub to track code.
- ✅ Dockerized the app with Apache as the web server.
- ✅ Set up Jenkins on an Ubuntu server to automate deployment.
- ✅ Integrated GitHub webhooks for real-time builds.
- ✅ Scaled CI/CD by adding an optional Jenkins agent node.

---

### 🙌 Project By: **Jayshri Landge**
