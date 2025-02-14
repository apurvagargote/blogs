---
title: "🐧 Advanced Linux Shell Scripting for DevOps Engineers"
datePublished: Sat Feb 08 2025 09:26:10 GMT+0000 (Coordinated Universal Time)
cuid: cm6vzqbp0000c09l58yoe4d1r
slug: advanced-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739006729072/24d4104b-7270-4c1c-83d3-956a27610c8c.jpeg
tags: 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

💡 **Ever wondered how to create 90 directories in seconds?** Instead of manually making each folder (`mkdir day1`, `mkdir day2`... 😩), we use automation!

---

## **1️⃣ Creating Multiple Directories in Seconds**

Let’s say we need **90 directories** named `day1`, `day2`, ..., `day90`. Instead of wasting time, a simple **one-liner** does the job:

```plaintext
mkdir day{1..90}
```

🔥 **BOOM! 90 directories created instantly!**

### **📌 But what if we need flexibility?**

We can write a **Bash script** to create **any range** of directories dynamically!

#### **📜** [`createDirectories.sh`](http://createDirectories.sh) (Bash Script to Create Directories)

```plaintext
#!/bin/bash

# Checking if the correct number of arguments are passed
if [ $# -ne 3 ]; then
    echo "Usage: $0 <directory_name> <start_number> <end_number>"
    exit 1
fi

# Assigning arguments to variables
dir_name=$1      # First argument (Directory name prefix)
start_num=$2     # Second argument (Start number)
end_num=$3       # Third argument (End number)

# Loop to create directories
for ((i=start_num; i<=end_num; i++)); do
    mkdir "${dir_name}${i}"  # Creates directories like day1, day2...day90
done

echo "✅ Created directories from ${dir_name}${start_num} to ${dir_name}${end_num}"
```

📌 **Explanation:**  
1️⃣ **Checks if the correct number of arguments (3) are provided.** If not, it shows the correct usage and exits.  
2️⃣ **Takes directory name, start number, and end number as input.**  
3️⃣ **Loops from the start number to the end number** and creates directories dynamically using `mkdir`.  
4️⃣ **Prints a success message** after completion.

📌 **How to run this script?**

```plaintext
chmod +x createDirectories.sh       # Makes the script executable
./createDirectories.sh day 1 90     # Creates day1 to day90
./createDirectories.sh Movie 20 50  # Creates Movie20 to Movie50
```

🚀 **Now, you can generate any number of directories dynamically!**

---

## **2️⃣ Automating Backups in Linux** 🛠️

**As a DevOps Engineer, backup is life-saving!**  
Imagine accidentally deleting files... 😱 A backup script can **save your day!**

#### **📜** [`backup.sh`](http://backup.sh) (Bash Script for Backup)

```plaintext
#!/bin/bash

backup_dir="/home/$(whoami)/backup"  # Define backup directory based on the logged-in user
mkdir -p $backup_dir  # Create the backup directory if it doesn’t exist

# Create a compressed backup of the 'work' directory
tar -czf "$backup_dir/backup_$(date +%Y%m%d_%H%M%S).tar.gz" /home/$(whoami)/work

echo "✅ Backup completed! Stored in $backup_dir"
```

📌 **Explanation:**  
1️⃣ **Defines a backup directory** inside the user's home folder (`/home/username/backup`).  
2️⃣ **Creates the backup directory if it doesn’t exist** using `mkdir -p`.  
3️⃣ **Compresses the** `work` directory using `tar -czf`, saving it with a timestamp (`YYYYMMDD_HHMMSS`) to avoid overwriting.  
4️⃣ **Displays a success message** after completing the backup.

### **🤖 Automate Backups using Cron!**

Instead of running the script manually, **schedule it with** `cron`:

```plaintext
crontab -e
```

Add this line to run the backup **every night at 2 AM**:

```plaintext
0 2 * * * /path/to/backup.sh
```

📌 **Explanation:**

🔹 **0** → The **minute** when the script runs (**0th minute**).  
🔹 **2** → The **hour** when the script runs (**2 AM**).  
🔹 Scripting Secrets: Automate Everything in Linux!**\****→ The* ***day of the month*** *(runs* ***every day****).  
🔹* **\*** → The **month** (runs **every month**).  
🔹 **\*** → The **day of the week** (runs **on all days**).

🔥 **Now backups happen automatically!** No worries about data loss!

---

## **3️⃣ User Management in Linux 👥**

**Users in Linux = Separate Accounts for Different Tasks**  
💡 Linux assigns **unique IDs** to each user.  
🔹 **System Users**: IDs **0-999**  
🔹 **Local Users**: IDs **1000+**

### **📌 Create 2 Users and Display Their Names**

```plaintext
sudo useradd devops1  # Creates a new user named 'devops1'
sudo useradd devops2  # Creates another user named 'devops2'

# Display user list
cut -d: -f1 /etc/passwd | tail -n 5
```

📌 **Explanation:**  
1️⃣ `useradd devops1` & `useradd devops2` → Creates new users named `devops1` and `devops2`.  
2️⃣ `cut -d: -f1 /etc/passwd` → Extracts usernames from `/etc/passwd` (Linux user database).  
3️⃣ `tail -n 5` → Displays the last 5 users (including the new ones).

🚀 **Now, you’ve created users like a pro!**

---

## **🔚 Final Thoughts**

* **📁 Automated Directory Creation** → Saves Time!
    
* **💾 Backup Script + Cron Job** → Keeps Data Safe!
    
* **👤 User Management** → Controls Access in Linux!
    

**💡 DevOps is all about automation!** Start scripting, and **make Linux work for you!**