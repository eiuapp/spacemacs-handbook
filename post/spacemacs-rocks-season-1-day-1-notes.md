+++
title = "Spacemacs Rocks Day 1, Features & Workflow"
date = 2017-12-19
lastmod = 2018-11-22T19:02:32+08:00
tags = ["emacs", "spacemacs"]
categories = ["spacemacs"]
draft = false
weight = 3003
+++

[spacemacs-rocks(1)](http://v.youku.com/v%5Fshow/id%5FXMTM1Njc3MzU4MA==.html?spm=a2h0j.11185381.listitem%5Fpage1.5!30~A)


## 跳到函数定义，并返回 ##i

- describe-function: C-h f
- find-function: C-h C-f 或者 , g g
    - 然后 C-o 会切回到上一个 buffer

## 跳 变量

- C-h v
- C-h C-v

## Navigation functions in current file ##

> SPC s l （已经失效，因为没有找到这个快捷键）

替换成

> M-x helm-jump-in-buffer

这样，就可以把它们绑定一下。
