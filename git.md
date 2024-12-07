[home](README.md) - [gdb](gdb.md) - [git](git.md) - [strace](strace.md) - [valgrind](valgrind.md)

***

# Summary

- [Tutos](#tutos)
- [Commit](#commit)
- [Branch](#branch)

# Tutos

[nicelydev.com](https://www.nicelydev.com/git/git-show)  
[Learn Git Branching](https://learngitbranching.js.org/?locale=fr_FR)
[buzut.net](https://buzut.net/cours/versioning-avec-git/depots-distants)

# Status

Watch the state of stagging areas

```bash
git status
```

# Commit

Add file in stagging area

```bash
git add <files>
```

New commit

```bash
git commit -m "msg"
```

New commit with all change

```bash
git commit -am "msg"
```

Change last commit

```bash
git --amend
```

Watch list of commits

```bash
git log
```

Go to a commit

```bash

```

### Display difference

Display diff between last commit and current state of work

```bash
git diff
```

Display diff between a commit and the previous

```bash
git show <commit>
```

Display diff between two commit

```bash
git diff <commit1> <commit2>
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

### Create a branch locale

- without move onto 
  
  ```bash
  git branch <name-of-branch>
  ```

- with move onto
  
  ```bash
  git branch <name-of-branch>
  git checkout <name-of-branch>
  ```
  or
  ```bash
  git checkout -b <name_new_branch>
  ```
### add a local branch on remote
```
git push <remote_name> <branch-name>
```
by default `<remote-name>` = origin

### get a remote branch

- simple methode
  ```
  git pull <remote-name> <branch-name>
  ```
- with the same name as the remote
  ```bash
  git checkout --track <remote_name>/<branch-name>
  ```
  by default `<remote-name>` = origin
- with an other name in local
  ```bash
  git checkout --track -b <local-branch> origin/<remote-branch>
  ```

### [merge a branch](https://www.atlassian.com/fr/git/tutorials/using-branches/git-merge)
- place to branche which store the merge
```bash
 git checkout <main_branch>
```
- merge branch
``` bash
git merge <branch to merge>
```

- merge with squash
```bash
git checkout <branch_which_receive_the_merge>
git merge --squash <branch to merge>
git commit -m "merged <branch to merge>"
```