---
title: buildkite로 Unity CD 세팅해보자
categories:
  - Blog
tags:
  - Unity
  - CD
  - Buildkite
header:
  image: /assets/uml/unity-cd-with-buildkite.png
---

Dependencies
---

- aws CodeCommit, Lambda
- Buildkite
- Unity
- UActions (Unity Package)

TL;DR
---

Repository는 회사에서 aws써서 CodeCommit으로 할거.

유니티 빌드 세팅은 UActions로 잡을거고 Buildkite로 파이프라인 실행함.
self-hosted로 할꺼니까 빌드머신 준비해야 해. 여기선 macos를 빌드머신으로 쓸거니까 참고.

파이프라인 트리거는 Lambda로 CodeCommit 이벤트 받아서 Buildkite 빌드실행
url을 호출해줄거야. ok?

![arch]({{ site.url }}{{ site.baseurl }}/assets/uml/unity-cd-with-buildkite.png)

유니티 빌드 세팅
---

패키지부터 받아봐

[UActions](https://github.com/qkrsogusl3/UActions/tree/main/Packages/UActions) 이거 쓸꺼니까 ㄱㄱ

빌드만 뽑아보면 되니까 밑에꺼 복붙하고 넘어가자

> workflow.yaml

```yaml
env:
  COMPANY: tiny
  PRODUCT_NAME: UnityLane
jobs:
  build-apk:
    platform: android
    steps:
      - uses: player-settings
        with:
          company-name: $(COMPANY)
          product-name: $(PRODUCT_NAME)
          preset: Assets/PlayerSettings
      - uses: player-settings-android
        with:
          package-name: com.$(COMPANY).$(PRODUCT_NAME)
          architectures: !architectures
            - "ARMv7"
            - "ARM64"
      - uses: build
        with:
          path: $(PROJECT_PATH)/Build/$(PLATFORM)/$(PRODUCT_NAME)
```

로컬에서 빌드 잘나오는지 한번 체크하고 가자고

buildkite 세팅
---

[Buildkite](https://buildkite.com)가서 계정 만들고 [Document](https://buildkite.com/docs)도 한번 봐바

구성은 [Getting Started](https://buildkite.com/docs/tutorials/getting-started)보고 하면 됨.

![NewPipeline1](/assets/images/unity-cd-with-buildkite/buildkite-new-pipeline-1.png)

Name은 뒤에 Lambda에서 쓸 코드보면 Repository이름에 prefix붙혀서 콜할꺼니까 aws-<RepoName>으로 해

Repository URL은 ssh로 인증해서 받을꺼니까 ssh세팅도 ㄱ

[SSH 연결을 위한 설정 단계AWS CodeCommitLinux, macOS 또는 Unix의 리포지토리](https://docs.aws.amazon.com/ko_kr/codecommit/latest/userguide/setting-up-ssh-unixes.html)

> ssh config
```
Host git-codecommit.*.amazonaws.com
  User <SSH 키 ID>
  IdentityFile ~/.ssh/<private key>
```

![NewPipeline2](/assets/images/unity-cd-with-buildkite/buildkite-new-pipeline-2.png)

Run Script는 yaml 스타일로 다시 작성할꺼니까 대충 넘어가도 됨

![EditSteps](/assets/images/unity-cd-with-buildkite/buildkite-edit-steps.png)

EditSteps로 넘어오면 이렇게 돼있는데 'Convert to YAML Steps' 누르고 'Save Steps'

이제 pipeline에서 실행한다고 한 run.sh 스크립트 만들면 됨

> scripts/run.sh
```bash
echo run pipeline
```

스크립트 만들고 일단 커밋.

**Warning Notice:** 에이전트에서 실행할 스크립트이니까 커밋하기전에 파일실행 권한 줘야함
{: .notice--warning}

테스트 한번 해볼겸 NewBuild 눌러서 잘 되는지 확인.

잘 되면 이제 Lambda 세팅하러 ㄱ

[BuildKite-With-CodeCommit](https://github.com/qkrsogusl3/BuildKite-With-CodeCommit)

다른 오픈소스에서 url부분만 고쳐서 올린 프로젝트임.
받아서 빌드하면 zip파일 하나 나오는데 그걸 Lambda에 올리면 됨.

[//]: # (Window면 [zip]&#40;http://stahlworks.com/dev/?tool=zipunzip&#41; 받아놓고 `yarn build-win`으로 빌드하면 됨.)

올린 함수 구성으로 가서 환경변수 추가

```
BUILDKITE_ORG
BUILDKITE_TOKEN
```

main 브랜치에서 push 발생 시 실행되도록 트리거 세팅.

이제 Repository에 push해봐

mac fastlane settings
---

- aws cli
- `brew install pyenv`
- `pip install git-remote-codecommit`
- `MATCH_PASSWORD=`
- `fastlane match development --readonly`


checklist
===

Enter passphrase k...
---

ssh agent 세팅 다시 해봐야 함.

[맥에서 키체인을 활용한 세팅](https://apple.stackexchange.com/questions/48502/how-can-i-permanently-add-my-ssh-private-key-to-keychain-so-it-is-automatically)

```shell
# agent 시작
eval "$(ssh-agent -s)"
# add key
ssh-add --apple-use-keychain ~/.ssh/<private key>
# 체크
ssh-add -l 
```

