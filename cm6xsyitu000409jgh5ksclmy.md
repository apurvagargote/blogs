---
title: "🔒 Linux File Permissions, ACLs & Special Permissions! 🚀"
datePublished: Sun Feb 09 2025 15:52:07 GMT+0000 (Coordinated Universal Time)
cuid: cm6xsyitu000409jgh5ksclmy
slug: linux-file-permissions-acls-special-permissions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739116173932/5ed184a4-0168-47b6-9716-d3aa4ea14cb2.jpeg
tags: 90daysofdevops

---

---

## 📌 1. Understanding File Permissions

Every file and directory in Linux has **three sets of permissions** for **three types of users**:

👤 **Owner** – The user who created the file.  
👥 **Group** – A set of users who share access.  
🌍 **Others** – Anyone else with system access.

Each file permission is made up of **three types of actions**:

* **r (read) 👀** – Can **view** the contents of a file.
    
* **w (write) ✍️** – Can **modify** the file or add/remove content.
    
* **x (execute) 🚀** – Can **run** the file if it’s a script or program.
    

### 📌 Example of File Permissions

Run this command to see file permissions:

```plaintext
ls -ltr
```

Example output:

```plaintext
-rwxr--r-- 1 user group 1234 Feb 9 12:00 myfile.txt
```

Let's break this down:

* `-rwxr--r--` → The first section shows permissions.
    
    * `rwx` → **Owner** can read, write, and execute.
        
    * `r--` → **Group** can only read.
        
    * `r--` → **Others** can only read.
        
* `user` → The owner of the file.
    
* `group` → The group that owns the file.
    
* `1234` → File size in bytes.
    
* `Feb 9 12:00` → Last modified date and time.
    
* `myfile.txt` → File name.
    

---

## 🎯 2. Changing File Permissions

### 🛠 Change File Permissions

You can modify **who can read, write, or execute** a file using `chmod`.

#### 🔹 Add or Remove Specific Permissions

```plaintext
tchmod u+x file.txt  # Give execute permission to owner
chmod g-w file.txt  # Remove write permission from group
chmod o-r file.txt  # Remove read permission from others
```

* `u` → Owner
    
* `g` → Group
    
* `o` → Others
    
* `+` → Add permission
    
* `-` → Remove permission
    

#### 🔹 Change Permissions Using Numbers

Each permission type has a number:

* `r` = 4 (Read)
    
* `w` = 2 (Write)
    
* `x` = 1 (Execute)
    

To **set permissions for owner, group, and others**, sum up the values:

```plaintext
chmod 755 file.txt
```

**Breakdown of** `755`:

* `7` → **Owner** = `rwx` (4+2+1 = 7)
    
* `5` → **Group** = `r-x` (4+0+1 = 5)
    
* `5` → **Others** = `r-x` (4+0+1 = 5)
    

---

### 🛠 Change Ownership of a File

When a file is created, it **automatically belongs** to the user who created it. You can change this using:

#### 🔹 Change File Owner

```plaintext
chown new_owner file.txt
```

* **Example:** If you want to change the owner of `report.txt` to `alice`:
    
    ```plaintext
    chown alice report.txt
    ```
    

#### 🔹 Change Group Ownership

```plaintext
chgrp new_group file.txt
```

* **Example:** If you want to change the group of `data.csv` to `developers`:
    
    ```plaintext
    chgrp developers data.csv
    ```
    

---

## 🏆 3. Access Control Lists (ACLs) – Advanced Permissions

Linux **Access Control Lists (ACLs)** allow **more flexible** permission management. Instead of just **Owner, Group, Others**, you can **assign specific permissions to individual users**.

### 🛠 View ACL Permissions

```plaintext
getfacl file.txt
```

* This shows **detailed permissions** including special ACL settings.
    

### 🛠 Set ACL for a Specific User

```plaintext
setfacl -m u:username:rwx file.txt
```

* **Example:** Give full access to `bob` for `notes.txt`:
    
    ```plaintext
    setfacl -m u:bob:rwx notes.txt
    ```
    

### 🛠 Remove ACL for a User

```plaintext
setfacl -x u:username file.txt
```

* **Example:** Remove `bob` from ACL of `notes.txt`:
    
    ```plaintext
    setfacl -x u:bob notes.txt
    ```
    

---

## ⚡ 4. Special Permissions: Sticky Bit, SUID, SGID

### 🎩 **Sticky Bit (👢 Protecting shared folders!)**

* Used **in shared directories** like `/tmp`.
    
* **Prevents users from deleting files they don’t own**.
    

🔹 **Set Sticky Bit**

```plaintext
chmod +t mydir
```

🔹 **Check if Sticky Bit is set**

```plaintext
ls -ld mydir
```

🔹 **Example output:** `drwxrwxrwt` (notice the `t` at the end)

---

### 🎭 **SUID (Superpower Mode! 🦸)**

* **Allows a file to run as the owner**, not the user executing it.
    
* Used for commands like `passwd` (which needs root privileges).
    

🔹 **Set SUID on a script**

```plaintext
chmod u+s script.sh
```

🔹 **Check if SUID is set**

```plaintext
ls -l script.sh
```

🔹 **Example output:** `-rwsr-xr-x` (notice the `s` in place of `x`)

---

### 🤝 **SGID (Group Magic! 🧙)**

* **Ensures new files inside a directory inherit the group**.
    
* Useful for **collaborative project folders**.
    

🔹 **Set SGID on a directory**

```plaintext
chmod g+s mydir
```

🔹 **Check if SGID is set**

```plaintext
ls -ld mydir
```

🔹 **Example output:** `drwxrwsr-x` (notice the `s` in the group section)

---

## 🛠 5. Automating Permissions with Scripts

### 📌 Change Permissions for Multiple Files

```plaintext
#!/bin/bash
echo "Enter permission (e.g., 755): "
read perm
chmod $perm *
```

* Prompts user for a permission code and applies it to **all files** in the directory.
    

---

### 📌 Set ACL for a User on a File

```plaintext
#!/bin/bash
echo "Enter username: "
read user
setfacl -m u:$user:rwx myfile.txt
```

* Prompts for a **username** and grants them **full access** to `myfile.txt`.
    

---

## 🛡️ 6. Backup & Restore Permissions

### 📌 Backup Permissions

```plaintext
getfacl -R mydir > permissions_backup.txt
```

* Saves **all file permissions** in `mydir` to `permissions_backup.txt`.
    

### 📌 Restore Permissions

```plaintext
setfacl --restore=permissions_backup.txt
```

* Restores **previously saved permissions**.