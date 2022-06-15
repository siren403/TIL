---
title: PowerShell CheatSheet
categories:
  - CheatSheet
tags:
  - PowerShell
---

특정 크기보다 큰 파일 찾기
---

```shell
Get-ChildItem <dir> -recurse | where-object {$_.length -gt 524288000} | Sort-Object length | ft fullname, length -auto
```