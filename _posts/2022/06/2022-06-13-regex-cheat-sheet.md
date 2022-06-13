---
title: Regex CheatSheet
categories:
  - CheatSheet
tags:
  - Regex
---

digit
---

```regexp
/^run: \d{6}-\d{6}-\d{4,12}/
```

```text
run: 111212-121212-121212121212 // matched
run: 111212-121212-121
run: 111212-121212-1233  // matched
```

prefix
---

```regexp
/^run: (.*)/
```

```text
run: 111212-121212-121212121212 // matched
111212-121212-121
run: 111212-121212-1233  // matched
```
