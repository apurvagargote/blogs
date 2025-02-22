---
title: "🚀 Docker Volumes & Networks for DevOps Engineers."
datePublished: Sat Feb 22 2025 08:51:13 GMT+0000 (Coordinated Universal Time)
cuid: cm7fynbd300010ajucliyam2p
slug: docker-volumes-and-networks-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740214103519/04a5d974-5d89-48fc-8b7b-6a0360df1a0a.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1740214145439/9a908835-0a22-4713-b681-1b0835276b05.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

## 🗄️ Docker Volumes (Persistent Storage)

By default, container data is **deleted** when a container is removed. **Volumes** store data **outside** the container so it persists even if the container is deleted.

### **📌 Key Benefits:**

✔ Data stays even if the container is removed.  
✔ Multiple containers can share the same volume.  
✔ Better performance than bind mounts.

### **🔗 Useful Commands:**

✅ **Create a volume:**

```plaintext
docker volume create my_volume
```

✅ **List all volumes:**

```plaintext
docker volume ls
```

✅ **Inspect volume details:**

```plaintext
docker volume inspect my_volume
```

✅ **Remove a volume:**

```plaintext
docker volume rm my_volume
```

---

## 🌐 Docker Network (Container Communication)

Containers **by default** are isolated. **Docker Networks** allow containers to **communicate** with each other securely.

### **📌 Network Types:**

✔ **Bridge** (Default) – Connects containers on the same host.  
✔ **Host** – Uses the host’s network directly.  
✔ **Overlay** – Used in multi-host Docker Swarm setups.

### **🔗 Useful Commands:**

✅ **Create a network:**

```plaintext
docker network create my_network
```

✅ **List all networks:**

```plaintext
docker network ls
```

✅ **Inspect network details:**

```plaintext
docker network inspect my_network
```

✅ **Remove a network:**

```plaintext
docker network rm my_network
```

---

## 🏗️ Task 1: Multi-Container Setup Using Docker Compose

Let's create a **multi-container setup** with an application and a database using **docker-compose** which uses volume and network concept.

### **🔗 Example** `docker-compose.yml` file:

```plaintext
version: '3.8'

services:
  app:
    image: my-app
    networks:
      - my_network
    depends_on:
      - db

  db:
    image: postgres
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - my_network

volumes:
  db_data:

networks:
  my_network:
```

### **📌 Running the Setup:**

✅ **Start containers in detached mode:**

```plaintext
docker-compose up -d
```

✅ **Stop and clean up everything:**

```plaintext
docker-compose down
```

---

## 📂 Task 2: Share Data Between Containers Using Volumes

Let's create **two containers** that share the same volume and verify data persistence.

### ✅ **Run two containers with a shared volume:**

```plaintext
docker run -d --name c1 --mount source=shared_vol,target=/data busybox  
docker run -d --name c2 --mount source=shared_vol,target=/data busybox  
```

#### 🔹 Explanation:

* `docker run` → Starts a new container.
    
* `-d` → Runs the container in **detached mode** (in the background).
    
* `--name c1` → Assigns the name `c1` to the first container.
    
* `--mount source=shared_vol,target=/data` →
    
    * **source=shared\_vol** → Uses a **named volume** called `shared_vol`.
        
    * **target=/data** → Mounts it inside the container at `/data`.
        
* `busybox` → A lightweight Linux-based container image.
    

Both `c1` and `c2` use **the same volume**, meaning they can **share** data.

---

### ✅ **Write data in container1:**

```
docker exec c1 sh -c "echo 'Hello from container1' > /data/message.txt"
```

#### 🔹 Explanation:

* `docker exec c1` → Runs a command inside the running container `c1`.
    
* `sh -c` → Executes the following shell command.
    
* `echo 'Hello from container1' > /data/message.txt` →
    
    * Writes "Hello from container1" into the file `/data/message.txt`.
        
    * Since `/data` is a shared volume, this file is accessible from `c2`.
        

---

### ✅ **Read data from container2:**

```plaintext
docker exec c2 cat /data/message.txt
```

#### 🔹 Explanation:

* `docker exec c2` → Runs a command inside the `c2` container.
    
* `cat /data/message.txt` → Reads and displays the content of `message.txt`.
    
* Since `c1` wrote the file to the **shared volume**, `c2` can now read it! ✅
    

---

### ✅ **List all volumes:**

```plaintext
docker volume ls
```

---

### ✅ **Remove the volume when done:**

```plaintext
docker volume rm shared_vol
```

---