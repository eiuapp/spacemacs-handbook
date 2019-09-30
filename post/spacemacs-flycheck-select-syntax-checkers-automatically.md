---
title: "Spacemacs flycheck select syntax checkers automatically"
date: 2018-08-28T23:53:02+08:00
draft: false
tags: ["spacemacs"]
categories: ["spacemacs"]
subtitle: "使用flycheck时自动选择syntax checker"
descriptions: ""
bigimg:
---


## Env

- os: mac os 10.13.3
- emacs: 26.1
- spacemacs： 0.200.13@26.1

## Step

http://www.flycheck.org/en/latest/user/syntax-checkers.html

先通过 `flycheck-verify-setup` 找到当前mode下所有的 checkers, 如果你想自动使用第3个 checker ,则把第1,2个 disable 就可以了.

比如:

目标: 在js2-mode下自动使用javascript-standard作为 syntax checker.
操作: 在js2-mode下配置

```
;; (add-to-list 'flycheck-checkers 'javascript-standard)
(setq-default flycheck-disabled-checkers '(javascript-eslint javascript-jshint))
```
实操: https://github.com/eiuapp/spacemacs-private-wsl-tl/commit/dda680a7d2a39e3a9df705397a82ff64e4536324

现在直接就报了一个错误。见 https://github.com/zilongshanren/spacemacs-private/issues/180 

# flycheck

https://github.com/flycheck/flycheck/issues/1087

## eslint-auto.el

https://gist.github.com/blue0513/f503c26bf5cb8a1b6fb6e75f1ec91557
https://gist.github.com/ustun/73321bfcb01a8657e5b8

## add-node-modules-path

https://github.com/codesuki/add-node-modules-path

## eslintd-fix

https://github.com/aaronjensen/eslintd-fix
https://github.com/mantoni/eslint_d.js

## js-auto-format-mode
https://github.com/ybiquitous/js-auto-format-mode

这个，蛮好的，可以在 检查代码。

- 本地运行 eslint
- 好像不开启 flycheck-mode 时，依然能使用
- tramp后的远程文件，不能使用

## gist 

https://gist.github.com/mvanzorn/9b7c694cf9369e7379b7723c65b2186f

