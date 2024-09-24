---
layout: single
title: "Github"
permalink: /learning/git/
classes: wide
sidebar:
  nav: Programming
---

Staging → `git add {files}`

Unstaging → `git restore --staged {files}`

Commit → `git commit ""commit message`

commit without staging → `git commit -a -m "message`

amend commit → `git commit -m "message" --amend`

Go back to specific commit `git reset {commitID}`

Cancel git reset `git reset 'HEAD@{1}'`

create new branch `git branch {branch name}`

check branch `git branch`

switch branch `git switch {branch name}`

delete branch `git branch -d {branch name}`

switch and create new branch `git switch -c {new branch name}`

### Remove a commit / force push old commit

```
git reset --hard {commitID}
git push --force
```
