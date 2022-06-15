---
title: ssh remote login
categories:
  - Blog
tags:
  - ssh
---

references
---

- [SSH Keygen을 이용한 키 생성 방법과 ssh-agent에 대한 간단 설명](https://devlog.jwgo.kr/2019/04/17/ssh-keygen-and-ssh-agent/)

start ssh agent
---

```shell
# macOS
eval "$(ssh-agent -s)"

# windows
start-ssh-agent
```

```shell
ssh-keygen -t rsa
```

```shell
# powershell
scp $env:USERPROFILE/.ssh/id_rsa.pub <username>@<host>:<path>

# zsh
scp $HOME/.ssh/id_ras.pub ...
```


```shell
cat ./id_rsa.pub >> ~/.ssh/authorized_keys
```


기본 키(is_rsa)가 아닌 다른 키(ex. work_rsa)로 접속하려면

접속 테스트
known_hosts에 추가할지 메세지가 나옴
```shell
ssh <username>@<host> -i <path/to/key>
```

```shell
# agent keys
ssh-add -l
```

issue
---

---

Windows에서 AWS CodeCommit ssh 접속을 위해 PubkeyAcceptedAlgorithms, HostkeyAlgorithms 설정을 했을 때
macOS에 ssh 접속이 안되는 경우.

```text
C:\\Users\\Aaron/.ssh/config: line 8: Bad configuration option: pubkeyacceptedalgorithms
C:\\Users\\Aaron/.ssh/config: terminating, 1 bad configuration options
```

운영체제 별로 OpenSSH 구현이 다르기 때문에 옵션을 찾을 수 없는 경우가 있다.

~/.ssh/config

```text
Host *
  IgnoreUnknown PubkeyAcceptedAlgorithms,HostkeyAlgorithms
```

위 옵션을 맨 위에 추가

[.ssh/config: "Bad configuration option: UseKeychain" on Mac OS Sierra 10.12.6](https://stackoverflow.com/questions/47455300/ssh-config-bad-configuration-option-usekeychain-on-mac-os-sierra-10-12-6)
[SSH: Bad configuration option: usekeychain](https://www.unixtutorial.org/ssh-bad-configuration-option-usekeychain/)

---

