---
title: "🚀 Jenkins Freestyle Project: Setting Up an Agent & Automating Docker Tasks"
datePublished: Wed Feb 26 2025 07:42:50 GMT+0000 (Coordinated Universal Time)
cuid: cm7llyrul000d09if1rum8j7w
slug: jenkins-freestyle-project-setting-up-an-agent-and-automating-docker-tasks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740555154429/dcdbea22-f1ee-4029-b37f-38235745920d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1740555752601/11fd7f09-647f-4cb1-8018-0e85411f3190.png
tags: devops, jenkins, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

This guide will help you:  
✅ **Set up a Jenkins Agent via SSH on another EC2 instance**  
✅ **Create a Jenkins Freestyle Project** to build & run a Docker container  
✅ **Automate Multi-Container Deployment** using Docker Compose

---

## 🔹 **Task 1: Setting Up a Jenkins Agent via SSH & Running Docker Build**

### 🛠 **Step 1: Install Jenkins on the Master Node (EC2 Instance 1)**

✅Ensure Jenkins is installed and running on the **Jenkins Master Machine** (EC2 Instance 1). You can install Jenkins using:

```plaintext
sudo apt update && sudo apt install -y openjdk-17-jdk
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list
sudo apt update
sudo apt install -y jenkins
sudo systemctl enable --now jenkins
```

✅Check Jenkins status:

```plaintext
sudo systemctl status jenkins
```

---

### 🛠 **Step 2: Install & Configure SSH on the Agent Machine (EC2 Instance 2)**

✅On the **Jenkins Agent Machine** (which is a separate EC2 instance), install the necessary packages:

```plaintext
sudo apt update && sudo apt install -y openjdk-17-jdk openssh-server
sudo systemctl enable --now ssh
```

✅ **Install Docker (Latest Version) & Configure Jenkins User**

```plaintext
sudo apt-get install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo tee /etc/apt/keyrings/docker.gpg > /dev/null
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

✅Create a Jenkins user:

```plaintext
sudo useradd -m -s /bin/bash jenkins
sudo passwd jenkins  # Set a password for the Jenkins user
```

✅Give Jenkins user Docker permissions:

```plaintext
sudo usermod -aG docker jenkins
```

✅Generate an SSH Key (on the **Agent Machine**, logged in as Jenkins user):

```plaintext
ssh-keygen -t rsa -b 4096
cat ~/.ssh/id_rsa.pub
```

🔹 `ssh-keygen` → The command to generate SSH key pairs.  
🔹 `-t rsa` → Specifies the key type as **RSA** (Rivest-Shamir-Adleman), a widely used encryption algorithm.  
🔹 `-b 4096` → Sets the key length to **4096 bits**, making it more secure (default is 2048 bits).

Copy this key and add it to the **Master Machine** under `/home/jenkins/.ssh/authorized_keys`.

✅Test SSH connection from **Jenkins Master(EC2 Instance 1)** to **Jenkins Agent (EC2 Instance 2)**:

```plaintext
ssh jenkins@<AGENT_EC2_IP>
```

---

### 🛠 **Step 3: Add the Agent Node in Jenkins UI**

1. **Go to Jenkins Dashboard** → `Manage Jenkins` → `Manage Nodes and Clouds` → `New Node`
    
2. Enter a **Node Name** (e.g., `docker-agent`), select **Permanent Agent**, and click **OK**
    
3. Set **Remote root directory**: `/home/jenkins`
    
4. Select **Launch method**: `Launch agents via SSH`
    
5. Enter the **Agent Machine (EC2 Instance 2) IP** and **Jenkins User Credentials**
    
6. Click **Save** and then **Launch Agent** to verify the connection
    

---

### 🛠 **Step 4: Create a Jenkins Freestyle Project to Build & Run a Docker Container**

1. **Go to Jenkins Dashboard** → Click `New Item`
    
2. Enter a **Project Name** (e.g., `Docker-Build-Run`) and select `Freestyle Project`
    
3. Under **General**, select `Restrict where this project can be run` and enter `docker-agent`
    
4. In the **Build Section**, click `Add build step` → `Execute Shell`
    
5. Add the following commands:
    

```plaintext
cd /home/jenkins/workspace/Docker-Build-Run
docker build -t my-app:latest .
docker run -d -p 8080:8080 --name my-app-container my-app:latest
```

6. Click **Save** and then **Build Now**
    

#### 📜 **Jenkinsfile for Task 1**

```plaintext
pipeline {
    agent { label 'docker-agent' }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-repo/app.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app:latest .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:8080 --name my-app-container my-app:latest'
            }
        }
    }
}
```

---

## 🔹 **Task 2: Automate Multi-Container Deployment using Docker Compose**

### 🛠 **Step 1: Create a Docker Compose File**

✅Inside your repository (`/home/jenkins/workspace/Docker-Compose`), create `docker-compose.yml`:

```plaintext
version: '3.9'
services:
  app:
    image: my-app:latest
    ports:
      - "8080:8080"
    depends_on:
      - db
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: app_db
```

---

### 🛠 **Step 2: Create a Jenkins Freestyle Project for Docker Compose**

1. **Go to Jenkins Dashboard** → Click `New Item`
    
2. Enter a **Project Name** (e.g., `Docker-Compose`) and select `Freestyle Project`
    
3. Under **General**, select `Restrict where this project can be run` and enter `docker-agent`
    
4. In the **Build Section**, click `Add build step` → `Execute Shell`
    
5. Add the following commands:
    

```plaintext
cd /home/jenkins/workspace/Docker-Compose
docker-compose up -d
```

6. Click **Post-build Actions** → `Add build step` → `Execute Shell`
    
7. Add cleanup commands:
    

```plaintext
cd /home/jenkins/workspace/Docker-Compose
docker-compose down
```

8. Click **Save** and then **Build Now**
    

#### 📜 **Jenkinsfile for Task 2**

```plaintext
pipeline {
    agent { label 'docker-agent' }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-repo/app.git'
            }
        }
        stage('Start Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }
        stage('Cleanup') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}
```

---
