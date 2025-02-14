---
title: "🖥️ Advanced Linux Commands"
datePublished: Thu Feb 06 2025 15:08:22 GMT+0000 (Coordinated Universal Time)
cuid: cm6th2ov8000509l4gi8vboh6
slug: advanced-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738853759999/8997f21a-9377-4e05-8ac6-53e0dec435ff.jpeg
tags: 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

## 1\. **🔐 Advanced File Permissions & Ownership**

**File Permissions in Linux:**

* **r**: Read (4) 📖
    
* **w**: Write (2) ✍️
    
* **x**: Execute (1) ▶️
    

Permissions are added together to set them.

#### **🔧 Modify File Permissions (chmod)**

* **✅ Give full permission to the owner, read-execute to others:**
    
    ```
    chmod 755 script.sh
    ```
    
    * **7** → Owner permission: Read (4) + Write (2) + Execute (1) = 7
        
    * **5** → Group permission: Read (4) + Execute (1) = 5
        
    * **5** → Others permission: Read (4) + Execute (1) = 5
        
* **❌ Make a file read-only for everyone:**
    
    ```
    chmod 444 important.txt
    ```
    
    * 🔒 No one can modify the file because Write (2) is removed.
        
* **🚫 Remove execute permission from a file:**
    
    ```
    chmod -x file.sh
    ```
    
    * The `-x` removes execute permission from the file.
        

#### **👤 Change File Ownership (chown & chgrp)**

* **👤 Change the file owner:**
    
    ```
    sudo chown newuser file.txt
    ```
    
    * `newuser` becomes the owner of `file.txt`.
        
* **👥 Change both owner and group:**
    
    ```
    sudo chown newuser:newgroup file.txt
    ```
    
    * `newuser` is the new owner.
        
    * `newgroup` is the new group.
        

---

### 2\. **🌐 Network Monitoring & Troubleshooting**

#### **🔍 Check Open Network Connections (netstat, ss)**

* **📶 List all open ports and services:**
    
    ```
    netstat -tulnp
    ```
    
    * **t**: Shows TCP connections.
        
    * **u**: Shows UDP connections.
        
    * **l**: Shows listening ports.
        
    * **n**: Displays numeric addresses.
        
    * **p**: Shows process ID (PID).
        
* **🌍 Check listening ports (alternative to netstat):**
    
    ```
    ss -tulnp
    ```
    
    * ⚡ Faster alternative to `netstat`.
        

#### **🛠️ Network Diagnostics (ping, nslookup, traceroute)**

* **🔄 Test network connectivity:**
    
    ```
    ping google.com
    ```
    
    * Sends ICMP echo requests to check if [`google.com`](http://google.com) is reachable.
        
* **🌐 Get DNS information of a domain:**
    
    ```
    nslookup google.com
    ```
    
    * Resolves the IP address of [`google.com`](http://google.com) using DNS lookup.
        
* **🏃 Trace the route packets take to a destination:**
    
    ```
    traceroute google.com
    ```
    
    * Shows each hop (router) a packet takes to reach [`google.com`](http://google.com).
        

---

### 3\. **💽 Transfer Files Over SSH (scp)**

* **📂 Copy a file to a remote server:**
    
    ```
    scp file.txt user@remote:/path/
    ```
    
    * Securely copies `file.txt` from your local machine to `/path/` on the remote server.
        

---

### 4\. **🔑 SSH Command for Remote Access**

* **🚀 Access a remote server using SSH:**
    
    ```plaintext
    ssh user@remote
    ```
    
    * `ssh`: Securely logs you into a remote server.
        
    * `user`: Replace with the username on the remote server.
        
    * `remote`: Replace with the server's IP address or hostname (e.g., `192.168.1.10`).
        

---

### 5\. **⏳ Automation & Scheduling Tasks (cron)**

#### **⌚ Schedule Jobs with Cron**

* **📝 Edit the cron table:**
    
    ```
    crontab -e
    ```
    
    * Opens the cron job editor.
        
* **💾 Schedule a backup every day at midnight:**
    
    ```
    0 * * * * /home/user/backup.sh
    ```
    
    * This cron job will run `/home/user/`[`backup.sh`](http://backup.sh) at the start of every hour.
        

**Format breakdown:**

* **0** : Minute (0–59)
    
* **\*** : Hour (0–23)
    
* **\*** : Day (1–31)
    
* **\*** : Month (1–12)
    
* **\*** : Day of the week (0–7)