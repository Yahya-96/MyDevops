# Git Workflow

## Objective: 
In order to familiarise myself with the Git Workflow and understand the benefits of Git, i was tasked to the following: 

- Create a feature branch
- Make improvements to my BASH scripts
- Make meaningful commits
- Create a Merge Request.


## 1: Clone repository



 ## 2: Create a feature branch.
As i want to improve the efficiency of my code, it is important i follow the best Git practices for naming a branch. I named the feature branch `feature/script-enhancements`. On my terminal, i did the following:
```
git branch feature/script-enhancements

git status
```

`git status` allows me to double check what i am doing, where i am at and if the previous code has gone through. It keeps me up-to-date with what i am doing.

---

## 3: Make changes to BASH scripts.
I will go on my BASH `.md` files and making meaningful changes and improvements. Once i have made the changes, i will save them and emter the following:
```
git add (filename.md)
```

'git add': This stages changes (new, modified, or deleted files) to be included in the next commit. It moves changes to the staging area, allowing you to selectively choose what gets committed.

---

## 4: Make a commit using `git commit -m`
Once `git add` is used, i will make a commit. This allows me to saves the staged changes to the repository’s history. It will also allow me to record the changes along with a descriptive message (`m`).
```
git commit - "Concise description of change"
```

It is important to keep the commit messages concise yet descriptive. This is to ensure it is easy for others (and future you) to understand what was done without unnecessary details. Concise messages also help pinpoint relevant commits faster.


## 5: Do not forget to use `git push`.
Once i have made all of my commits, i am now ready to "push" this to my remote repo. This will be the final step.
```
git push
```

## 6: Initiate a Pull Request.  
