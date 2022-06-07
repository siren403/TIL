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


docker file arg

```shell
docker build \
-t essearch/ess-elasticsearch:1.7.6 \
--build-arg number_of_shards=5 \
--build-arg number_of_replicas=2 \
--no-cache .
```

```dockerfile
FROM alpine
ARG number_of_shards
RUN echo $number_of_shards
```

image
---

```shell
docker images -a

# image id
docker images -a -q '<Image>'
```

```shell
# remove image
docker image rm <IMAGE>
docker rmi <IMAGE>
```

container
---

```shell
docker ps -a

# image 이름으로 id 검색
docker ps -a --format {% raw %}"{{.ID}} {{.Image}}"{% endraw %} | grep '<Image>' | awk '{print $1}'
```

build
---

```shell
# docker build -t <name:tag> --build-arg <key>=<value> -f <file> <path>
docker build -t test:1.0 --build-arg MSG=test -f Dockerfile .
```
