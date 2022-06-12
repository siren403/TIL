---
title: linux command CheatSheet
categories:
  - CheatSheet
tags:
  - linux
---

monitor log file
---

```shell
tail -f <file>
```

regex
---

```shell
#!/bin/bash

# file regex
grep <pattern> <file>
echo <text> | grep ...

# split
cut -d <split> -f<position> <file>
echo <text> | cut ...
```