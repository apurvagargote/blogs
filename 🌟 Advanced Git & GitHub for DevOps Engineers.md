---
title: "🌟Advanced Git & GitHub for DevOps Engineers"
datePublished: Sun Feb 16 2025 17:15:59 GMT+0000 (Coordinated Universal Time)
cuid: cm77w1c1e000309jv7vz423r5
slug: advanced-git-and-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1739726079565/f00abeb9-3ef3-4dbe-a7d7-75df39d79938.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1739726125451/b0fb8a91-ef56-4567-88c0-b8f4cd8d047d.png
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

Git can feel like magic, but it’s really just a set of tools that help you collaborate, experiment, and recover from mistakes with ease. Let’s break it all down in a **fun and simple way**, and we’ll explain the **commands** step-by-step too!

---

### 🌿 **Git Branching: Your Playground for Experiments**

Think of **branches** as separate workspaces for your ideas. They let you work on new features, fix bugs, or test experiments without touching the main project. When you’re done, you can **merge** your branch into the main one.

Here’s why branches are awesome:

* 🛡️ They keep your main branch safe from unfinished work.
    
* 🤝 Multiple people can work on different branches simultaneously.
    
* 🔀 You can merge branches when features are ready.
    

---

#### 🛠 **Task 1: Feature Development with Branches**

##### 1\. **Create a New Branch and Add a Feature**

👉 Command:

```plaintext
git checkout -b dev
```

* `git checkout -b dev`: Creates a new branch called `dev` and switches to it.
    

Now, let’s add a file and commit our changes:

```plaintext
echo "This is the first feature of our application" > Devops/Git/version01.txt
git add Devops/Git/version01.txt
git commit -m "Added new feature"
```

* `echo`: Adds text to the file `version01.txt`.
    
* `git add`: Stages the file, meaning Git is now tracking this change.
    
* `git commit -m`: Saves the change with a message (`-m`) describing what you did.
    

##### 2\. **Push Your Branch to GitHub**

👉 Command:

```plaintext
git push origin dev
```

* `git push origin dev`: Uploads your `dev` branch to the remote GitHub repository.
    

##### 3\. **Add More Features with Separate Commits**

Let’s simulate more updates to the file:

```plaintext
echo "This is the bug fix in development branch" >> Devops/Git/version01.txt
git commit -am "Added bug fix in development branch"
```

* `>>`: Appends text to the file without overwriting it.
    
* `git commit -am`: Stages (`-a`) and commits the change in one step.
    

Repeat this for more lines:

```plaintext
echo "This is gadbad code" >> Devops/Git/version01.txt
git commit -am "Added gadbad code in development branch"

echo "This feature will gadbad everything from now" >> Devops/Git/version01.txt
git commit -am "Added problematic feature"
```

##### 4\. **Revert to a Clean Version**

Oops! We messed up. Let’s roll back the last two changes:  
👉 Command:

```plaintext
git revert HEAD~2
```

* `git revert HEAD~2`: Creates a new commit that undoes the last two commits (`HEAD` refers to the latest commit).
    

---

### 🔄 **Git Reset vs Git Revert**

1. **Git Revert**: Safely undoes changes by creating a new commit. Great for collaborative projects.  
    👉 Command:
    
    ```plaintext
    git revert HEAD  
    ```
    
2. **Git Reset**: Completely erases changes, even from history. Be careful!  
    👉 Command:
    
    ```plaintext
    git reset --hard HEAD~1  
    ```
    
    * `--hard`: Removes changes from both the history and the working directory.
        

---

#### 🛠 **Task 2: Playing with Branches**

##### 1\. **Check Branches**

List all branches in your repository.  
👉 Command:

```plaintext
git branch
```

* The branch with `*` is your current branch.
    

Create two new branches:  
👉 Command:

```plaintext
git branch feature1
git branch feature2
```

##### 2\. **Merge Branches**

Merge changes from `dev` into `master`.  
👉 Command:

```plaintext
git checkout master
git merge dev
```

* `git checkout master`: Switches to the `master` branch.
    
* `git merge dev`: Merges the `dev` branch into `master`.
    

##### 3\. **Rebase Your Branch**

Rebase `dev` onto `master` to clean up the commit history.  
👉 Command:

```plaintext
git rebase master
```

* `git rebase master`: Moves `dev`'s commits to the end of `master`'s history, creating a linear timeline.
    

---

### 🔀 **Rebase vs Merge**

* **Merge**: Combines branches while preserving the full history (shows all commits).  
    👉 Command:
    
    ```plaintext
    git merge dev  
    ```
    
* **Rebase**: Integrates changes while rewriting the commit history (creates a cleaner timeline).  
    👉 Command:
    
    ```plaintext
    git rebase master  
    ```
    

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739725666291/9882e760-75fd-4431-a882-0f4e4b5dd632.jpeg align="center")

---

### 🎯 **Why Is This Important for DevOps?**

1. **Branches** let you experiment without breaking the main project.
    
2. **Revert/Reset** helps you fix mistakes easily.
    
3. **Rebase/Merge** organizes your project history.
    

Git makes teamwork seamless and reduces risks during development. 🚀
