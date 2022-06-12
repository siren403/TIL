---
title: yaml CheatSheet
categories:
  - CheatSheet
tags:
  - yaml
---

references
---

- [How do I break a string in YAML over multiple lines?](https://stackoverflow.com/questions/3790454/how-do-i-break-a-string-in-yaml-over-multiple-lines)

strings
---

```yaml
value: >
  a b 
  c d
```

```text
a b c d\n
```

```yaml
value: >-
  test a
  b c
```

```text
test a b c
```

```yaml
value: |
  test
  a
  b c
```

```text
test\ba\nb c\n
```

```yaml
value: |-
  test
  a
  b c
```

```text
test\ba\nb c
```