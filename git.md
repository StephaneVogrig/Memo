[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)- [escape code](ainsi_escape_code.md)

***

# Summary

- [Tutos](#tutos)
- [Commit](#commit)
- [Branch](#branch)
- [Log](#log)
- [reflog](#reflog)
- [pull request](#reflog)

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

### Create a local branch

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

### Create a remote  branch

### create a remote branch with a local branch
```
git push -u origin <branch-name>
```
'-u' is a contraction for '--set-upstream'
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
# log

### To display all log

```
git log --all
```
### To display logs one one line

```
git log --oneline
```
### To display log whit graphical branch

```
git log --graph
```

# reflog
[stackoverflow: usage example](https://stackoverflow.com/questions/10099258/how-can-i-recover-a-lost-commit-in-git)


Every time the HEAD is modified there will be a new entry in the reflog
```
git reflog
git checkout HEAD@{...}
```

# pull request
[pull request](https://www.frayssinet.org/2021/06/25/tuto-debutant-faire-une-pull-request-sur-github-avec-git/)