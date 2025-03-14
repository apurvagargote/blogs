---
title: "🚀 Docker Compose for DevOps Engineers."
datePublished: Fri Feb 21 2025 12:31:05 GMT+0000 (Coordinated Universal Time)
cuid: cm7er27el00010al89cj73i8c
slug: docker-compose-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740140983777/8e1edf2b-f286-4958-a2f5-bad29fd7262a.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1740141053801/5ca17b19-b723-4dad-97f3-59a973615bcb.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

## 🚀 What is Docker Compose?

Docker Compose is a tool designed to **define and run multi-container applications** using a simple YAML file. Instead of manually running multiple `docker run` commands, Compose lets you:

✅ **Define services** in a `docker-compose.yml` file  
✅ **Spin up all containers** with a single command  
✅ **Easily manage dependencies** between containers  
✅ **Pass environment variables** and configurations efficiently

### 📜 What is YAML?

YAML (Yet Another Markup Language or YAML Ain’t Markup Language) is a human-readable format used for writing configuration files.  
🔹 Uses `.yml` or `.yaml` extensions  
🔹 Follows an **indentation-based** structure  
🔹 Easily readable and widely used in DevOps

---

## 🏗️ **Task 1: Understanding docker-compose.yml**

To get hands-on with Docker Compose, learn how to:

1️⃣ **Set up an environment** using `docker-compose.yml`  
2️⃣ **Configure multiple services** within the file  
3️⃣ **Link containers** so they communicate with each other  
4️⃣ **Use environment variables** in the YAML file

### 🎯 Sample `docker-compose.yml` File

Here’s a simple example of a `docker-compose.yml` file that runs an **NGINX** server and a **PostgreSQL** database together:

```plaintext
version: '3.8'

networks:
  mynetwork:  # Custom network name

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    depends_on:
      - db
    networks:
      - mynetwork  # Attach web to custom network

  db:
    image: postgres:latest
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      POSTGRES_DB: mydatabase
    networks:
      - mynetwork  # Attach db to the same network
```

### **🛠️ Breakdown**

✅ `networks`

* `networks:` defines a **custom bridge network** called `mynetwork`.
    
* Both `web` and `db` services are attached to `mynetwork`.
    
* Now, `web` can connect to `db` using `db:5432` (PostgreSQL default port).
    

✅ `web` (NGINX Service)

* Uses `nginx:latest` image.
    
* Exposes [`http://localhost:8080`](http://localhost:8080) by mapping host port `8080` → container port `80`.
    
* `depends_on: db` ensures the **database starts first** (but doesn’t check if it’s fully ready).
    

✅ `db` (PostgreSQL Service)

* Uses `postgres:latest` image.
    
* **Environment variables** configure:
    
    * `POSTGRES_USER`: Username (**myuser**)
        
    * `POSTGRES_PASSWORD`: Password (**mypassword**)
        
    * `POSTGRES_DB`: Default database (**mydatabase**)
        

---

### **🚀 How to Run?**

1️⃣ **Start containers:**

```plaintext
docker-compose up -d
```

2️⃣ **Stop and remove containers:**

```plaintext
docker-compose down
```

---

## 🛠️ **Task 2: Pull and Run a Docker Image**

Now, let’s pull and run a Docker container step by step:

### 1️⃣ **Pull a Docker Image**

Download an existing image (e.g., NGINX) from **Docker Hub**:

```plaintext
docker pull nginx:latest
```

### 2️⃣ **Run the Container as a Non-Root User**

By default, Docker runs as root, which is **not secure**. To run Docker without `sudo`, add your user to the Docker group:

```plaintext
sudo usermod -aG docker $USER
```

**Reboot the machine** to apply the changes:

```plaintext
sudo reboot
```

### 3️⃣ **Start the Container**

Run the NGINX container in detached mode (`-d`):

```plaintext
docker run -d --name my-nginx -p 8080:80 nginx
```

🌐 Now, visit [`http://localhost:8080`](http://localhost:8080) to see NGINX in action!

### 4️⃣ **Inspect the Running Container**

Check running processes and exposed ports:

```plaintext
docker inspect my-nginx
```

### 5️⃣ **View Logs**

Check the container logs to debug issues:

```plaintext
docker logs my-nginx
```

### 6️⃣ **Stop and Restart the Container**

To **stop** the container:

```plaintext
docker stop my-nginx
```

To **start** it again:

```plaintext
docker start my-nginx
```

### 7️⃣ **Remove the Container**

Once you're done, clean up the container:

```plaintext
docker rm my-nginx
```

---

## 🎯 **Summary**

🔹 **Docker Compose** simplifies managing multi-container apps using a YAML file.  
🔹 **YAML** is a human-friendly configuration format for DevOps tools.  
🔹 **Running Docker without sudo** improves security and ease of use.  

---
