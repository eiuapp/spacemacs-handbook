+++
title = "Spacemacs Rocks Day 8, Spacemacs as a JavaScript/Node.js IDE"
date = 2018-11-17T11:00:00+08:00
lastmod = 2018-11-19T23:07:58+08:00
tags = ["emacs", "spacemacs"]
categories = ["spacemacs"]
draft = false
weight = 3010
+++

## Autocompletion {#autocompletion}

1.  company-etags vs company-tern

使用的场景不同. company-tern 用于小型项目开发; company-etags 用于大型项目开发.

但是,我目前参与的项目可以说,都是一些小型项目(代码量不会超出10**4),所以大多数情况下,我们用 company-tern 就可以了.

2.  hippie-expand


> M-x hippie-expand

或者

> M-/

比如: 输入 con 后,会有补全下拉选择项目, 按 C-g 取消, 再按 M-/ 就可以进行hippie-expand补全.

## Jump to definition {#jump-to-definition} ##

1.  SPC s l to jump to function definitions.  ctags.
2.  SPC m g d/ etags-select
3.  SPC s p / SPC o s to search keywords
4.  SPC m g g if use tern.js


### jump to function definitions.  ctags> SPC s l {#jump-to-function-definitions-dot-ctags-spc-s-l} ###

已经失效了


### etags-select {#etags-select} ###

etags, 基于正则表达式的补全

> SPC m g d
和
> , g d
相同


### tern-mode精确补全下, 跳转定义 ###

> M-x tern-find-definitions

或者对应的快捷鍵

> SPC m g g 也就是 > , g g


## Syntax check {#syntax-check}

1.  flycheck with jshint / eslint
2.  js2-mode checking


### 开启语法检查 {#开启语法检查}

> SPC t S

在 ubuntu 下,会发现失效了. 怎么办?



### 查看语法错误信息 {#查看语法错误信息}

> SPC e l

在 ubuntu 下,会发现失效了. 怎么办?

## REPL {#repl}

1.  jscomint

jscomint has better ES6 support. But the keybinding are not perfect

1.  nodejs repl

ES6 support is not good, but has better keybinding.


### nodejs repl {#nodejs-repl}

#### 开启

> M-x nodejs-repl

#### 关闭 nodejs-repl

> .exit

#### 去 nodejs-repl buffer执行当前行 ####

> M-x nodejs-repl-eval-dwim

或者快捷鍵

> , e d

已修改成

> , s d

#### 去 nodejs-repl buffer执行当前buffer ####

> M-x nodejs-repl-eval-buffer 

或者快捷鍵

> , s b


#### 具体其它命令，可以搜索文档 ####

> C-h o nodejs-repl-command

然后，查看 nodejs-repl-mode 文档



## Format code {#format-code}

1.  js beautify

> M-x web-beautify-js

或者快捷鍵

> , = = 

运行前，需要先安装 js-beautify

```
$ npm install -g js-beautify
```

其中js-beautify的配置文件是 \`~/.jsbeautifyrc\`.

如果不想安装，则使用：

> SPC j =

runs the command spacemacs/indent-region-or-buffer.
