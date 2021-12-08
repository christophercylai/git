## git Log - How to Grab the Information You Need
> git log has tons of options, and here are some common usages
* To get the log of the newest X commits
```
# get the newest 1 commit
git log -1

# get the newest 5 commits
git log -5
```
* Show your commits since branching off from origin/HEAD
```
git log origin/HEAD..HEAD
```
* Show the commits between two commits
```
git log origin/HEAD..HEAD
```
* Filter the log with a string search
```
# --grep can be use multiple times, commits that match any one of the patterns will show
git log --grep=<string pattern>

# commits that must match all the search pattern
git log --grep=<string pattern1> --grep=<string pattern2> --all-match
```
* Filter the log to show only commits from a particular author
```
# --author can be use multiple times
git log --author <author name>
```
* Commit Formatting - shows only the information you are interested in
```
# only show <hash> <title line> of the commits
git log --pretty=oneline

# show only <hash>
git log --pretty=format:%H

# to create oneline with format
git log --pretty=format:"%H %s"
```
