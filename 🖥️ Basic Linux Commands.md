---
title: "🖥️ Basic Linux Commands"
datePublished: Wed Feb 05 2025 08:50:31 GMT+0000 (Coordinated Universal Time)
cuid: cm6ro4xd7000009le00sdg445
slug: basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738744979226/4a5601ea-fbe8-44b9-92e3-d72061fddc9c.png
tags: 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

## 📂 **1\. Listing Commands (**`ls`)

* `ls` → 📋 List files and directories.
    
* `ls -l` → 📜 Detailed list with permissions, size, owner, etc.
    
* `ls -a` → 👀 Show **hidden files**.
    
* `ls -lh` → 📏 Human-readable file sizes.
    
* `ls -d */` → 📁 List **only directories**.
    
* `ls *.sh` → 🛠️ Show **only** `.sh` files.
    

🔹 **Example:**

```
ls -lh
ls -a
```

---

## 📁 **2\. Directory Commands**

* `pwd` → 📌 Show **current directory path**.
    
* `cd folder` → 🔄 Change directory.
    
* `cd ..` → ⬆️ Move **one level up**.
    
* `cd -` → 🔙 Switch to **previous directory**.
    
* `cd ~` → 🏠 Go to the **home directory**.
    

### 📂 **Creating Directories (**`mkdir`)

* `mkdir newFolder` → 🏗️ Create **a new folder**.
    
* `mkdir .NewFolder` → 👀 Create a **hidden folder**.
    
* `mkdir A B C D` → 📂 Create **multiple folders at once**.
    
* `mkdir /home/user/Mydirectory` → 📍 Create a **folder in a specific location**.
    
* `mkdir -p A/B/C/D` → 🔀 Create **nested directories**.
    

🔹 **Example:**

```
mkdir newFolder
mkdir .NewFolder
mkdir A B C D
mkdir /home/user/Mydirectory
mkdir -p A/B/C/D
```

### 📂 **Deleting Directories (**`rmdir`, `rm -r`)

* `rmdir folder` → ❌ Remove **empty directory**.
    
* `rm -r folder` → 🚨 Remove **non-empty directory**.
    

🔹 **Example:**

```
rmdir emptyFolder
rm -r oldFolder
```

---

## 📄 **3\. File Management**

* `touch file.txt` → 📄 Create a **new empty file**.
    
* `cat file.txt` → 📖 View file content.
    
* `cp file1 file2` → 📑 Copy file.
    
* `mv old new` → ✏️ Rename/move file.
    
* `rm file.txt` → ❌ Delete a file.
    
* `vim file.txt` → ✍️ Open file in the **Vim text editor**.
    

🔹 **Example:**

```
touch notes.txt
cp notes.txt backup.txt
rm unwanted.txt
vim myfile.txt
```

---

## 🔎 **4\. Searching Files & Text**

* `find /path -name filename` → 🔍 Find **file by name**.
    
* `grep "word" file.txt` → 🔎 Search **inside a file**.
    

🔹 **Example:**

```
find /home -name "notes.txt"
grep "error" log.txt
```

---

## ⚙️ **5\. System & Process Management**

* `df -h` → 💾 Check **disk space**.
    
* `free -m` → 🔋 Check **RAM usage**.
    
* `top` → 📊 View **real-time system processes**.
    
* `kill PID` → ❌ Stop a process of mentioned process ID (PID).
    

🔹 **Example:**

```plaintext
df -h
top
kill 1234
```
