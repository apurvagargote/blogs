---
title: "🚀 Jenkins Declarative Pipeline ."
datePublished: Sat Mar 01 2025 17:14:43 GMT+0000 (Coordinated Universal Time)
cuid: cm7qgps95000009jo0aoe6is8
slug: jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740849137104/c5a7ca2c-03f3-4f26-989d-55bc2daf94dd.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1740849195158/ff849a09-1b7f-4202-b298-08d85005a468.png
tags: devops, jenkins, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

## 📌 What is a Jenkins Pipeline?

A **Pipeline** in Jenkins automates software delivery through a **sequence of steps.**

### 🏗️ Types of Pipelines

* **Declarative Pipeline** 📝 – Structured and recommended.
    
* **Scripted Pipeline** 💻 – Flexible, Groovy-based.
    

### ✅ Why Use Pipelines?

* **Pipeline-as-Code** for version control 📂
    
* **Automates build, test, and deployment** 🔄
    

---

## 🎯 Task-01: Create a Jenkins Declarative Pipeline

### 1️⃣ Create a New Job

* Open **Jenkins Dashboard** → **New Item** → **Pipeline** 🔧
    
* Name it (e.g., `HelloWorldPipeline`) → **OK** ✅
    

### 2️⃣ Define the Pipeline

Go to **Pipeline** section → **Pipeline Script** → Use this code:

```plaintext
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { echo 'Building... 🏗️' }
        }
        stage('Test') {
            steps { echo 'Testing... ✅' }
        }
        stage('Deploy') {
            steps { echo 'Deploying... 🚀' }
        }
    }
}
```

### 3️⃣ Save & Run

* Click **Save** 💾 → **Build Now** ▶️
    
* Check **Console Output** 🧐
    

---

## 📝 Learnings

* Created a **Pipeline Job** in Jenkins.
    
* Understood **Declarative Pipeline Syntax**.
    
* Implemented **Pipeline-as-Code** for CI/CD.