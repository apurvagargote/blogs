---
title: "🐧 The Ultimate Linux & Git-GitHub Cheat Sheet for DevOps 🛠️"
datePublished: Mon Feb 17 2025 06:21:06 GMT+0000 (Coordinated Universal Time)
cuid: cm78o2zuk000509ju759m4iy6
slug: the-ultimate-linux-and-git-github-cheat-sheet-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739773208528/0f2410c7-1e61-4b8f-a7ad-9933803fa127.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1739773132923/ff458766-d2f1-4a29-be48-b60166060a5d.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

### **🐧 Linux Commands for Everyday Use**

| **Command** | **Description** | **Example** |
| --- | --- | --- |
| `whoami` | Displays the current logged-in user. | `whoami` |
| `uname -r` | Displays the Linux kernel version. | `uname -r` |
| `df -h` | Shows disk usage in a human-readable format. | `df -h` |
| `du -sh [directory]` | Shows the size of a directory or file. | `du -sh /home/user` |
| `ls -la` | Lists all files and directories with detailed information. | `ls -la` |
| `pwd` | Prints the current working directory. | `pwd` |
| `mkdir [directory]` | Creates a new directory. | `mkdir project_folder` |
| `rm -rf [directory/file]` | Deletes files or directories (use with caution). | `rm -rf old_files` |
| `chmod [permissions] [file]` | Changes file permissions. | `chmod 755` [`script.sh`](http://script.sh) |
| `chown [user]:[group] [file]` | Changes ownership of a file or directory. | `chown user:group file.txt` |
| `ps -aux` | Displays all running processes. | `ps -aux` |
| `kill [process_id]` | Terminates a process by its PID. | `kill 1234` |
| `history` | Shows command history. | `history` |
| `alias [name]='[command]'` | Creates a shortcut for a command. | `alias ll='ls -la'` |
| `curl [url]` | Fetches data from a URL. | `curl` [`https://example.com`](https://example.com) |
| `wget [url]` | Downloads a file from a URL. | `wget` [`https://example.com/file.zip`](https://example.com/file.zip) |
| `scp [file] [user@host:/path]` | Securely copies files between local and remote systems. | `scp file.txt user@192.168.1.1:/tmp` |
| `ssh [user@host]` | Connects to a remote server via SSH. | `ssh user@192.168.1.1` |

---

### **🔍 Text Processing Commands.**

| **Command** | **Description** | **Example** |
| --- | --- | --- |
| `find [directory] -name "[name]"` | Searches for files by name. | `find /home -name "*.txt"` |
| `awk '/pattern/ {action}' [file]` | Processes text based on patterns in files. | `awk '/error/ {print $2}' log.txt` |
| `sed -i 's/[old]/[new]/g' [file]` | Finds and replaces text in a file. | `sed -i 's/foo/bar/g' file.txt` |
| `sort [file]` | Sorts lines in a file. | `sort data.txt` |
| `uniq [file]` | Removes duplicate lines from a file. | `uniq data.txt` |
| `wc -l [file]` | Counts the number of lines in a file. | `wc -l file.txt` |
| `grep [pattern] [file]` | Searches for a pattern in a file. | `grep "error" log.txt` |
| `crontab -e` | Edits the crontab to schedule recurring tasks. | `crontab -e` |

---

### **🌐 Networking Commands**

| **Command** | **Description** | **Example** |
| --- | --- | --- |
| `ping [host]` | Tests connectivity to a server. | `ping` [`google.com`](http://google.com) |
| `netstat -tuln` | Displays open ports and network connections. | `netstat -tuln` |
| `ip a` | Displays IP address and network details. | `ip a` |
| `scp [file] [user@host:/path]` | Copies files between local and remote systems. | `scp` [`backup.zip`](http://backup.zip) `user@192.168.1.1:/tmp` |
| `ssh [user@host]` | Connects to a remote server via SSH. | `ssh user@192.168.1.1` |
| `curl -I [url]` | Fetches HTTP headers for a URL. | `curl -I` [`https://example.com`](https://example.com) |

---

### **🛠️ Git Essentials**

| **Command** | **Description** | **Example** |
| --- | --- | --- |
| `git init` | Initializes a Git repository in the current directory. | `git init` |
| `git clone [url]` | Creates a local copy of a remote repository. | `git clone` [`https://github.com/user/repo.git`](https://github.com/user/repo.git) |
| `git status` | Shows the status of changes in the working directory. | `git status` |
| `git add [file]` | Stages a file for commit. | `git add` [`README.md`](http://README.md) |
| `git commit -m "[message]"` | Saves staged changes with a commit message. | `git commit -m "Initial commit"` |
| `git push origin [branch]` | Pushes changes to the remote repository. | `git push origin main` |
| `git pull origin [branch]` | Fetches and merges changes from a remote repository. | `git pull origin main` |
| `git branch` | Lists all branches in the repository. | `git branch` |
| `git checkout -b [branch]` | Creates and switches to a new branch. | `git checkout -b feature-branch` |
| `git merge [branch]` | Merges a branch into the current branch. | `git merge feature-branch` |
| `git log` | Displays the commit history. | `git log` |

---

### **🌟 GitHub Essentials**

| **Action** | **Description** | **Steps** |
| --- | --- | --- |
| **Create a Repository** | Sets up a new repository on GitHub. | Go to GitHub → Click on "New" → Fill details. |
| **Clone a Repository** | Copies an existing repository to your local system. | `git clone [url]` |
| **Push Changes** | Updates the remote repository with local changes. | `git push origin main` |
| **Pull Requests** | Proposes changes to a branch. | Navigate to your branch → Click "Pull Request". |
