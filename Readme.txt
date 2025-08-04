#  Automated Website Deployment using Jenkins, Docker & Git

This project demonstrates how to implement a **CI/CD pipeline** that automates the deployment of a static website using **Jenkins**, **Docker**, and **GitHub** on **Ubuntu servers**. Whenever new code is pushed to GitHub, Jenkins automatically builds a Docker image and redeploys the website container — achieving true Continuous Integration and Continuous Delivery (CI/CD).

---

##  Table of Contents

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

##  Project Overview

This CI/CD project automates the process of deploying a static website from GitHub using Jenkins and Docker. The automation ensures that any changes pushed to the GitHub repo are built into a Docker container and deployed instantly via Jenkins, minimizing manual intervention and increasing deployment speed.

---

##  Technologies Used

- Ubuntu Server 24.04 LTS (AMI)
- Git & GitHub
- Jenkins
- Docker
- Apache Web Server
- Webhook integration

---

##  Architecture

<div align="center">
  <img src="images/screenshot26.png" alt="Architecture Diagram" width="100%">
  <p><strong>Automated Deployment Architecture</strong></p>
</div>

---

##  Setup & Configuration

### 1️⃣ Developer Instance

- Launch Ubuntu 24.04 LTS instance.
- Download the Arsha Bootstrap theme:

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

... (remaining content trimmed for brevity in code) ...
