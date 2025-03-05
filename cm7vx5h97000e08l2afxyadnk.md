---
title: "🚀Launching Your First Kubernetes Cluster with Kind & Nginx"
datePublished: Wed Mar 05 2025 12:53:40 GMT+0000 (Coordinated Universal Time)
cuid: cm7vx5h97000e08l2afxyadnk
slug: launching-your-first-kubernetes-cluster-with-kind-and-nginx
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741179031855/56380d5d-a594-4ab7-8d81-1e35b38efa98.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741179201247/5b34ec58-5b6b-4d63-aca6-dd66e22a9b34.png
tags: kubernetes, devops, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge, kubernetespods

---

Let's take it a step further with **hands-on practice** by setting up a **Kubernetes cluster** using **Kind** **(Kubernetes in Docker)** and creating **Nginx pod** as our first pod! 🚀

---

## 🔍 What is Kind?

**Kind (Kubernetes in Docker)** is a lightweight tool that lets you quickly create **Kubernetes clusters inside Docker containers**. It's a great alternative to Minikube for **local development, testing, and CI/CD pipelines**.

### ✨ Features of Kind:

✅ Runs Kubernetes **inside Docker** 🐳  
✅ **Lightweight & fast** 🚀  
✅ Supports **multiple Kubernetes versions**  
✅ Works on **Linux, macOS, and Windows**  
✅ Perfect for **testing Kubernetes workloads locally**

---

## 🛠️ Task-01: Install Kind

🔹 First, install Kind by following the official guide: [`Kind Installation`](https://kind.sigs.k8s.io/docs/user/quick-start/).  
🔹 Ensure [`Docker`](https://docs.docker.com/engine/install/) is installed before proceeding.

### ✅ **Create a Kind Cluster**

Once installed, create a Kubernetes cluster using:

```plaintext
kind create cluster --name my-cluster
```

To verify, run:

```plaintext
kubectl cluster-info --context kind-my-cluster
```

---

## 🔹 Understanding Kubernetes Pods

### 🤔 What is a Pod?

A **Pod** is the **smallest deployable unit** in Kubernetes. It consists of:

* **One or more containers** 🐳
    
* **Shared storage & network**
    
* **A specification defining how to run the containers**
    

A Pod acts as a **"logical host"**, ensuring all its containers run together efficiently.

---

## 🛠️ Task-02: **Create a Pod Definition (nginx-pod.yaml)**

```plaintext
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
    - name: nginx-container
      image: nginx:latest
      ports:
        - containerPort: 80
```

### 🛠 Explanation:

1. `apiVersion: v1` → Uses **v1** API for Kubernetes objects.
    
2. `kind: Pod` → Defines this as a Pod resource.
    
3. `metadata`:
    
    * `name: nginx-pod` → Assigns a name to the Pod.
        
    * `labels: app: nginx` → Adds a label for easy identification.
        
4. `spec`:
    
    * `containers` → Lists the containers within the pod.
        
    * `name: nginx-container` → Names the container inside the pod.
        
    * `image: nginx:latest` → Uses the latest **Nginx** Docker image.
        
    * `ports: containerPort: 80` → Exposes port 80 for web traffic (HTTP).
        

### ✅ **Apply the YAML file**

```plaintext
kubectl apply -f nginx-pod.yaml
```

Check if the Pod is running:

```plaintext
kubectl get pods
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1741178797674/a57d8fc7-5d7c-4187-b516-05fa363d7141.png align="center")

🎉 **Congrats! You've successfully created an Nginx Pod.**