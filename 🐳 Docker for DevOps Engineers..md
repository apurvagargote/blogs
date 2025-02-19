---
title: "🐳 Docker for DevOps Engineers."
datePublished: Wed Feb 19 2025 13:36:40 GMT+0000 (Coordinated Universal Time)
cuid: cm7byiuc2000g09jvai0i1sju
slug: docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739972133020/67d4830d-db67-4bca-8858-acbad34d4248.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1739972192389/b244435f-cf48-4b48-a659-56daf091bc45.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

### 💡 What is Docker?

* Docker is like a **magic suitcase** 🧳 for your applications. It lets you **pack** everything your app needs—libraries, tools, code, and even the runtime—into a neat container that works seamlessly anywhere.
    
* Whether you're on your local machine, a server, or in the cloud, you can **unpack** this container, and it will work exactly as intended.
    

---

### **What is Containerization?** 🧳

Imagine you're packing for a trip. Instead of throwing your clothes, shoes, and toiletries all over the car, you organize them neatly into suitcases.

📦**Containerization** works the same way for applications:

* It packages everything an app needs—code, libraries, dependencies, and runtime—into a **container**.
    
* These containers are **lightweight and portable**, so your app runs reliably no matter where it's deployed.
    

---

### **Essential Docker Commands 🐧**

#### 1️⃣ **Run Your First Container** 🐣

```plaintext
docker run hello-world
```

* Downloads the `hello-world` image if it’s not already on your system.
    
* Starts a container that prints a welcome message.
    
* Confirms Docker is installed and running properly.
    

---

#### 2️⃣ **List Running Containers** 📋

```plaintext
docker ps
```

* Shows all containers currently running.
    

---

#### 3️⃣ **List All Containers (Running + Stopped)** 🗂️

```plaintext
docker ps -a
```

* Displays all containers, whether they’re running or stopped.
    

---

#### 4️⃣ **Inspect a Container or Image** 🔎

```plaintext
docker inspect <container_name_or_id>
```

* Shows detailed information about a container or image, like configurations, network settings, and file mounts.
    

---

#### 5️⃣ **Check Port Mappings** 🌐

```plaintext
docker port <container_name_or_id>
```

* Lists which host ports are mapped to your container ports.
    

---

#### 6️⃣ **Monitor Resource Usage** 📊

```plaintext
docker stats
```

* Provides real-time stats like CPU, memory, and network usage for running containers.
    

---

#### 7️⃣ **View Running Processes** 🧑‍🍳

```plaintext
docker top <container_name_or_id>
```

* Lists the processes running inside the container.
    

---

#### 8️⃣ **Save an Image to a File** 💾

```plaintext
docker save -o <file_name.tar> <image_name>
```

* Saves a Docker image to a `.tar` file.
    

---

#### 9️⃣ **Load an Image from a File** 📂

```plaintext
docker load -i <file_name.tar>
```

* Loads a Docker image from a `.tar` archive.
    

---

### **📝Dockerfile : The Recipe for Your Containers.**

#### create a Docker image. 🛠️

```plaintext
# Use a base image
FROM python:3.8-slim

# Set the working directory
WORKDIR /app

# Copy application files into the container
COPY . .

# Install dependencies
RUN pip install -r requirements.txt

# Run the app
CMD ["python", "app.py"]
```

---

#### **How to Use a Dockerfile?**

1. ### **Build the Docker Image 🏗️**
    

```plaintext
docker build -t my-python-app .
```

  
1️⃣ `docker build` : This command tells Docker to create an image.  
2️⃣ `-t my-python-app` : The `-t` flag gives the image a tag (name) for easy reference. Here, the image is named `my-python-app`.  
3️⃣ `.` : The dot specifies the current directory as the context, which contains the **Dockerfile** and app files.

---

2. ### Run the Container **🚀**
    

```plaintext
docker run -p 5000:5000 my-python-app
```

  
1️⃣ `docker run`: Starts a new container from a specified image.  
2️⃣ `-p 5000:5000`: Maps port 5000 on your local machine to port 5000 inside the container.

* **First 5000**: Port on your machine (host).
    
* **Second 5000**: Port inside the container.
    
* This allows your app running inside the container to be accessed locally on port 5000.
    

3️⃣ `my-python-app`: The name of the image to run as a container.

---

### 📜**How Docker Workflow Works?**

1. **Write a Dockerfile** (Recipe) 📝
    
2. **Build a Docker Image** (Pre-packaged app) 📦
    
3. **Run a Docker Container** (The app in action) 🚢
    

---

### **Closing Thoughts** 💡

Docker is a powerful tool that makes application deployment fast, reliable, and fun! Happy Dockering! 🐳

---
