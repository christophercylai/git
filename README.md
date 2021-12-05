# Git Commands - Some Common Operations
> On Windows, using Git Bash is highly recommended

## Git Help
* The man page of Git
* Example: if you want to know what what does `git stash` do
```
git help stash
```

## Understanding Git Branches
> Here we assume that the remote repository remains static
* Cloning a remote repository to the local machine
```
$ git clone https://github.com/christophercylai/git.git
```
* The latest commit to the main branch is the HEAD of the main branch
* The main branch is also called the HEAD-branch (i.e. `origin/HEAD`), which is a different concept than HEAD of a branch
* `origin` represents the default remote repository (there could be multiple remote repositories)
```
$ git branch
* main

$ git log -n 1
commit ba7573edbd1532dd8925eefc490a720fd7ea5329 (HEAD -> main, origin/main, origin/HEAD)
...
```
* If we branch off from the main branch to create `new_branch`, HEAD represents the latest commit to `new_branch`
* Please note that `new_branch` only exists locally
```
$ git checkout -b new_branch
Switched to a new branch 'new_branch'

$ git log -n 1
commit ba7573edbd1532dd8925eefc490a720fd7ea5329 (HEAD -> new_branch, origin/main, origin/HEAD, main)
...
```
* Create `new_file.txt` and add this file to `new_branch`
```
$ git branch
  main
* new_branch

$ touch new_file.txt
$ git add new_file.txt
$ git status
On branch new_branch
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   new_file.txt

$ git commit -m 'added new_file.txt'
[new_branch 70ebee2] added new_file.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 new_file.txt
```
* After the commit, HEAD becomes the latest commit of new_branch
```
$ git log -n 2
commit 70ebee2035b896600b686113a0494b12847ac05f (HEAD -> new_branch)
Author: christopher lai <christophercylai@outlook.com>
Date:   Sat Dec 4 20:05:30 2021 -0500

    added new_file.txt

commit ba7573edbd1532dd8925eefc490a720fd7ea5329 (origin/main, origin/HEAD, main)
...
```
* Make `new_branch` known to the default remote repository
* At this point, our local repository is the same as the remote
```
$ git push -u origin new_branch
```

## Bringing Changes from the Remote Repository to Local
* Continue with the example above, let's suppose that someone has merged a few commits to the main branch in the remote repository
* We would like to synchronize our local main branch with the remote
```
$ git checkout main
$ git pull origin  # origin can be omitted if there is only one remote repository
```
* We also want to bring in the changes from `main` to `new_branch`
```
$ git checkout new_branch
$ git merge main
```

## Git Pull and Merge - Conflict Resolution
* If you encounter a pull or merge conflict, you have a couple options
  1. resolve the conflicts manually - if there are a small number of conflicts, this is a good option because it is safe
  ```
  # after the conflict has been resolved, use this command to finanlize the resolution
  $ git merge --continue
  ```
  2. resolve the conflicts using pull/merge `strategy` - see the `MERGE STRATEGIES` of `git help merge` for details
  ```
  # if there is a merge conflict, abort the merge first
  $ git merge --abort
  
  # attempt the merge again using merge strategy
  # for example, we prefer the changes from the main branch
  $ git merge -X theirs main
  
  # if we prefer the changes from new_branch
  $ git merge -X ours main
  ```
