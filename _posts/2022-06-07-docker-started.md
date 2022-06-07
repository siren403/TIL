---
title: docker Started
categories:
  - blog
tags:
  - docker
---

TL;DR
---

```shell
# docker run -it -p <host>:<container> -v <host>:<container> --name <name> <image>
docker run -it -p 80:80 -v $PWD:/mnt/dir --name sample alpine

# docker exec <container> <command>
docker exec sample pwd

docker rm <container>
```


볼륨으로 현재 경로 마운트하기
---

$PWD를 인자로 넘겨 설정

```shell
docker run -v $PWD:/mnt/dir alpine
```

docker desktop의 경우 File Sharing에서 마운트 해야 할 경로를 지정해 줘야 한다.
{: .notice--info}


