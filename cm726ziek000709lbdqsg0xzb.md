---
title: "🐚 Shell Scripting Challenge: Directory Backup with Rotation ."
datePublished: Wed Feb 12 2025 17:35:53 GMT+0000 (Coordinated Universal Time)
cuid: cm726ziek000709lbdqsg0xzb
slug: shell-scripting-challenge-directory-backup-with-rotation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739381667299/345e9beb-030a-4b89-a4ee-f963fd4f8f36.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

## 📋 **Challenge Description**

The task is to write a bash script that:

1. Accepts a **directory path** as a command-line argument.
    
2. Creates a **timestamped backup folder** in the specified directory.
    
3. Copies all the files from the directory into this new backup folder.
    
4. **Keeps only the last 3 backups** and deletes any older ones automatically.
    

---

## 🛠 **Shell Script:** `backup_with_`[`rotation.sh`](http://rotation.sh)

Here’s the script to handle the challenge step-by-step:

```plaintext
#!/bin/bash

# Check if a directory is provided as an argument
if [ -z "$1" ]; then
    echo "❌ Error: Please provide a directory path as an argument!"
    exit 1
fi

# Assign the directory path
DIR_PATH="$1"

# Check if the provided path exists and is a directory
if [ ! -d "$DIR_PATH" ]; then
    echo "❌ Error: The specified path does not exist or is not a directory!"
    exit 1
fi

# Generate a timestamp for the backup folder
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
BACKUP_FOLDER="backup_${TIMESTAMP}"

# Create the backup folder
mkdir "$DIR_PATH/$BACKUP_FOLDER"

# Copy all files from the specified directory to the backup folder
cp -r "$DIR_PATH"/* "$DIR_PATH/$BACKUP_FOLDER" 2>/dev/null
echo "✅ Backup created: $DIR_PATH/$BACKUP_FOLDER"

# Change to the directory containing the backups
cd "$DIR_PATH" || exit

# Get a list of backup folders matching the pattern "backup_*"
BACKUPS=(backup_*)
NUM_BACKUPS=${#BACKUPS[@]} # Count the number of backups

# If more than 3 backups exist, remove the oldest ones
if [ "$NUM_BACKUPS" -gt 3 ]; then
    DELETE_COUNT=$((NUM_BACKUPS - 3))
    for ((i = 0; i < DELETE_COUNT; i++)); do
        rm -rf "${BACKUPS[$i]}"
        echo "🗑 Removed old backup: ${BACKUPS[$i]}"
    done
fi
```

---

## 🧩 **How the Script Works**

### Step-by-Step Breakdown:

1. **Input Validation**
    
    * The script checks if the directory path is provided as an argument.
        
    * It verifies that the given path exists and is a directory.
        
2. **Create a Timestamped Backup**
    
    * A unique backup folder is created using the current timestamp, e.g., `backup_2025-02-12_12-30-45`.
        
    * Files from the directory are copied into this backup folder.
        
3. **Backup Rotation**
    
    * The script lists all existing backup folders matching the pattern `backup_*`.
        
    * If there are more than 3 backups, the oldest backups are deleted to retain only the latest 3.
        

---

## 💻 **Example Execution**

### **Command:**

```plaintext
$ ./backup_with_rotation.sh /home/user/documents
```

### **First Execution (2025-02-12):**

Output:

```plaintext
✅ Backup created: /home/user/documents/backup_2025-02-12_10-15-30
✅ Backup created: /home/user/documents/backup_2025-02-12_11-45-00
✅ Backup created: /home/user/documents/backup_2025-02-12_12-30-45
```

**Directory contents:**

```plaintext
backup_2025-02-12_10-15-30  
backup_2025-02-12_11-45-00  
backup_2025-02-12_12-30-45  
file1.txt  
file2.txt  
...  
```

---

### **Second Execution (2025-02-13):**

Output:

```plaintext
✅ Backup created: /home/user/documents/backup_2025-02-13_08-00-00
🗑 Removed old backup: backup_2025-02-12_10-15-30
```

**Directory contents (after rotation):**

```plaintext
backup_2025-02-12_11-45-00  
backup_2025-02-12_12-30-45  
backup_2025-02-13_08-00-00  
file1.txt  
file2.txt  
...  
```

🎯 **Notice:** The oldest backup (`backup_2025-02-12_10-15-30`) is deleted to retain only the last 3 backups.

---

## 🔍 **Key Shell Commands Used**

Here are the main commands powering the script:

1. `date`  
    Generates a unique timestamp for each backup.
    
    ```plaintext
    date +"%Y-%m-%d_%H-%M-%S"
    ```
    
2. `mkdir`  
    Creates a new directory for the backup folder.
    
    ```plaintext
    mkdir "$DIR_PATH/$BACKUP_FOLDER"
    ```
    
3. `cp`  
    Copies all files from the source directory to the backup folder.
    
    ```plaintext
    cp -r "$DIR_PATH"/* "$DIR_PATH/$BACKUP_FOLDER"
    ```
    
4. `rm`  
    Deletes the oldest backups to maintain only the last 3 backups.
    
    ```plaintext
    rm -rf "${BACKUPS[$i]}"
    ```
    

---

## ⏰ **Scheduling Backups with Cron**

Automate the script to run daily at 2:00 AM using the following `cron` command:

```plaintext
0 2 * * * /path/to/backup_with_rotation.sh /home/user/documents
```