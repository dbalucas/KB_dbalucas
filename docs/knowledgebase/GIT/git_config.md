---
title: setup a good gitconfig
date: 2024-07-30
authors: [dbalucas]
description: >
  description of how to setup a good git config
categories:
  - git
tags:
  - git
---

```zsh
vi ~/.gitconfig

#!/.giconfig
[user]
        name = <username>
        email = <mailaddres>
[init]
        defaultBranch = main
[alias]
    cleanup = "!git branch --merged | grep  -v '\\*\\|master\\|develop\\main' | xargs -n 1 -r git branch -d"
```

To avoid having thousend of local branches not alligned with the remote repository, just do:
```zsh
git cleanup
```
