---
title: "🚀 Mastering ConfigMaps and Secrets in Kubernetes."
datePublished: Wed Mar 12 2025 10:36:15 GMT+0000 (Coordinated Universal Time)
cuid: cm85sbppc000909jr8ig92zg1
slug: mastering-configmaps-and-secrets-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741775528678/c2ea87a5-682e-42ac-acc0-0a6892770fb7.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741775759709/c88994ab-9e91-4e12-838e-31bce399d849.webp
tags: kubernetes, devops, 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, kubernetes-configmap, 90daysofdevopschallenge

---

## **1️⃣ Task: Creating a ConfigMap**

### **📝 Method 1: Using a YAML File**

Create a file named `configmap.yml` and add the following content:

```plaintext
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config    # Name of the ConfigMap
data:
  APP_ENV: "production"  # Environment setting
  LOG_LEVEL: "debug"  # Logging level
```

📌 **Explanation**:

* `apiVersion: v1` → Specifies the Kubernetes API version.
    
* `kind: ConfigMap` → Defines that this is a ConfigMap.
    
* [`metadata.name`](http://metadata.name)`: my-config` → Assigns a name to the ConfigMap.
    
* `data` → Stores key-value pairs used for configuration.
    

### **🔹 Apply the ConfigMap using the command**:

```plaintext
kubectl apply -f configmap.yml -n <namespace-name>
```

📌 **What this does**:

* Applies the `configmap.yml` file to the specified namespace in Kubernetes.
    

### **📝 Method 2: Using the Command Line**

If you don’t want to create a file, you can create a ConfigMap directly with this command:

```plaintext
kubectl create configmap my-config --from-literal=APP_ENV=production --from-literal=LOG_LEVEL=debug -n <namespace-name>
```

📌 **Explanation**:

* `kubectl create configmap` → Command to create a ConfigMap.
    
* `my-config` → Name of the ConfigMap.
    
* `--from-literal=APP_ENV=production` → Directly sets a key-value pair (`APP_ENV=production`).
    
* `-n <namespace-name>` → Specifies the namespace where the ConfigMap will be created.
    

### **🔎 Verify that the ConfigMap is created**

```plaintext
kubectl get configmaps -n <namespace-name>
```

📌 **Shows a list of ConfigMaps in the specified namespace.**

```plaintext
kubectl describe configmap my-config -n <namespace-name>
```

📌 **Displays details about the** `my-config` ConfigMap.

---

## **2️⃣ Task: Using the ConfigMap in a Deployment**

Modify your `deployment.yml` file to use the ConfigMap:

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
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
          image: nginx
          envFrom:
            - configMapRef:
                name: my-config  # Using the ConfigMap in the container
```

📌 **Explanation**:

* [`envFrom.configMapRef.name`](http://envFrom.configMapRef.name)`: my-config` → Loads all key-value pairs from the ConfigMap into environment variables for the container.
    

### **🔹 Apply the updated Deployment**

```plaintext
kubectl apply -f deployment.yml -n <namespace-name>
```

---

## **3️⃣ Task: Creating a Secret**

### **📝 Method 1: Using a YAML File**

Create a file named `secret.yml`:

```plaintext
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  DB_PASSWORD: cGFzc3dvcmQ=  # Base64 encoded password (password)
```

### **📌 Encoding the Secret in Base64**

Run the following command in your **terminal** to generate the Base64-encoded password:

```plaintext
echo -n "password" | base64
```

✅ Example Output:

```plaintext
cGFzc3dvcmQ=
```

📌 **Explanation**:

* `kind: Secret` → Defines that this is a Secret.
    
* `type: Opaque` → Specifies an arbitrary secret type.
    
* `data.DB_PASSWORD: cGFzc3dvcmQ=` → Base64-encoded value for **password** (`password` encoded in Base64).
    

### **🔹 Apply the Secret**

```plaintext
kubectl apply -f secret.yml -n <namespace-name>
```

### **📝 Method 2: Using the Command Line**

```plaintext
kubectl create secret generic my-secret --from-literal=DB_PASSWORD=password -n <namespace-name>
```

📌 **Explanation**:

* `kubectl create secret generic` → Creates a generic Secret.
    
* `my-secret` → Name of the Secret.
    
* `--from-literal=DB_PASSWORD=password` → Adds a key-value pair with `DB_PASSWORD=password`.
    
* Kubernetes automatically encodes the value in Base64.
    

### **🔎 Verify that the Secret is created**

```plaintext
kubectl get secrets -n <namespace-name>
```

📌 **Lists all Secrets in the namespace.**

```plaintext
kubectl describe secret my-secret -n <namespace-name>
```

📌 **Shows detailed information about the Secret.**

---

## **4️⃣ Task: Using the Secret in a Deployment**

Modify your `deployment.yml` file:

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
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
          image: nginx
          env:
            - name: DB_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: my-secret  # Using the Secret in the container
                  key: DB_PASSWORD
```

📌 **Explanation**:

* [`env.name`](http://env.name)`: DB_PASSWORD` → The environment variable inside the container.
    
* [`valueFrom.secretKeyRef.name`](http://valueFrom.secretKeyRef.name)`: my-secret` → Refers to the Kubernetes Secret named `my-secret`.
    
* `valueFrom.secretKeyRef.key: DB_PASSWORD` → Uses the `DB_PASSWORD` key from the Secret.
    

### **🔹 Apply the updated Deployment**

```plaintext
kubectl apply -f deployment.yml -n <namespace-name>
```