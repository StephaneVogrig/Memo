[home](README.md) - [gdb](gdb.md) - [git](git.md) - [strace](strace.md) - [valgrind](valgrind.md)

***

# Summary

- [Tutos](#tutos)
- [Commit](#commit)
- [Branch](#branch)

# Tutos

[nicelydev.com](https://www.nicelydev.com/git/git-show)
[Learn Git Branching](https://learngitbranching.js.org/?locale=fr_FR)

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

### Create a branch

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
