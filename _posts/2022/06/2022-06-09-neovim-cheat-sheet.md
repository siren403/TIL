---
title: Neovim CheatSheet
categories:
  - CheatSheet
tags:
  - neovim
---

references
---

- [From init.vim to init.lua](https://teukka.tech/luanvim.html)
- [neovim configuration from gist](https://gist.github.com/synasius/5cdc75c1c8171732c817)

lua config
---

init.vim

```text
lua << EOF

vim.opt.list = true
vim.opt.listchars:append("eol:↴")

require("indent_blankline").setup {
    show_end_of_line = true,
}

EOF
```

plugins
---

- [Indent Blankline](https://github.com/lukas-reineke/indent-blankline.nvim)
  indent line
- [barbar.nvim](https://github.com/romgrk/barbar.nvim)
  tabbar
- [onedark](https://github.com/navarasu/onedark.nvim)