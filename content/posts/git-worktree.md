---
title: "Git Worktree"
date: 2021-02-10T23:28:04-08:00
draft: false
---


Use the same git repo and .git content but have multiple working directories.
This can be very useful if you are switcing contexts on the same monorepo.


From the [documentation](https://git-scm.com/docs/git-worktree#_examples) explaining the use-case:

> create a temporary linked working tree to make the emergency fix, remove it when done, and then resume your earlier refactoring session.

```
$ git worktree add -b emergency-fix ../temp master
$ pushd ../temp
# ... hack hack hack ...
$ git commit -a -m 'emergency fix for boss'
$ popd
$ git worktree remove ../temp
```
