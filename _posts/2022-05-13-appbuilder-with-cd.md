---
title: AppBuilder with CD
categories:
  - blog
tags:
  - Unity
  - CD
---

case 1
---

* repository : aws codecommit
* event : aws lambda
* pipeline : buildkite

>           [aws]                   [buidkite]            [local]
>
>[push -> lambda trigger] -> [post build url -> agent] -> [build script] 

