[home](README) - [gdb](gdb) - [git](git) - [strace](strace) - [valgrind](valgrind)
***
# Summary
- [Commit](#commit)
- [Branch](#branch)

# Tutos
[Learn Git Branching](https://learngitbranching.js.org/?locale=fr_FR)
***
# Commit
Add file in stagging area
```
git add <files>
```
New commit
```
git commit -m "msg"
```
New commit with all change in following files
```
git commit -am "msg"
```
Change last commit
```
git --amend
```
Watch the state of stagging areas
```
git status
```
Watch list of commits
```
git log
```
Go to a commit
```

```
# Branch
#### List all branch
```bash
git branch
```
### Load a branch
```bash
git switch <name_branch>
```
### Create a branch
- without move onto 
```
git branch <name-of-branch>
```
- with move onto
```
git branch <name-of-branch>
git checkout <name-of-branch>
```
ou
```bash
git checkout -b <name_new_branch>
```