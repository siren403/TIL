---
title: git cli
categories:
  - Gist
tags:
  - git
---

{% gist 77238d4b2929fb90107c363bb3fd6048 %}

checkout
---

```shell
git checkout -f <branch>
```

add
---

```shell
# hunk
git add -p
```

remote
---

```shell
git remote <remote> --all
```

rm
---

```shell
# remove all tree
git filter-branch -f --prune-empty --index-filter "git rm -r --cached --ignore-unmatch ./file1" HEAD
```

lfs
---

```shell
git lfs migrate import --include-ref=<branch> --include="*.zip"

git lfs migrate import --everything --include="*.zip"

git lfs migrate import --everything --above=100kb
```

merge conflict
---

```shell
# select
git checkout --ours  <file>
git checkout --theirs  <file>
```

unstage
---

```shell
git reset HEAD -- .
```

submodule
---

```shell
git submodule update --recursive
git pull --recurse-submodules
```