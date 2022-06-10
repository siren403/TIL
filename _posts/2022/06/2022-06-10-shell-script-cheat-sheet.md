---
title: shell script CheatSheet
categories:
  - CheatSheet
tags:
  - sh
---

references
---

- [explainshell](https://explainshell.com/)

[Shebang](https://en.wikipedia.org/wiki/Shebang_(Unix))
---

해당 스크립트를 실행할 인터프리터 지시문

```shell
#!/bin/bash
```

exist file
---

[Bash Conditional Expressions](https://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html)

```shell
if[-f "$FILE_NAME"];then
	echo "exist"
else 
  	echo "not exist"
fi
```

`-f`: 파일 체크  
`-d`: 디렉토리 체크  
`-e`: 구별하지않고 체크  
`-x`: 실행가능 체크  