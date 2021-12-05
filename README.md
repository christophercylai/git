# Git Commands - Some Common Operations
> On Windows, using Git Bash is highly recommended

## Understanding Git Branches
* Cloning a remote repository to the local machine
```
git clone https://github.com/christophercylai/git.git
```
* The latest commit to the main branch is the HEAD of the main branch
```
git branch
* main

git log -n 1
commit 5b6cc9bf3654b0926c9d1ad26bbc3648ce7cbb09 (HEAD -> main, origin/main, origin/HEAD)
```
* If we branch off from the main branch to create `new_branch`, HEAD represents the latest commit to `new_branch`
* Please note that `new_branch` only exists locally
```
git checkout -b new_branch
Switched to a new branch 'new_branch'

git log -n 1
commit 5b6cc9bf3654b0926c9d1ad26bbc3648ce7cbb09 (HEAD -> new_branch, origin/main, origin/HEAD, main)
```
* Suppose that we create `new_file.txt` and add this file to 
* If we make a new commit to `new branch`
```

```
