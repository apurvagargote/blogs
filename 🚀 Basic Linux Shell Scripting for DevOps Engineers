---
title: "🚀 Basic Linux Shell Scripting for DevOps Engineers"
datePublished: Fri Feb 07 2025 14:18:16 GMT+0000 (Coordinated Universal Time)
cuid: cm6uuq43r000409l4c9x32l62
slug: basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738938314174/01f7ab15-cb66-4324-9725-143c56982883.jpeg
tags: 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

---

## 🖥️ What is a Shell Script?

Imagine you own a **pizza shop** 🍕, and every day you have to:

1️⃣ Open the shop 🏪  
2️⃣ Turn on the oven 🔥  
3️⃣ Prepare the dough 🍞  
4️⃣ Make pizza 🍕  
5️⃣ Serve customers 🛎️  
6️⃣ Clean the shop 🧹

Now, instead of doing this manually **every single day**, what if you could create a **robot assistant 🤖** that follows a list of instructions and does it for you?

That’s exactly what a **shell script** does for computers!

✅ A shell script is like a **to-do list** 📋 for your computer.  
✅ It tells the computer **what to do step by step**.  
✅ It automates boring, repetitive tasks so you can relax. 😎

---

## 🔹 What is `#!/bin/bash`?

The first line of a shell script starts with **shebang (**`#!`), which tells the computer **which language** to use for the script.

```plaintext
#!/bin/bash
echo "Hello, DevOps!"
```

✔️ `/bin/bash` → Uses the Bash shell (most common).  
✔️ `/bin/sh` → Uses a more general shell (might behave differently on some systems).

Think of it like telling your robot assistant **which language to speak** before giving instructions! 🤖

---

## ✍️ Shell Script to Print a Message

Let's create a simple script that prints a motivational message.

```plaintext
#!/bin/bash
echo "I will complete #90DaysOfDevOps challenge."
```

📌 **Save the file as** [`challenge.sh`](http://challenge.sh) and run:

```plaintext
chmod +x challenge.sh  # Give execute permission
./challenge.sh         # Run the script
```

**Output:**

```plaintext
I will complete #90DaysOfDevOps challenge.
```

---

## 🔢 Script to Take User Input & Arguments

```plaintext
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello, $name!"

echo "Script Name: $0"
echo "First Argument: $1"
echo "Second Argument: $2"
```

📌 **How to run the script with arguments:**

```plaintext
./script.sh DevOps Enthusiast
```

**Output:**

```plaintext
Enter your name:
Ana
Hello, Ana!
Script Name: script.sh
First Argument: DevOps
Second Argument: Enthusiast
```

**Explanation:**

* `$name` → Stores user input.
    
* `$0` → The script name.
    
* `$1`, `$2`, etc. → Arguments passed when running the script.
    

---

## 🔄 If-Else Statement in Shell Scripting

```plaintext
#!/bin/bash
num1=10
num2=20

if [ $num1 -gt $num2 ]
then
    echo "$num1 is greater than $num2"
else
    echo "$num1 is less than or equal to $num2"
fi
```

📌 **Comparison Operators:**

* `-eq` → Equal to
    
* `-ne` → Not equal to
    
* `-gt` → Greater than
    
* `-lt` → Less than
    
* `-ge` → Greater than or equal to
    
* `-le` → Less than or equal to
    

---

## 🔁 **Loops in Shell Scripting**

Loops help us **repeat tasks** automatically instead of writing the same commands multiple times.

### 1️⃣ **For Loop** 🌀

A **for loop** is used when we know **how many times** we want to repeat something.

```plaintext
#!/bin/bash
for i in 1 2 3 4 5
do
  echo "Iteration number: $i"
done
```

📌 **Run this script**, and it will print:

```plaintext
Iteration number: 1
Iteration number: 2
Iteration number: 3
Iteration number: 4
Iteration number: 5
```

🔹 **Real-life example:**  
Imagine you want to print 100 invoice copies. Instead of clicking print **100 times**, a loop does it for you!

### 2️⃣ **While Loop** 🔄

A **while loop** runs **until a condition is met**.

```plaintext
#!/bin/bash
count=1

while [ $count -le 5 ]
do
  echo "Count: $count"
  count=$((count+1))  # Increase count by 1
done
```

📌 **Output:**

```plaintext
Count: 1
Count: 2
Count: 3
Count: 4
Count: 5
```

---

## 🌍 Real-Life Use Cases for Shell Scripting

✔️ **📦 Automate software deployment** → No more clicking buttons manually!  
✔️ **📊 Log Analysis** → Scan logs for errors and send alerts automatically.  
✔️ **☁️ Cloud Automation** → Start/stop cloud servers when needed.  
✔️ **💾 Database Backups** → Save important data without forgetting.

Just like a **robot assistant** makes your life easier in the pizza shop, a **shell script** makes life easier for DevOps engineers!
