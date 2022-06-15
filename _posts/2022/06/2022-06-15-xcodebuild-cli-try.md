---
title: xcodebuild cli try
categories:
  - Blog
tags:
  - Xcode
---

cli build
---

```shell
xcodebuild \
-workspace Unity-iPhone.xcodeproj/project.xcworkspace \
-scheme "Unity-iPhone" \
-destination 'platform=iOS,id=<identifier> \
-configuration Debug \
-sdk iphoneos 
```

CodeSign 단계에서 실패 할 경우 login 키체인 해제를 할 수 없어 발생 할 수 있다.

```shell
security unlock-keychain -p YOUR_PASSWORD ~/Library/Keychains/login.keychain-db
```

빌드 전 미리 해제해두고 실행하면 됨. (유지시간 기본 300초)

- [xcodebuild command failing on codesign but logs show incorrect profile uuid being used](https://stackoverflow.com/questions/30089572/xcodebuild-command-failing-on-codesign-but-logs-show-incorrect-profile-uuid-bein)
- [Unlock keychain for longer time](https://gist.github.com/lifuzu/da249bf3267d5893a9f3d6c44b34f5c4)