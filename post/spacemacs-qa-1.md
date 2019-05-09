---
title: "Spacemacs Qa 1"
date: 2018-08-25T12:33:47+08:00
draft: false
tags: ["spacemacs", "emacs"]
categories: ["spacemacs"]
subtitle: "Symbol's function definition is void"
descriptions: ""
bigimg:
---

## Env

### env-1
- os: mac os 10.13.3
- emacs: 26.1
- spacemacs： 0.200.13@26.1

### env-2
- os: ubuntu 16.04
- emacs: 26.1
- spacemacs： 0.200.13@26.1

## 未解决

## 已解决
### QA

Q:

Description :octocat:
```
Error (use-package): org-projectile :config: Symbol's function definition is void: org-projectile-per-project
```

A:

参考 https://github.com/syl20bnr/spacemacs/issues/9374 知道

I also faced this issue today after updating all packages.

`find ~/.emacs.d/elpa/org-projectile-20180601.242/ -name "*elc" -delete` and restarting fixed it.



###  让 spacemacs(base windows)中的git生效

现在就是SPC g s后，c c（commit）不能用。主要原因就是提示没有设置

`git config --global user.name`


