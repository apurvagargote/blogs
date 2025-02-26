---
title: "😃Getting Started with Jenkins ."
datePublished: Tue Feb 25 2025 10:54:39 GMT+0000 (Coordinated Universal Time)
cuid: cm7kddlqt000809kz6t51di2f
slug: getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740480655470/5d83170f-c10f-4aef-886f-62a7b8e9b128.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1740480853899/ffc8a20c-7769-4871-9f6d-46eddcc14d0c.jpeg
tags: devops, jenkins, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

Jenkins is an open-source automation server written in Java that helps automate the process of building, testing, and deploying software. It’s a core key tool in the DevOps toolkit!

---

## What is Jenkins and Why Use It? 🤔

* **Automation at Its Best:**  
    Jenkins automates repetitive tasks like building, testing, and deploying code, saving you time and reducing human errors.
    
* **Seamless Integration:**  
    With a wide range of plugins, Jenkins easily integrates with tools like Git, Docker, and more—making it an essential part of the DevOps lifecycle.
    
* **Continuous Improvement:**  
    By running tests and deployments automatically, Jenkins helps ensure that new code changes are safe and production-ready at all times.
    

---

## 🛠️Creating a Simple Freestyle Pipeline with Jenkinsfile

### Steps to Create the Pipeline:

1. **Set Up Your Job:**
    
    * Create a new Freestyle project in Jenkins.
        
    * Configure it to use a Jenkinsfile from your source control.
        
2. **Define Pipeline Tasks:**
    
    * **Greeting:** Print a welcoming "Hello World".
        
    * **Date & Time:** Show the current date and time.
        
    * **Clone Repository:** Pull a GitHub repository and list its files.
        
    * **Schedule Execution:** Set the job to run periodically (e.g., every hour).
        
3. **Write the Jenkinsfile:**  
    Save the following Jenkinsfile in the root of your project repository.
    

---

### Jenkinsfile Example

```plaintext
pipeline {
    agent any

    // Schedule the pipeline to run every hour
    triggers {
        cron('H * * * *')
    }

    stages {
        stage('Greeting') {
            steps {
                // Print "Hello World"
                echo 'Hello World'
            }
        }
        stage('Show Date & Time') {
            steps {
                // Display current date and time
                sh 'date'
            }
        }
        stage('Clone and List Repository') {
            steps {
                // Clone the GitHub repository (replace URL with your repo)
                sh 'git clone https://github.com/your-repository-url.git'
                // List contents of the cloned repository (update folder name if needed)
                sh 'ls -la your-repository-folder'
            }
        }
    }
}
```

---

## How It Works 🌟

* **Agent any:**  
    The pipeline runs on any available Jenkins agent.
    
* **Triggers:**  
    The cron syntax (`H * * * *`) schedules the pipeline to run every hour automatically.
    
* **Stages:**
    
    * **Greeting:** Uses `echo` to print "Hello World".
        
    * **Show Date & Time:** Executes the `date` command to display the current date and time.
        
    * **Clone and List Repository:**
        
        * Clones your specified GitHub repository.
            
        * Lists all files in the repository directory.
            

---

Demo:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740480304183/f7d840ba-9060-4878-ac86-9ce5c710fbee.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740480325162/9aaa4b88-f28b-424b-a6b9-53d009edcb34.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740480344491/a79c145f-2654-45a8-adce-eb32a54cd35d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740480356111/74e74074-6f0e-4dff-b9d8-86d8b657eb31.png align="center")

Happy automating! 😃👍
