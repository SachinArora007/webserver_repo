# 🚀 Jenkins CI/CD Pipeline Automation

This project demonstrates a complete **CI/CD pipeline using Jenkins**, 
where code pushed to GitHub is automatically built and deployed to a web server.

---

## 📌 Project Overview

This pipeline automates the entire software delivery process:

- Code is written in VS Code
- Pushed to GitHub repository
- GitHub webhook triggers Jenkins
- Jenkins pulls latest code
- Application is deployed to server
- Website reflects changes automatically

---

## 🏗️ Architecture Workflow


Developer (VS Code)
↓
GitHub Repo
↓ 
(Webhook Trigger)
Jenkins Server (Public IP)
↓
Build & Deployment
↓
Web Server (Live Website)


---

## ⚙️ Tools & Technologies Used

- Jenkins (CI/CD Automation)
- Git & GitHub (Version Control)
- VS Code (Code Editor)
- Linux Server (Hosting Jenkins & Web App)
- Webhook (Automation trigger)

---

## 🔧 Setup & Configuration Steps

### 1️⃣ Jenkins Setup

- Installed Jenkins on Linux server
- Configured Jenkins and exposed via Public IP
- Installed required plugins:
  - Git Plugin
  - Pipeline Plugin

---

### 2️⃣ GitHub Integration

- Created repository and pushed code

```bash id="git1"

git init
git add .
git commit -m "Initial commit"
git push origin main

3️⃣ Webhook Configuration
Configured webhook in GitHub:

http://<JENKINS_PUBLIC_IP>:8080/github-webhook/
✔ Automatically triggers Jenkins on every push

4️⃣ Jenkins Job Configuration
Created Freestyle/Pipeline job
Configured:
GitHub repo URL
Branch: main
Credentials (PAT)
Build trigger: GitHub webhook

5️⃣ Build & Deployment
Jenkins executes deployment commands:

rm -f /var/www/html/index.html
rm -f /var/www/html/index.nginx-debian.html
cp index.html /var/www/html/

✔ Automatically updates website

▶️ Pipeline Execution Flow

-> Developer pushes code to GitHub
-> Webhook triggers Jenkins
-> Jenkins pulls latest code
-> Build process executes
-> Application deployed to server
-> Website updates after refresh

📦 Key Features

-> Fully automated CI/CD pipeline
-> Real-time deployment on code push
-> No manual intervention required
-> Simple and efficient setup

⚠️ Challenges Faced & Solutions

🔴 1. Branch Configuration Issue

Error:

ERROR: Couldn't find any revision to build.
Cause:
Jenkins was configured with master branch
Repository was using main

Solution:
Updated branch to main in Jenkins job


🔴 2. GitHub Authentication Issue

Issue:
No credentials specified

Cause:
Jenkins could not access repository securely

Solution:
Added GitHub credentials (Username + PAT)
Configured in Jenkins (github_cred)

🔴 3. Sudo Permission Issue

Error:
sudo: a terminal is required to read the password

Cause:
Jenkins runs as non-interactive user
sudo requires password input

✅ Solution Applied
Removed sudo from deployment commands
rm -f /var/www/html/index.html
cp index.html /var/www/html/

Alternative (Best Practice):
sudo visudo
jenkins ALL=(ALL) NOPASSWD: ALL

🟢 Final Result
Build successful
Code deployed automatically
Website updated instantly

📊 Benefits
Faster deployment cycle
Reduced manual effort
Real-time updates
Improved DevOps workflow

🎯 Learning Outcome
CI/CD pipeline fundamentals
Jenkins automation
GitHub webhook integration
Real-world deployment troubleshooting

👨‍💻 Author
Sachin Arora
DevOps Engineer


If you found this project helpful, give it a star ⭐
