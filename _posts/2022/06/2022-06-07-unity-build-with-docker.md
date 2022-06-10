---
title: docker로 Unity Build
categories:
  - Blog
tags:
  - Unity
  - docker
---

Install docker
---

[GameCI](https://game.ci/)
---

Unity CI구축에 필요한 자료들이 있는 사이트.

docker 빌드를 위한 Image들도 업데이트 해주고 있음.

```shell
docker run -it unityci/editor:ubuntu-2021.2.12f1-base-1.0.1
```

[Offline (manual) license activation](https://docs.unity3d.com/Manual/ManualActivationGuide.html)

```shell
unity-editor -batchmode -createManualActivationFile -logfile -
```

```shell
unity-editor -batchmode -manualLicenseFile *.ulf -logfile -
```