---
title: "🔧Error Handling in Shell Scripting ."
datePublished: Fri Feb 14 2025 13:34:15 GMT+0000 (Coordinated Universal Time)
cuid: cm74t8gto000109ibdc118din
slug: error-handling-in-shell-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739539854109/134e7eba-4e9f-4e15-a903-939d1a00f690.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1739539994111/7b53daa6-387f-44e9-9919-9f0f80659372.jpeg
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

Handling errors is like having a safety net for your shell scripts! 🎯 Today, you’ll learn how to catch mistakes, clean up when things go wrong, and display meaningful messages. Let’s make scripting simple and reliable! 🚀

---

### **What You’ll Learn 📚**

* **Exit Status (**`$?`): Know if a command succeeded or failed.
    
    * ✅ `0`: Success
        
    * ❌ Non-zero: Failure
        
* **Error Handling with** `if`: Check for errors at every step.
    
* **Cleanup with** `trap`: Automatically clean up temporary files and resources.
    
* **Redirect Errors**: Save error messages to files for debugging.
    
* **Custom Messages**: Provide user-friendly error explanations.
    

---

### **Code Examples and Explanation 🛠️**

#### **Task 1 : Checking Exit Status 🔍**

```plaintext
#!/bin/bash
mkdir /tmp/mydir
if [ $? -ne 0 ]; then
  echo "❌ Error: Failed to create directory /tmp/mydir."
else
  echo "✅ Success: Directory /tmp/mydir created."
fi
```

##### **Detailed Explanation**:

1. `mkdir /tmp/mydir`: Attempts to create a directory.
    
2. `$?`: Captures the exit status of the last command:
    
    * `0`: Success.
        
    * Non-zero: Failure.
        
3. `if [ $? -ne 0 ]`: Checks if the exit status is **not equal** to `0` (failure).
    
4. `echo`: Prints a success or error message.
    

---

#### **Task 2 : Using** `if` for Multiple Steps 🚦

```plaintext
#!/bin/bash
mkdir /tmp/mydir
if [ $? -ne 0 ]; then
  echo "❌ Error: Could not create directory /tmp/mydir."
  exit 1
fi

touch /tmp/mydir/myfile.txt
if [ $? -ne 0 ]; then
  echo "❌ Error: Failed to create file myfile.txt in /tmp/mydir."
else
  echo "✅ Success: File myfile.txt created."
fi
```

##### **Detailed Explanation**:

1. `mkdir /tmp/mydir`: Creates a directory.
    
2. `if [ $? -ne 0 ]`: Checks if creating the directory failed.
    
3. `exit 1`: Exits the script with a non-zero status if an error occurs.
    
4. `touch /tmp/mydir/myfile.txt`: Creates a file in the new directory.
    
5. `if [ $? -ne 0 ]`: Checks if file creation failed.
    
6. Error or success messages are printed based on the status.
    

---

#### **Task 3 : Using** `trap` for Cleanup 🧹

```plaintext
#!/bin/bash
tempfile=$(mktemp)
trap "rm -f $tempfile; echo '🧹 Temporary file deleted.'" EXIT

echo "Temporary file created: $tempfile"
echo "Some data" > $tempfile

# Simulate an unexpected error
exit 1
```

##### **Detailed Explanation**:

1. `tempfile=$(mktemp)`: Creates a unique temporary file and stores its name in the variable `tempfile`.
    
2. `trap "rm -f $tempfile; echo '🧹 Temporary file deleted.'" EXIT`:
    
    * Sets up a "trap" to delete the temporary file when the script exits (even if it exits unexpectedly).
        
3. `echo "Some data" > $tempfile`: Writes some data to the temporary file.
    
4. `exit 1`: Simulates an unexpected error and triggers the `trap` to delete the file.
    

---

#### **Task 4 : Redirecting Errors ➡️**

```plaintext
#!/bin/bash
cat non_existent_file.txt 2> error.log
echo "Error messages (if any) have been saved to error.log."
```

##### **Detailed Explanation**:

1. `cat non_existent_file.txt`: Tries to display the contents of a file that doesn’t exist.
    
2. `2> error.log`: Redirects the error message (`2` is for standard error) to a file named `error.log`.
    
3. `echo`: Notifies the user that errors are logged in `error.log`.
    

---

#### **Task 5 : Creating Custom Error Messages ✍️**

```plaintext
#!/bin/bash
mkdir /tmp/mydir
if [ $? -ne 0 ]; then
  echo "❌ Error: Could not create /tmp/mydir. 
   Please check your permissions or if the directory already exists."
else
  echo "✅ Directory created successfully!"
fi
```

##### **Detailed Explanation:**

1. **Command**:  
    `mkdir /tmp/mydir`
    
    * This attempts to create a directory named `mydir` in the `/tmp` folder.
        
2. **Exit Status Check**:  
    `if [ $? -ne 0 ]`
    
    * `$?` holds the exit status of the previous command (`mkdir` in this case).
        
    * If the status is **not equal to 0 (**`-ne 0`), the command failed.
        
3. **Error Message**:  
    `echo "❌ Error: Could not create /tmp/mydir. Please check..."`
    
    * If the directory couldn’t be created, it prints an error message suggesting possible reasons (e.g., no permissions or the directory already exists).
        
4. **Success Message**:  
    `echo "✅ Success: Directory /tmp/mydir created."`
    
    * If the directory is successfully created, the script prints a success message.
        

---

Without proper error handling, scripts can fail silently, leaving behind messy files and incomplete tasks. With these techniques, you can create scripts that are **reliable, maintainable, and user-friendly** 💡.

---
