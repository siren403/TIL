---
title: Dockerfile CheatSheet
categories:
  - CheatSheet
tags:
  - docker
---

[CMD](https://docs.docker.com/engine/reference/builder/#cmd)
---

```dockerfile
CMD ["echo", "message"]
CMD ["sh", "-c", "echo $ENV"]
CMD ["param1", "param2"]
CMD echo $ENV
```

WORKDIR
---

```dockerfile

# home
FROM alpine
ENV HOME /root
WORKDIR $HOME
CMD pwd
```

RUN
---

```dockerfile
# layer를 생성하기 때문에 패키지 등을 설치할 때 주로 사용.
RUN ["command", "param1", "param2"]
RUN commands
```

ENTRYPOINT
---

```dockerfile
# 한 파일에 하나만 선언 가능하고, 컨테이너로 띄울때 마다 실행 됨.
# 컨테이너 생성 시 해당 커맨드가 실행되고 커맨드로 실행된 프로세스가 종료되면 컨테이너도 종료.
ENTRYPOINT ["command", "param1", "param2"]
ENTRYPOINT commands
```

CMD
---

```dockerfile
# ENTRYPOINT와 같은 시점에 실행 됨.
# 한 파일에 하나만 선언 가능.

CMD ["command", "param1", "param2"]
CMD ["param1", "param2"]
CMD commands

# ENTRYPOINT로는 Command만 지정하고 CMD를 통해 default parameter를 지정 가능하다.
ENTRYPOINT ["echo"]
CMD ["default-param"]

```

```shell
# docker run으로 parameter를 전달하면 default parameter를 대체함.

# echo default-param
docker run <image> 

# echo in-param
docker run <image> in-param
```

Multi Stage Shared ARG, ENV
---

```dockerfile
ARG VERSION=1.0.0
ARG BASE_IMAGE=image-$VERSION

FROM $BASE_IMAGE

ARG VERSION

ENV VERSION $VERSION

CMD ["sh", "-c", "echo $VERSION"]
```

COPY
---

```dockerfile
# multi stage copy
FROM $IMAGE_1 as first

RUN touch test.txt

FROM $IMAGE_2 as second

COPY --from=first test.txt ./test.txt
```

.dockerignore
---

build시 컨텍스트 제외 규칙.

```ignorelang
** # 전체 제외
!*.txt # txt 확장자는 이전 규칙에서 제외
```