---
title: "🚀 Kubernetes Namespaces & Services."
datePublished: Fri Mar 07 2025 15:08:11 GMT+0000 (Coordinated Universal Time)
cuid: cm7ywu5sm000109l78vvq95ww
slug: kubernetes-namespaces-and-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741360021470/65777fed-8860-4627-91b5-67333bac749a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741360079381/af092965-8bac-499d-a0e9-cb0110fb6735.png
tags: kubernetes, devops, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

## 📌 Understanding Namespaces in Kubernetes

Namespaces in Kubernetes provide a way to create isolated environments within a cluster. They help organize and manage resources efficiently, especially in multi-team or multi-project scenarios.

### 🔹 Key Features of Namespaces:

* **Isolation:** Resources within a Namespace do not interfere with those in another.
    
* **Logical Grouping:** Makes managing large applications easier.
    
* **Access Control:** Helps in applying resource limits and security policies.
    
* **Default Namespace:** If no Namespace is specified, resources are created in the `default` Namespace.
    

👉 **Create a Namespace using:**

```plaintext
kubectl create namespace my-namespace
```

---

## 📌 Understanding Services in Kubernetes

A **Service** provides a stable way to access and communicate with Pods, ensuring connectivity even if Pods are restarted or rescheduled.

### 🔹 Types of Kubernetes Services:

1. **ClusterIP (Default):**
    
    * Exposes the Service within the cluster.
        
    * Used for internal communication between Pods.
        
2. **NodePort:**
    
    * Exposes the Service on a static port on each node.
        
    * Can be accessed externally using `<NodeIP>:<NodePort>`.
        
3. **LoadBalancer:**
    
    * Uses an external load balancer to expose the Service outside the cluster.
        
    * Common in cloud environments like AWS, GCP, and Azure.
        
4. **ExternalName:**
    
    * Maps the Service to an external DNS name.
        
    * Useful for connecting to external services.
        
5. **Headless Service (No ClusterIP):**
    
    * Used when **direct Pod discovery** is required instead of a single Service IP.
        
    * Does **not** assign a ClusterIP.
        
    * Kubernetes DNS returns the **IP addresses of all matching Pods**, allowing direct communication.
        

---

## ✅ Task 1: Create a Namespace for Your Deployment

1️⃣ **Create a Namespace:**

```plaintext
kubectl create namespace my-namespace
```

2️⃣ **Update the** `deployment.yml` file to include the Namespace:

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  namespace: my-namespace      # Specify the Namespace
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: my-image:latest
```

3️⃣ **Apply the updated deployment:**

```plaintext
kubectl apply -f deployment.yml -n my-namespace
```

4️⃣ **Verify the Namespace creation:**

```plaintext
kubectl get namespaces
```

---

## ✅ Task 2: Learn About Services, Load Balancing & Networking

### 🔹 **How Kubernetes Services Expose and Route Traffic to Pods**

* Kubernetes **Services** act as a stable entry point to access Pods, even if Pods are restarted or rescheduled.
    
* They use **labels and selectors** to route traffic to the correct set of Pods.
    
* When a request comes to a Service, it **distributes** it across multiple Pods matching the selector.
    
* **Example:** A backend application with multiple replicas can be accessed via a single Service.
    

---

### 🔹 **Networking in Kubernetes and How Pods Communicate**

* Each Pod in Kubernetes has a **unique IP address**.
    
* Pods can communicate directly **within the same Node** or **across Nodes** using Kubernetes networking rules.
    
* **Kube-proxy** manages networking rules that allow traffic between Services and Pods.
    
* **CNI (Container Network Interface)** plugins like Calico, Flannel, and Cilium are used to define network policies.
    

📌 **Common Network Scenarios:**  
✔ **Pod-to-Pod Communication** – Direct IP-based communication.  
✔ **Pod-to-Service Communication** – Pods use the Service name (DNS) to connect to backend Pods.  
✔ **Ingress Communication** – External traffic enters the cluster via an Ingress Controller.

---

### 🔹 **Load Balancing Mechanisms in Kubernetes**

Load balancing ensures that traffic is **distributed efficiently** across multiple Pods to improve availability and reliability.

✅ **Types of Load Balancing in Kubernetes:**

1. **Internal Load Balancing:**
    
    * Kubernetes Services distribute traffic among multiple Pods.
        
    * Uses **ClusterIP** (for internal traffic) and **kube-proxy** to route requests.
        
2. **External Load Balancing:**
    
    * Uses **LoadBalancer Service** (if running in a cloud environment).
        
    * The cloud provider creates an external Load Balancer to distribute traffic.
        
3. **Ingress Load Balancing:**
    
    * Manages HTTP/HTTPS traffic and routes requests to different Services.
        
    * Requires an **Ingress Controller** like Nginx or Traefik.
        

📌 **Example of LoadBalancer Service:**

```plaintext
apiVersion: v1
kind: Service
metadata:
  name: my-loadbalancer
spec:
  selector:
    app: my-app
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 8080
```

---

## 📌 **Summary Table**

| Concept | Description |
| --- | --- |
| **Service** | Provides a stable way to expose and route traffic to Pods. |
| **Networking** | Ensures Pods can communicate across the cluster. |
| **Load Balancing** | Distributes traffic efficiently for reliability and availability. |