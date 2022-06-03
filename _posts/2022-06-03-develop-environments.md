---
title: Develop Environments
categories:
  - blog
tags:
  - python
  - ruby
---

windows
---

- [chocolatey](https://chocolatey.org/install)

macos
---

- [brew](https://brew.sh/index_ko)

python
---

- windows
  - [pyenv for Windows](https://github.com/pyenv-win/pyenv-win)
    
    ```bash
    choco install pyenv-win
    ```
- macos
  - [**pyenv**](https://github.com/pyenv/pyenv#installation)
    
    ```bash
    brew update
    brew install pyenv
    
    echo 'eval "$(pyenv init -)"' >> ~/.bashrc
    # or
    echo 'eval "$(pyenv init -)"' >> ~/.zshrc
    ```

ruby
---

- windows
  - [RubyInstaller](https://rubyinstaller.org/downloads/)
  - [rbenv for Windows](https://github.com/nak1114/rbenv-win#installation)

- macos
  - [rbenv](https://github.com/rbenv/rbenv#installation)

  ```zsh
  brew install rbenv ruby-build
  rbenv init
  curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-doctor | bash
  ```
  
nodejs
---

- windows
  - [NVM for Windows](https://github.com/coreybutler/nvm-windows)

  ```shell
  choco install nvm
  ```
  
