# Git Workflow
 
In order to familiarise myself with the Git Workflow and understand the benefits of Git, i was tasked with the following: 

- Create a feature branch
- Make improvements to my BASH scripts
- Make meaningful commits
- Create a Merge Request.


## 1: Download Git on local machine
 1. Navigated to the [Github](https://github.com/) website and signed into my account.
 2. As i already created a repository a week prior, there was no need for me to create a new one.
 3. Downloaded Git onto my local machine. As i am on Mac OS, i  installed [Homebrew](git-scm.com) via the **git-scm.com** website.
 4. Next, I will copy the script on the [Homebrew](https://brew.sh/) website, paste it onto my local terminal and press enter.
 5. Once [Homebrew](https://brew.sh/) has been downloaded, i will go back to [Git](https://git-scm.com/downloads/mac) and copy `$ brew install git`.
 6. Finally, i will go back to my terminal and paste `$ brew install git`

I have successfully downloaded Git on Mac!


## 2: Clone repository
As i already created a repository a week prior, there was no need for me to create a new one. I will go to the **terminal** and link my remote repository to the local repository by running the following commands:
```
git config --global user.name "Yahya-96"
git config --global user.email "ym96@hotmail.co.uk"
```

`git config --global user.name "Yahya-96"`: This sets my global Git username to "Yahya-96"

`git config --global user.email "ym96@hotmail.co.uk"`: This sets my global Git email to my personal email(**ym96@hotmail.co.uk**)

Next, i will go to my remote repository and click on **Code**. I will copy the url link under **HTTPS**, go back to the **terminal** and type the following command:
```
git clone https://github.com/Yahya-96/MyDevops.git
```

This successfully cloned the **MyDevops** repository.

---

 ## 2: Create a feature branch.
As i want to improve the efficiency of my code, it is important i follow the best Git practices for naming a branch. I named the feature branch `feature/script-enhancements`. On my terminal, i did the following:
```
git branch feature/script-enhancements

git status
```

`git status` allows me to double check what i am doing, where i am at and if the previous code has gone through. It keeps me up-to-date with what i am doing.

---

## 3: Make changes to BASH scripts.
I will go on my BASH `.md` files and making meaningful changes and improvements. Once i have made the changes, i will save them and enter the following:
```
git add (filename.md)
```

`git add`: This stages changes (new, modified, or deleted files) to be included in the next commit. It moves changes to the staging area, allowing you to selectively choose what gets committed.

---

## 4: Make a commit using `git commit -m`
Once `git add` is used, i will make a commit. This allows me to saves the staged changes to the repository’s history. It will also allow me to record the changes along with a descriptive message (`m`).
```
git commit -m "Concise description of change"
```

It is important to keep the commit messages concise yet descriptive. This is to ensure it is easy for others (and future you) to understand what was done without unnecessary details. Concise messages also help pinpoint relevant commits faster.


## 5: Do not forget to use `git push`.
Once i have made all of my commits, i am now ready to "push" this to my remote repo. This will be the final step.
```
git push
```

## 6: Initiate a Pull Request.  
This is done before a merge request. A pull request facilitates collaboration by allowing someone else to review your code and double-check if everything is in order.
