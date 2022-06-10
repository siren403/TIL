---
title: Docker Compose CheatSheet
categories:
  - CheatSheet
tags:
  - Docker
  - Docker Compose
---

docker-compose.yml
---

```yaml
version: "2"
services:
  unity-android:
    build:
      dockerfile: ./Dockerfile
      context: ~/workspace/unity-manual-activation-with-docker
      args:
        UNITY_VERSION: 2021.2.12f1
        IMAGE_PLATFORM: android
        BUILD_TARGET: android
        LICENSE_FILE_NAME: unity-license.ulf
    image: unity-android
    volumes:
      - $PWD:/mnt
    environment:
      JOB_NAME: build-apk
```

up
---

```shell
docker-compose up -d # background
docker-compose up --force-recreate # force new container
docker-compose up --build # image build -> compose up
```

down
---

```shell
docker-compose down
docker-compose down --rmi all # remove images
```
