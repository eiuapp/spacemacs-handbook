---
title: "Spacemacs Use Zilongshanren Spacemacs Private"
date: 2018-08-28T23:53:02+08:00
draft: false
tags: ["spacemacs"]
categories: ["spacemacs"]
subtitle: "直接使用zilongshanren的sapcemacs配置"
descriptions: ""
bigimg:
---

想直接使用，zilongshanren的 配置

## Env

- os: mac os 10.13.3
- emacs: 26.1
- spacemacs： 0.200.13@26.1


## prepare

在使用前，我们可以安装一些软件

```
brew install emacs
brew install ispell
brew install trash
brew tap caskroom/fonts && brew cask install font-source-code-pro
brew install ctags-exuberant
```

## Step

现在直接就报了一个错误。见 https://github.com/zilongshanren/spacemacs-private/issues/180 

然后，这个时候，从各地方，获知，要用 spacemacs 源码的 devlop分支，而不是master分支。所以。要重新clone一下。

```
➜  .emacs.d git:(develop) pwd
/Users/tomtsang/.emacs.d
➜  .emacs.d git:(develop) git remote -v
origin	https://github.com/syl20bnr/spacemacs.git (fetch)
origin	https://github.com/syl20bnr/spacemacs.git (push)
➜  .emacs.d git:(develop) git branch -v
* develop c122eb6a0 lsp-layer configuration and building blocks for derived layers.
  master  c7a103a77 Fix line separation in README
➜  .emacs.d git:(develop)
```

当然，我们的 zilongshanren 的配置，也应该是 devlop 分支的。

```
➜  .spacemacs.d git:(develop) ✗ pwd
/Users/tomtsang/.spacemacs.d
➜  .spacemacs.d git:(develop) ✗ git remote -v
origin	https://github.com/zilongshanren/spacemacs-private (fetch)
origin	https://github.com/zilongshanren/spacemacs-private (push)
➜  .spacemacs.d git:(develop) ✗ git branch -v
* develop ea09142 Merge branch 'windows' into develop
➜  .spacemacs.d git:(develop) ✗
```

这样，重新启动spacemacs, 就可以使用了。

## QA

### 问题1

```
Cannot find any of the specified fonts (Source Code Pro)! Font settings may not be correct.
```

https://github.com/syl20bnr/spacemacs/issues/7919

https://github.com/adobe-fonts/source-code-pro

```
brew tap caskroom/fonts && brew cask install font-source-code-pro
```

好像，这个问题，已经OK了。


### 修改 title bar中的文字 `guanghui` 为 `zengyunlong`

https://www.emacswiki.org/emacs/FrameTitle

找到 `~/.spacemacs.d/layers/zilongshanren-ui/config.el` 文件, 修改下面地方

```
(setq frame-title-format
      '("" " zengyunlong - "
        (:eval (if (buffer-file-name)
                   (abbreviate-file-name (buffer-file-name)) "%b"))))
```
### 修改 title bar中的图标 icon

参考

https://oomake.com/question/152482

我从一个免费软件网页下载了两个.ico文件(只是[google it](http://www.google.com/search?q=icon+ico+free))，并尝试使用它，这是可行的。以前我尝试过一个.bmp - 因为[frame parameters](http://www.gnu.org/software/emacs/elisp/html_node/Management-Parameters.html)的文档没有指定文件类型。看起来像你必须使用[.ico format](http://en.wikipedia.org/wiki/ICO_(icon_image_file_format))的窗口。现在我的两个emacs框架看起来像是[surfboard](http://www.iconarchive.com/download/icon/iconshock/beach/surf.ico)和[beach chair](http://www.iconarchive.com/download/icon/iconshock/beach/beach-sit.ico)。

```
(set-frame-parameter (car (frame-list)) 'icon-type  "c:/path/to/bitmap/surf.ico")
```

找到 `~/.spacemacs.d/layers/zilongshanren-ui/config.el` 文件, 修改下面地方

```
(setq frame-title-format
            '("" " zyl - "
              (:eval (if (buffer-file-name)
                         (abbreviate-file-name (buffer-file-name)) "%b"))))
(set-frame-parameter (car (frame-list)) 'icon-type  "~/.spacemacs.d/utils/images/ecoicon05_122077.png")
```



## Ref

- https://github.com/zilongshanren/spacemacs-private/issues/180 
