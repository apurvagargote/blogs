---
title: "🧑‍💻Python Basics for DevOps Engineers."
datePublished: Tue Feb 18 2025 07:38:56 GMT+0000 (Coordinated Universal Time)
cuid: cm7a6ay6w00030alb9y2s5ow1
slug: python-basics-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739864270072/eb178def-be50-4b88-82ec-3bd6d17ff053.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1739864312904/a7031036-11a2-4462-b09c-4ee417a91256.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

### **What is Python?** 🐍

**Python** is an easy-to-learn, **open-source**, and **general-purpose** programming language. It’s known for being readable and concise, making it perfect for DevOps tasks like automation and server management. 📝

Some cool things about Python:

* It’s used to automate **repetitive tasks**.
    
* Python integrates smoothly with DevOps tools like **Docker**, **Kubernetes**, and **AWS**.
    
* Python has an amazing collection of **libraries** and **frameworks** like:
    
    * **Django** – Web development 🕸️
        
    * **TensorFlow** – Machine Learning 🧠
        
    * **Flask** – Web frameworks 🔥
        
    * **Pandas** – Data analysis 📊
        
    * **Keras** – Deep learning 🧑‍💻
        

---

### **How to Install Python?** ⚙️

Before we get started, let’s install Python on your computer. Depending on your operating system, follow the instructions below:

#### **For Windows** 💻:

1. Go to the [Python website](https://www.python.org/downloads/).
    
2. Download and install Python, ensuring you check **"Add Python to PATH"**.
    
3. Open **Command Prompt** and type:
    
    ```plaintext
    python --version
    ```
    
    This shows the installed Python version.
    

#### **For Ubuntu (Linux)** 🐧:

1. Open the terminal and run:
    
    ```plaintext
    sudo apt-get update
    sudo apt-get install python3.6
    ```
    
2. Verify Python with:
    
    ```plaintext
    python3 --version
    ```
    

---

### **Important Python Data Types for DevOps** 💡

In Python, data comes in different types, which are used to store information in your programs. These are the most important data types for DevOps tasks:

#### **1\. Strings (str) 📜**

Strings are used to store **text data** like server names, URLs, or log messages.

#### Example:

```plaintext
server_name = "web_server"
url = "http://localhost:5000"
```

#### **2\. Lists 📝**

Lists are used to store **multiple items**. Think of them like a **to-do list** or a list of servers that need managing.

#### Example:

```plaintext
servers = ["server1", "server2", "server3"]
```

#### **3\. Dictionaries (dict) 🗃️**

Dictionaries store data in pairs (a **key** and a **value**). It’s perfect for storing things like configuration settings.

#### Example:

```plaintext
config = {
    "host": "localhost",
    "port": 8080,
    "username": "admin"
}
```

#### **4\. Booleans (bool) ✅/❌**

Booleans are used for conditions, like checking if a task was successful or if a server is online.

#### Example:

```plaintext
is_deployed = True
is_error = False
```

---

### **Conditional Statements (if/else) 🧐**

Conditional statements are used to make **decisions** in your program. You can check conditions and execute different code based on whether those conditions are **True** or **False**.

#### Example:

```plaintext
if is_deployed:
    print("Deployment Successful!")
else:
    print("Deployment Failed!")
```

This will print `"Deployment Successful!"` if `is_deployed` is `True`. Otherwise, it will print `"Deployment Failed!"`.

---

### **Loops (for/while) 🔄**

**Loops** allow you to repeat a block of code multiple times. This is super helpful in DevOps when you need to loop through a list of servers or run tasks multiple times.

#### **For Loop** (When you know how many times to loop)

```plaintext
for server in servers:
    print(f"Checking {server}")
```

#### **While Loop** (When the loop runs as long as a condition is True)

```plaintext
counter = 0
while counter < 5:
    print(f"Loop number {counter}")
    counter += 1
```

---

### **Boto3 - Managing AWS with Python** 🌩️

* **Boto3** is the official Python library for interacting with **AWS (Amazon Web Services)**. As a DevOps engineer, you'll often need to manage cloud resources like **EC2 instances**, **S3 buckets**, **Lambda functions**, and more.
    
* **Boto3** simplifies this by allowing you to create, configure, and manage AWS services with Python scripts. With Boto3, you can automate tasks like provisioning servers, storing files in the cloud, and managing security settings—making your work faster and more efficient!
    

#### **Getting Started with Boto3** 🚀

##### **Step 1: Install Boto3**

To use **Boto3**, you first need to install it on your system using `pip` (Python’s package manager):

```plaintext
pip install boto3
```

##### **Step 2: Set Up AWS Credentials**

Before you can start using **Boto3**, you’ll need to configure your **AWS credentials** (your access key and secret key). You can do this in a few different ways:

* Use the **AWS CLI** to configure it:
    
    ```plaintext
    aws configure
    ```
    

##### **Step 3: Example of Using Boto3 to List EC2 Instances**

Let’s write a simple Python script that lists all your EC2 instances in AWS.

```plaintext
import boto3

# Create an EC2 client
ec2 = boto3.client('ec2')

# List all EC2 instances
response = ec2.describe_instances()

# Print out the response
print(response)
```

In this script:

* **Import Boto3 library**: `import boto3` – to use AWS services in Python.
    
* **Create EC2 client**: `ec2 = boto3.client('ec2')` – connects to AWS EC2 service.
    
* **Describe instances**: `response = ec2.describe_instances()` – fetches details of all EC2 instances.
    
* **Print the response**: `print(response)` – outputs the instance details to the console.
    

---

### **Conclusion** 🧐

Python is an awesome tool for DevOps engineers! It helps you automate processes, manage infrastructure, and interact with services like **AWS** all while keeping things simple and efficient. 🚀

By understanding Python’s key features—like data types, loops, and conditional statements—you can write powerful scripts to manage servers, configurations, and cloud resources with ease.

And with libraries like **Boto3**, you can even automate your work with **AWS** and take your DevOps skills to the next level! ☁️

---