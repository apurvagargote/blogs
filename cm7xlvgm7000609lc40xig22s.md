---
title: "💡Launching Your Kubernetes Cluster with Deployment."
datePublished: Thu Mar 06 2025 17:13:30 GMT+0000 (Coordinated Universal Time)
cuid: cm7xlvgm7000609lc40xig22s
slug: launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741281054493/3bb4b303-691f-4383-a892-a378d366ea0e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741281195837/078f3ac0-412f-49c9-913d-6ed0bfb67c92.png
tags: kubernetes, devops, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

## 🔍 **What is a Deployment in Kubernetes?**

A **Deployment** helps manage application **updates, scaling, and availability** by ensuring the desired number of Pods are always running.

### ✅ **Key Features of Deployments**

* **Auto-healing**: Restarts crashed Pods automatically.
    
* **Auto-scaling**: Adjusts the number of Pods based on load.
    
* **Rolling updates**: Deploy new versions with **zero downtime**.
    
* **Rollback**: Revert to a previous version if needed.
    

💡 **In simple terms:** You define how many Pods you want, and Kubernetes ensures they are running and healthy at all times.

---

## 🛠 **Task 1: Deploying a Sample Todo-App with Auto-Healing, Auto-Scaling & Rolling Updates**

Let’s deploy a **Todo App** using a **Kubernetes Deployment**.

### 📄 **Step 1: Create a Deployment File (**`deployment.yml`)

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
  labels:
    app: todo
spec:
  replicas: 3            # Ensures 3 Pods run
  strategy:
    type: RollingUpdate  # Enables rolling updates
    rollingUpdate:
      maxUnavailable: 1  # At most, 1 pod can be unavailable during the update
      maxSurge: 1        # Allows 1 extra pod to start before stopping an old one
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
        - name: todo-container
          image: your-todo-app-image:v1  # Initial version
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: todo-service
spec:
  selector:
    app: todo
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: LoadBalancer
```

### 🔹 **Step 2: Apply the Deployment to Minikube**

```plaintext
kubectl apply -f deployment.yml
```

### 🔍 **Step 3: Verify Your Deployment**

```plaintext
kubectl get pods
kubectl get deployments
kubectl get services
```

---

## **🔄 How Auto-Healing, Auto-Scaling & Rolling Updates Work in This Deployment**

### **🔹 Auto-Healing**

The **Deployment Controller** ensures at least **3 replicas** are running. If a Pod crashes, it **automatically replaces it**.

```plaintext
spec:
  replicas: 3  # Ensures 3 instances of the app run
```

💡 **Example:** If one Pod fails, Kubernetes immediately creates a new one to replace it.

---

### **🔹 Auto-Scaling**

You can enable **Horizontal Pod Autoscaler (HPA)** to automatically adjust the number of Pods based on CPU usage.

Run this command to set up **auto-scaling**:

```plaintext
kubectl autoscale deployment todo-app --cpu-percent=50 --min=2 --max=5
```

💡 **Example:** If CPU usage goes above **50%**, Kubernetes adds more Pods (up to 5). If load decreases, it scales down (minimum 2 Pods).

---

### **🔹 Rolling Updates (Zero Downtime Deployment)**

The `RollingUpdate` strategy ensures new versions are deployed **gradually** without downtime.

To update your app from `v1` to `v2`, modify the deployment:

```plaintext
containers:
  - name: todo-container
    image: your-todo-app-image:v2  # New version
```

Apply the update:

```plaintext
kubectl apply -f deployment.yml
```

💡 **How it works:**  
✅ Kubernetes **gradually replaces** old Pods with new ones.  
✅ Ensures **at least 2 Pods are always running** during updates.  
✅ Users **don’t experience downtime** while the update happens.

Check rollout status:

```plaintext
kubectl rollout status deployment/todo-app
```

---

### **🔹 Rollback (Reverting to a Previous Version)**

If the new version has issues, rollback to the last stable version with:

```plaintext
kubectl rollout undo deployment todo-app
```

💡 **How it works:**  
✅ Instantly reverts back to the last working version.  
✅ Prevents users from experiencing a broken update.

---