[git lfs](https://git-lfs.github.com/)
---

>[github lfs storage](https://hbase.tistory.com/221)

```bash
# git lfs 세팅. 사용자 계정 당 한번이면 됨.
git lfs install

# add lfs
git lfs track "*.psd"

# track 설정 파일 버전관리 추가
git add .gitattributes
```

> [migrate import](https://github.com/git-lfs/git-lfs/blob/main/docs/man/git-lfs-migrate.1.ronn#import)
```bash
# 50MB이상 파일 lfs로 이전
git lfs migrate import --above=50MB
```

git reset
---

[gist](https://gist.github.com/qkrsogusl3/77238d4b2929fb90107c363bb3fd6048#file-git-cli-cheat-sheet-md)
[git tree visualized image](https://da-nyee.github.io/posts/git-git-reset-git-reflog/)

https://developer-ankiwoong.tistory.com/773

ssh
---

```bash
# start ssh agent
eval $(ssh-agent)

# add private key 재시작 시 다시 설정해야 함
ssh-add ~/.ssh/key_rsa
# or
# mac에서 다시 시작 시 암호를 유지하기 위해 키체인에 저장
ssh-add --apple-use-keychain ~/.ssh/id_rsa
```

buildkite
---

- slug

  파이프라인 이름 기반으로 생성되는 명칭.
  build url 생성 시에 사용 됨.
  lower case + 언더바는 하이픈으로 변경 됨.
  > aws_UActions -> aws-uactions

- [에이전트 관련 파일 경로](https://buildkite.com/docs/agent/v3/macos#file-locations)

- secret env

  에이전트 별 환경변수로 시크릿 환경변수 세팅

> sample
```yaml
steps:
  - label: "Run Unity Android Build"
    env:
      UNITY_VERSION: "2021.2.12f1"
      EXECUTE_METHOD: "UActions.Bootstrap.Run"
      JOB: "build-apk"
      BUILD_TARGET: "Android"
      UNITY_EDITOR: "/Applications/Unity/Hub/Editor/2021.2.12f1/Unity.app/Contents/MacOS/Unity"
    commands: 
    - "$$UNITY_EDITOR -batchmode -quit -buildTarget $$BUILD_TARGET -executeMethod $$EXECUTE_METHOD -job $$JOB"
```

klaytn dapp project
---

- react 
- truffle
- drizzle
- redux
- redux-saga

> truffle console
```
let instance = await Counter.deployed()
```

1. new react project
2. `truffle init`
3. create contract
4. create migration
5. `yarn add dotenv`
6. `yarn add truffle-hdwallet-provider-klaytn`
7. setting truffle-config.js
8. `truffle deploy --network <network>`

[HARDHAT AND ETHERS](https://ethereum.org/ko/developers/tutorials/waffle-say-hello-world-with-hardhat-and-ethers/)
- react
- hardhat

```bash
# create react project
yarn add -D hardhat @nomiclabs/hardhat-ethers ethers @nomiclabs/hardhat-waffle ethereum-waffle chai
mkdir contracts
touch ./contracts/<Contract>.sol

mkdir scripts

mkdir test
touch ./test/sample-test.js

```

post processing
---

- [언리얼 - 포스트 프로세싱 머티리얼](https://docs.unrealengine.com/4.26/ko/RenderingAndGraphics/PostProcessEffects/PostProcessMaterials/)
- [【UE4】포스트 프로세스로 만드는 아웃라인](https://qiita.com/4_mio_11/items/acb02e9d3e81d34b45e0)
- [URP 셰이더 코딩 튜토리얼 : 제 1편 - Unlit Soft Shadow](https://blog.naver.com/mnpshino/221844164319)

graphics
---

- [렌더링 파이프라인의 좌표 공간들 - clip space](http://rapapa.net/?p=3531)
- [Transition Shader in godot](https://www.youtube.com/watch?app=desktop&v=K9FBpJ2Ypb4)
- [Godot Shader Tutorial (1): Intro to Shader Programming](https://www.youtube.com/watch?v=xoyk_A0RSpI)

ssh
---

- [Understanding ssh-agent and ssh-add - Enter passphrase for key '/home/user/.ssh/id_rsa':](http://blog.joncairns.com/2013/12/understanding-ssh-agent-and-ssh-add/)

unity - uitoolkit
---

- [AspectRatioPanel.cs](https://gist.github.com/pbhogan/2094a033c094ddd1b0b8f37a5dffd005)

  {% gist pbhogan/2094a033c094ddd1b0b8f37a5dffd005 %}

- [URP로 시작하세요! 셰이더 입문](https://qiita.com/flankids/items/a92b14834792a10798e5)
- [L book](https://www.amazon.co.jp/HLSL-%E3%82%B7%E3%82%A7%E3%83%BC%E3%83%80%E3%83%BC%E3%81%AE%E9%AD%94%E5%B0%8E%E6%9B%B8-%E3%82%B7%E3%82%A7%E3%83%BC%E3%83%87%E3%82%A3%E3%83%B3%E3%82%B0%E3%81%AE%E5%9F%BA%E7%A4%8E%E3%81%8B%E3%82%89%E3%83%AC%E3%82%A4%E3%83%88%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%B3%E3%82%B0%E3%81%BE%E3%81%A7-%E6%B8%85%E5%8E%9F-%E9%9A%86%E8%A1%8C/dp/4798164283)