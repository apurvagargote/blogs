---
title: "🚀 Log Analyzer and Report Generator Challenge"
datePublished: Thu Feb 13 2025 12:19:58 GMT+0000 (Coordinated Universal Time)
cuid: cm73b53hm000709lb3d3n3gdl
slug: log-analyzer-and-report-generator-challenge
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739449035119/da65f0e2-fe0a-4781-8fe2-4cd5d1e2b3c3.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1739449146273/5647e395-b1ec-45a5-b9ac-93bd0bb7eb07.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

## 🖥️ **The Scenario**

You're a **system administrator** managing a network of servers. Each day, these servers generate **log files** full of system events and error messages.

Your task? Build a **Bash script** to analyze these logs and produce a daily **summary report**. This script will save time, automate log analysis, and ensure you never miss critical events!

---

## 🎯 **Script Objectives**

Your Bash script will do the following:

1. ✅ **Take a log file as input** (via command-line arguments).
    
2. 🔎 **Count error messages** with keywords like `ERROR` or `Failed`.
    
3. 🚨 **Highlight critical events** containing the keyword `CRITICAL` (with line numbers).
    
4. 📊 **Identify the top 5 error messages** and their counts.
    
5. 📝 **Generate a summary report** with all findings in a text file.
    
6. 📦 **Optional**: Archive or move processed logs to a designated directory for cleanup.
    

---

## 🛠️ **Bash Commands Explained**

Here’s how the script works step by step, with commands to get you started!

### 1️⃣ **Reading the Log File**

* **Command**: `cat`
    
    * Usage: `cat /path/to/logfile.log`
        
    * **What it does**: Displays the entire content of the log file. Useful for verifying the file’s content before processing.
        
    * Example:
        
        ```plaintext
        cat logfile.log
        ```
        
* **Command for checking existence**: `if`
    
    * Usage:
        
        ```plaintext
        if [ -f logfile.log ]; then
            echo "File exists!"
        else
            echo "File not found!"
        fi
        ```
        
    * **What it does**: Checks if the file exists before processing. Prevents errors if the file is missing.
        

---

### 2️⃣ **Counting Errors**

* **Command**: `grep`
    
    * Usage: `grep -i "ERROR" logfile.log | wc -l`
        
    * **What it does**:
        
        * `grep -i "ERROR"`: Searches for all lines containing "ERROR" (case-insensitive with `-i`).
            
        * `wc -l`: Counts the number of lines returned by `grep`.
            
    * Example:
        
        ```plaintext
        error_count=$(grep -i "ERROR" logfile.log | wc -l)
        echo "Total errors: $error_count"
        ```
        

---

### 3️⃣ **Finding Critical Events**

* **Command**: `grep -n`
    
    * Usage: `grep -n "CRITICAL" logfile.log`
        
    * **What it does**:
        
        * `-n`: Displays the line number along with the matching lines.
            
    * Example:
        
        ```plaintext
        grep -n "CRITICAL" logfile.log
        ```
        
        Output:
        
        ```plaintext
        45:CRITICAL: Disk space low
        87:CRITICAL: Service timeout
        ```
        

---

### 4️⃣ **Top 5 Error Messages**

* **Command**: `awk` + `sort` + `uniq`
    
    * Usage:
        
        ```plaintext
        grep -i "ERROR" logfile.log | awk '{print $0}' | sort | uniq -c | sort -nr | head -5
        ```
        
    * **Explanation**:
        
        1. `grep -i "ERROR"`: Finds all error lines.
            
        2. `awk '{print $0}'`: Prints the entire line.
            
        3. `sort`: Sorts the lines alphabetically.
            
        4. `uniq -c`: Groups identical lines and counts their occurrences.
            
        5. `sort -nr`: Sorts the output numerically in descending order.
            
        6. `head -5`: Displays the top 5 most common error messages.
            
    * Example Output:
        
        ```plaintext
        20 ERROR: Service unavailable
        15 ERROR: Connection timeout
        10 ERROR: Disk space low
        ```
        

---

### 5️⃣ **Generating a Summary Report**

* **Command**: `echo` + Redirection (`>` or `>>`)
    
    * Usage:
        
        ```plaintext
        echo "Date of Analysis: $(date)" > summary_report.txt
        echo "Log File: logfile.log" >> summary_report.txt
        echo "Total Errors: $error_count" >> summary_report.txt
        echo "Critical Events:" >> summary_report.txt
        grep -n "CRITICAL" logfile.log >> summary_report.txt
        ```
        
    * **What it does**: Creates a report with all the key details in a text file.
        
        * `>`: Creates/overwrites the file.
            
        * `>>`: Appends to the file.
            

---

### 6️⃣ **Archiving Processed Logs (Optional)**

* **Command**: `mv` or `gzip`
    
    * Move the processed log file to an archive folder:
        
        ```plaintext
        mv logfile.log /path/to/archive/
        ```
        
    * Compress the log file:
        
        ```plaintext
        gzip logfile.log
        ```
        

---

## 📝 **Sample Summary Report**

Here’s what your final report might look like:

```plaintext
Date of Analysis: Tue Feb 13 2025
Log File: logfile.log
Total Lines Processed: 12345
Total Errors: 205
Top 5 Error Messages:
   20 ERROR: Service unavailable
   15 ERROR: Connection timeout
   10 ERROR: Disk space low
Critical Events:
   45:CRITICAL: Disk space low
   87:CRITICAL: Service timeout
```
