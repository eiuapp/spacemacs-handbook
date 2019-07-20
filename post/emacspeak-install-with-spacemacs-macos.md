---
title: "emacspeak install with spacemacs and macos"
date: 2018-08-28T23:53:02+08:00
draft: false
tags: ["spacemacs"]
categories: ["spacemacs"]
subtitle: "安装emacspeak(基于spacemacs和macos)"
descriptions: ""
bigimg:
---

当你看tutorial时，会不自觉地想睡觉，真的麻烦，这时，如果有语音帮忙，陪你一起看文档，是不是会好一点呢？

emacspeak 会来帮助你哟。

spacemacs install emacspeak, 其它系统，其它emacs安装方法，则基本类似了。

## env 

why i do this?

- https://blog.csdn.net/redguardtoo/article/details/7222501/

->

- https://sachachua.com/blog/2012/07/transcript-emacs-chat-john-wiegley/

seach keyword "emacspeak"

-> 

- https://github.com/tvraman/emacspeak
- http://tvraman.github.io/emacspeak/manual/

## step

- http://tvraman.github.io/emacspeak/manual/Quick-Installation.html#Quick-Installation
- https://gist.github.com/AmandaKLacy/bbdcdaa9bef885bbafe25d8a0f8432af

```
mv ~/Downloads/emacspeak-49.0.tar.bz2 ~/Downloads/emacspeak-49.0/ soft
cd soft/emacspeak-49.0
make config
make
mkdir -p ~/emacs/emacspeak/
cp -a ./* ~/emacs/emacspeak
export DTK_PROGRAM=mac
echo "export DTK_PROGRAM=mac" >> ~/.zshrc
source ~/.zshrc
cd ~/emacs/emacspeak/servers
chmod +x ./mac
./mac
```

### How to test the speech server:

```
### Type the following commands at a terminal prompt:
cd ~/source/emacspeak/servers
chmod +x ./mac
./ mac  #You should hear Emacspeak "server."
q “This is a test”
d #You should hear "this is a test."
```

### configure spacemacs init.el


```
(defun dotspacemacs/user-config ()

  (require 'cl)
  (setq load-path (cons "~/emacs/emacspeak/lisp" load-path))
  (setq emacspeak-directory "~/emacs/emacspeak")
  (setq dtk-program "mac")
  (require 'emacspeak-setup)
  (require 'mac-voices)
  (emacspeak-tts-startup-hook)
  (dtk-set-rate 300 t)
```

**注意** 这里，要去掉复制过来的 "\" 号，不然，重启会报错的。

### 尝试

`M-x info`, 找到任何文章，然后，就会帮你读出来了。

但是，会发现，发声规则是：

- 进入新buffer时，自动读整篇文章
- 移动光标时，以行为单位

## question

1. 如果以语句或者段落为单位，那就更好了，谁知道怎么做到吗？



