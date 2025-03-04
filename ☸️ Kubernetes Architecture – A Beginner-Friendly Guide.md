---
title: "☸️ Kubernetes Architecture – A Beginner-Friendly Guide"
datePublished: Tue Mar 04 2025 11:06:37 GMT+0000 (Coordinated Universal Time)
cuid: cm7udvy40000s09l55y7uabi5
slug: kubernetes-architecture-a-beginner-friendly-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741086343532/6e0c2094-92be-4618-b0d2-7eb139ab5e96.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741086385072/2474fdd2-a3de-410d-8b97-dbff183d644c.jpeg
tags: kubernetes, devops, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

## 📌 What is Kubernetes?

Kubernetes (K8s) is an **open-source platform** that **automates the deployment, scaling, and management** of containerized applications.

It helps developers and DevOps teams **run applications efficiently** across multiple environments on-premise or in the cloud.

### 🔹 Quick Facts about Kubernetes

✅ **Developed by Google** and later donated to the **Cloud Native Computing Foundation (CNCF)**.  
✅ **Inspired by Google’s internal cluster management system, Borg**.  
✅ **Why "K8s"?** The **8** represents the number of letters between **K** and **s** in **Kubernetes** → **K8s**.

---

## 🎯 Why Use Kubernetes? (Key Benefits)

✅ **Automated Scaling** – Adjusts the number of running containers based on traffic.  
✅ **Self-Healing** – Restarts failed containers, replaces them, and reschedules on healthy nodes.  
✅ **Load Balancing** – Distributes traffic evenly across containers.  
✅ **Service Discovery** – Helps services find and communicate with each other.  
✅ **Declarative Configuration** – Uses YAML/JSON files to define infrastructure.  
✅ **Multi-Cloud Support** – Works on **AWS, Azure, GCP, or on-premises**.

---

![Kubernetes Architecture](https://camo.githubusercontent.com/d381547c80f03cc120dc61f5d601a2871a941075337bc7ff18ab5232aa3ed403/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f76322f726573697a653a6669743a313430302f312a30537564786575356d51794e336168693146563439412e706e67)


---

## 🏗 Kubernetes Architecture

Kubernetes follows a **Master-Worker Node Architecture**, where the **Control Plane(Master)** manages the **Worker Nodes**.

### 📌 Main Components

#### 1\] **Control Plane (Master Node)** – The "Brain" of Kubernetes

* Manages the overall cluster.
    
* Ensures workloads run where needed.
    
* ### Main Responsibilities
    
    ✅ **Schedules** workloads on worker nodes.  
    ✅ **Handles** cluster-wide decisions.  
    ✅ **Manages** communication between components.
    

#### 2\] **Worker Nodes** – The Machines Running Applications

* Handle the actual execution of applications.
    

#### 3\] **kubectl** – The Command-Line Tool

* Used to interact with Kubernetes.
    
* Sends instructions to the **API Server**.
    

---

## 🖥 Control Plane Components

Manages the entire cluster, ensuring apps run as expected.

🔹 **API Server** 🌐 – The **entry point** for all requests, like a city hall processing permits.  
🔹 **Scheduler** 📝 – Assigns workloads (pods) to worker nodes, like a dispatcher.  
🔹 **Controller Manager** ⚙️ – Watches over the cluster, fixing issues automatically.  
🔹 **etcd** 🛢 – The memory, storing all cluster configurations.

### 🏗 **Worker Nodes (The Workforce 💪)**

These are the machines where actual applications run.

🔹 **Kubelet** 🔹 – Ensures containers run properly, like a site supervisor.  
🔹 **Kube Proxy** 🔹 – Handles networking, ensuring smooth communication.  
🔹 **CNI** 🌍 – Manages IP addresses and connections between pods.

## 🎮 kubectl (Command-Line Interface)

* **Installed on the user's machine**.
    
* **Interacts with the API Server** to manage Kubernetes clusters.
    
* **Common commands:**  
    🔹 `kubectl apply` – Deploy apps  
    🔹 `kubectl get pods` – View running applications  
    🔹 `kubectl delete` – Remove applications
    

---

## 🔄 Difference Between `kubectl` and `kubelet`

| **Feature** | `kubectl` **🖥 (Command Tool)** | `kubelet` **🔗 (Worker Agent)** |
| --- | --- | --- |
| **Definition** | CLI tool to interact with the cluster. | An agent running on worker nodes. |
| **Role** | Sends commands to the API Server. | Ensures containers are running. |
| **Location** | Installed on a user's machine. | Runs on each worker node. |
| **Usage** | Used for deploying, inspecting, and managing apps. | Communicates with the Control Plane. |

---

## 🌐 The Role of the API Server

The **API Server** is the **heart** of Kubernetes. It serves as the **main gateway** for all communication inside the cluster.

### 📌 What Does the API Server Do?

✅ Accepts requests from **kubectl, UI, or other tools**.  
✅ Validates and processes those requests.  
✅ Stores cluster configurations in **etcd**.  
✅ Acts as the **single source of truth** for the cluster.

---
