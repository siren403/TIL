---
title: Unity SubAsset
categories:
  - blog
tags:
  - Unity
---

case 1
---

* repository : aws codecommit
* event : aws lambda
* pipeline : buildkite

>           [aws]                   [buidkite]            [local]
>
>[push -> lambda trigger] -> [post build url -> agent] -> [build script] 

