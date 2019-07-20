+++
title = "macos 下 spacemacs 使用 sdcv"
date = 2019-07-19
lastmod = 2019-07-19T19:02:32+08:00
tags = ["emacs", "spacemacs"]
categories = ["spacemacs"]
draft = false
weight = 3003
+++

(未完成)

macos 下 spacemacs 使用 sdcv

## env ##

- os: macos
- emacs: spacemacs

## step ##
### 总结 ###

此文与 https://eiu.app/emacs-handbook/post/lazycat-emacs.html 配合着看

### backgroud ###

https://github.com/eiuapp/lazycat-emacs/blob/eiuapp/README.eiuapp.md

https://github.com/manateelazycat/sdcv

### 安装 sdcv ###

```
brew install sdcv
```

但是

```
brew install stardict 
```

出错了.

下载 [stardict-3.0.5-beta1-macosx.tar.bz2](https://sourceforge.net/projects/stardict-4/files/MacOSX/stardict-3.0.5-beta1-macosx.tar.bz2/download)

解压后, 出来的是APP，也不是我要的词典呀，怎么用呀？

后面会发现, 好像, 这个还真的是可以不运行.

找到了 github 官网 https://github.com/huzheng001/stardict-3

又参考:

https://tc77.com/articles/macosx-command-line-dictionary-stardict/


### 下载字典 ###

知道,我们要去下载这个字典.

找到官网

http://stardict-4.sourceforge.net/
http://stardict-4.sourceforge.net/index_cn.php

找到 词典下载地圵

http://download.huzheng.org/

找到 `简体中文`, 进入 

http://download.huzheng.org/zh_CN/

比如,我们这里下载 "懒虫简明英汉词典", "懒虫简明汉英词典" 到 ~/Download 文件夹下

`stardict-lazyworm-ec-2.4.2.tar.bz2`, `stardict-lazyworm-ce-2.4.2.tar.bz2`

运行下面的命令.

```
mkdir -p $HOME/.stardict/dic
tar -xvzf ~/Downloads/dict.tgz -C $HOME/.stardict/dic
```

实操

```
➜  dic git:(master) ✗ tar -xjvf ~/Downloads/stardict-lazyworm-ce-2.4.2.tar.bz2 -C ~/.stardict/dic
x stardict-lazyworm-ce-2.4.2/
x stardict-lazyworm-ce-2.4.2/lazyworm-ce.dict.dz
x stardict-lazyworm-ce-2.4.2/lazyworm-ce.ifo
x stardict-lazyworm-ce-2.4.2/lazyworm-ce.idx
➜  dic git:(master) ✗ tar -xjvf ~/Downloads/stardict-lazyworm-ec-2.4.2.tar.bz2 -C ~/.stardict/dic
x stardict-lazyworm-ec-2.4.2/
x stardict-lazyworm-ec-2.4.2/lazyworm-ec.ifo
x stardict-lazyworm-ec-2.4.2/lazyworm-ec.idx
x stardict-lazyworm-ec-2.4.2/lazyworm-ec.dict.dz
➜  dic git:(master) ✗ ls ~/.stardict/dic
x stardict-lazyworm-ce-2.4.2	stardict-lazyworm-ec-2.4.2
➜  dic git:(master) ✗
```

看到了, 把这些词典已经放在了 ~/.stardict/dic 文件夹下了。

那怎么验证，这些安装的词典，能使用呢？

### 查看词典的使用名 ###

因为，词典不止一个，那么要区分使用的是哪一个词典，所以要查看一下。

运行 `cd dict & cat dict.ifo | grep bookname`

```
➜  dic git:(master) ✗ cd stardict-lazyworm-ec-2.4.2 & ls
lazyworm-ec.dict.dz  lazyworm-ec.idx  lazyworm-ec.ifo
➜  stardict-lazyworm-ec-2.4.2 git:(master) ✗ cat lazyworm-ec.ifo | grep bookname
bookname=懒虫简明英汉词典
```

### shell 中 翻译 ###

运行 `sdcv -n -u "词典bookname" "被翻译的单词（如 hero）" --data-dir=词典所在目录`

#### 英译汉 ####

如, 英文单词 `hero` 使用 在 `~/.stardict/dic` 目录下的 `懒虫简明英汉词典` 进行翻译：

```
➜  stardict-lazyworm-ec-2.4.2 git:(master) ✗ sdcv -n -u "懒虫简明英汉词典" hero --data-dir=~/.stardict/dic
save to cache /Users/tomtsang/.stardict/dic/stardict-lazyworm-ec-2.4.2/lazyworm-ec.idx
Found 1 items, similar to hero.
-->懒虫简明英汉词典
-->hero

['hiәrәu]
n.
英雄, 男主角, 男主人公

➜  stardict-lazyworm-ec-2.4.2 git:(master) ✗
```

#### 汉译英 ####

https://sites.google.com/site/gtonguedict/home/stardict-dictionaries

下载了 `Chinese-English dictionary` 词典

如, 中文单词 `你好` 使用 在 `~/.stardict/dic` 目录下的 `懒虫简明英汉词典` 进行翻译：

```
➜  stardict-chinese-eng-2.4.2 git:(master) ✗ pwd
/Users/tomtsang/.stardict/dic/stardict-chinese-eng-2.4.2
➜  stardict-chinese-eng-2.4.2 git:(master) ✗ cat chinese-eng.ifo | grep bookname
bookname=Chinese-English dictionary
➜  stardict-chinese-eng-2.4.2 git:(master) ✗ sdcv -n -u "Chinese-English dictionary" "你好" --data-dir=~/.stardict/dic
Found 1 items, similar to 你好.
-->Chinese-English dictionary
-->你 你


[ni3] /you/

➜  stardict-chinese-eng-2.4.2 git:(master) ✗
```

结果是出来了, 但是很明显呀, 翻译的是 `你`, 而不是 `你好`, 这就有点尴尬了。

说明，我们在 shell 中翻译成功

#### 错误 ####

如果使用错误会报成下面这样

```
➜  stardict-chinese-eng-2.4.2 git:(master) ✗ sdcv -n -u "懒虫简明英汉词典" -u "懒虫简明汉英词典" -u "KDic11万英汉词典" hero --data-dir=~/.stardict/dic
Internal error: map::at:  key not found
➜  stardict-chinese-eng-2.4.2 git:(master) ✗ sdcv -n -u "Chinese-English dictionary" hero --data-dir=~/.stardict/dic
save to cache /Users/tomtsang/.stardict/dic/stardict-chinese-eng-2.4.2/chinese-eng.idx
Nothing similar to hero, sorry :(
```

### emacs 中翻译 ###

当完成了 shell 中的翻译后，其实，也就完成了 emacs 中翻译。只不过，我们在 emacs 中要加一些词典。

配置文件在 `~/.spacemacs.d/layers/zilongshanren-tomtsang/packages.el`

关键配置如下：

```
(defun zilongshanren-tomtsang/init-sdcv ()
  (use-package sdcv
    ;; :demand t
    :init
    :config
    (add-to-list 'load-path (expand-file-name "~/.spacemacs.d/layers/manaul-install/"))
    (require 'company-english-helper)
    (require 'insert-translated-name)
    (load-file "~/.spacemacs.d/layers/manaul-install/posframe.el")
    (load-file "~/.spacemacs.d/layers/manaul-install/sdcv.el")
    ;; (require 'sdcv)
    ;; (setq sdcv-dictionary-data-dir lazycat-emacs-sdcv-data-dir) ;设置星际译王本地词典的目录
    (setq sdcv-dictionary-data-dir "~/.stardict/dic")
    (setq sdcv-say-word-p t)	     ;say word after search
    (setq sdcv-dictionary-simple-list    ;星际译王屏幕取词词典, 简单, 快速
          '("懒虫简明英汉词典"
            "懒虫简明汉英词典"
            "KDic11万英汉词典"))
    (setq sdcv-dictionary-complete-list     ;星际译王的词典, 完全, 详细
          '(
            "懒虫简明英汉词典"
            "英汉汉英专业词典"
            "XDICT英汉辞典"
            "stardict1.3英汉辞典"
            "WordNet"
            "XDICT汉英辞典"
            "Jargon"
            "懒虫简明汉英词典"
            "FOLDOC"
            "新世纪英汉科技大词典"
            "KDic11万英汉词典"
            "朗道汉英字典5.0"
            "CDICT5英汉辞典"
            "新世纪汉英科技大词典"
            "牛津英汉双解美化版"
            "21世纪双语科技词典"
            "quick_eng-zh_CN"
            ))
    )
  )
```

如果，对于，上面出现的词典，没有下载完全，也可以使用，具体效果如下：

- 运行 `M-x sdcv-check` 时, 报出部分词典未安装
- 运行 `M-x sdcv-search-point+` 时，使用的是上面的3部词典，所以只要有结果，就会返回。

### FAQ(未解决) ###

#### 读出英文单词 ####

从 http://stardict-4.sourceforge.net/index_cn.php 找到

http://reciteword.sourceforge.net/


##### sdcv 发音 #####


(setq sdcv-say-word t)

```
- 直接 ssh 运行远程 Emacs  放弃治疗。
- tramp 或者反向穿透回来（讨论：关于远程文件编辑的方式选择 4），用的还是本地电脑的播放系统。
```



