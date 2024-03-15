[home](README.md) - [gdb](gdb.md) - [git](git.md) - [strace](strace.md) - [valgrind](valgrind.md)
***
# Summary
- [Commit](#commit)
- [Branch](#branch)

# Tutos
[nicelydev.com](https://www.nicelydev.com/git/git-show)
[Learn Git Branching](https://learngitbranching.js.org/?locale=fr_FR)
# Status
Watch the state of stagging areas
```
git status
```
# Commit
Add file in stagging area
```md
git add <files>
```
New commit
```h
git commit -m "msg"
```
New commit with all change
```h
git commit -am "msg"
```
Change last commit
```
git --amend
```

Watch list of commits
```
git log
```
Go to a commit
```

```
### Display difference
Display diff between last commit and current state of work
```
git diff
```
Display diff between a commit and the previous
```md
git show <commit>
```
Display diff between two commit
```md
git diff <commit1> <commit2>
```
# Branch
#### List all branch
```h
git branch
```
### Load a branch
```md
git switch <name_branch>
```
### Create a branch
- without move onto 
```md
git branch <name-of-branch>
```
- with move onto
```md
git branch <name-of-branch>
git checkout <name-of-branch>
```
ou
```md
git checkout -b <name_new_branch>
```
