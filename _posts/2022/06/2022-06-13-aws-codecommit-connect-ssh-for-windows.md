---
title: aws CodeCommit ssh Windows Settings
categories:
  - Blog
tags:
  - AWS CodeCommit
  - ssh
---

references
---

- [SSH 연결을 위한 설정 단계AWS CodeCommitLinux, macOS 또는 Unix의 리포지토리](https://docs.aws.amazon.com/ko_kr/codecommit/latest/userguide/setting-up-ssh-unixes.html)

steps
---

1. IAM 권한 설정은 위 레퍼런스 참조
2. ssh 키 생성

	```shell
	ssh-keygen -t rsa
    cat ~/.ssh/id_rsa.pub
	```

3. public key iam 업로드
4. ssh config 설정

	```text
	Host git-codecommit.*.amazonaws.com↴
	  User <IAM SSH Key ID>↴
	  IdentityFile ~\.ssh\id_rsa↴
	  # Add these to let the SSH client accept RSA keys↴(Windows issue)
	  PubkeyAcceptedAlgorithms +ssh-rsa↴
	  HostkeyAlgorithms +ssh-rsa
	```
 
issue
---

Windows에서 config 설정 시 User, IdentifyFile만 설정하면 아래 에러가 나옴

> Unable to negotiate with <ip> port 22: no matching host key type found. Their offer: ssh-rsa

```text
PubkeyAcceptedAlgorithms +ssh-rsa↴
HostkeyAlgorithms +ssh-rsa
```

이 부분을 추가로 설정하면 해결