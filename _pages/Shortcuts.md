---
layout: single
title: "VScode shortcuts"
permalink: /shortcuts/
classes: wide
sidebar:
  nav: Learning
---

## Remote pull and push

[Reference](https://www.freecodecamp.org/news/create-and-sync-git-and-github-repositories/#scenario-2-remote-first){: .btn .btn--info}{:target="\_blank"}

### git pull

To update local files from remote repo, type `git pull origin`. If you have local changes before pulling, you may need to `git stash` to stash your local change before pulling

### git push

After editing and saved. You need to commit by `git commit -am "message"` first. And `git push` after commit

\* If you have added new file, `git add *` is needed

## jekyll local server

`bundle exec jekyll serve`

## Multiple cursor in same column

To add multiple lines, press `Ctrl + Alt + Up/Down` and start editing.

To remove the multi-cursor, press `Esc`.

## Multiple cursor on same keywords

To add one additional cursor on same search, press `Ctrl + Shift + L` .
To increase more than one extra cursor, just press the command multiple times.

To remove the multi-cursor, press `Esc`.

## Shift codes lines

Highlight the lines you wish to move, hold `Alt` and press &uarr; or &darr; to move

## ignore error

Write `// @ts-ignore` right above the line you wish to ignore error

## See available properties / option

press `Ctrl + Space` to view options
