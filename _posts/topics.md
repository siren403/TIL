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