---
title: fastlane With Unity
categories:
  - blog
tags:
  - fastlane
  - Unity
  - iOS
  - Android
---
  
## Table of Content
 - [fastlane Getting Started](#fastlane-getting-started)
 - GooglePlay
 - [AppStore](#appstore)

fastlane Getting Started
---
[rbenv](https://github.com/rbenv/rbenv#homebrew)
```bash
# install rbenv
rbenv install ruby
# install bundler
gem install bundler
# install fastlane
cd $WORK_DIR
bundle init
echo "\ngem 'fastlane'" >> ./Gemfile
bundle install
# bundle install

brew install ios-deploy # use install_on_device
```

AppStore
---

1. AppleDeveloper -> Add Identifier
2. fastlane match
   1. [https(grc)](https://docs.aws.amazon.com/ko_kr/codecommit/latest/userguide/setting-up-git-remote-codecommit.html)
   ```bash
   brew install python3
   python3 --version
   pip3 --version
   ```
   2. Install aws cli
   3. Create Access Key ([Permission](https://ap-northeast-2.console.aws.amazon.com/codesuite/codecommit/repositories?region=ap-northeast-2))
   4. [fastlane match with aws code commit](https://qiita.com/sekitaka_1214/items/d3a9c771437e5abeb562)
   5. MATCH_KEYCHAIN_PASSWORD