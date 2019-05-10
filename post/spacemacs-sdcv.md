(未完成)
spacemacs 使用 sdcv

## env

env-wsl

## step

### backgroud ###

https://github.com/manateelazycat/sdcv

然后,配置后,出了问题,提 issue

https://github.com/manateelazycat/sdcv/issues/7

作者说可能是 popup window 的问题(事后证明不是这个问题),关键,我现在对这个 popup window 不熟悉呀.

后来 按 
https://github.com/manateelazycat/lazycat-emacs 来安装成功后, 依然, 也是出现了框框,没有结果.

这就说明, 一定要先在 lazycat-emacs 下解决掉, 才有机会, 迁移到 spacemacs 上来.

那就回头去弄 lazycat-emacs 吧.

可能的问题点:

- ubuntu 在 wsl 中, 所以 mobaxterm xserver 的 x server 会不会过滤掉了信息.
- 在windows下启动 lazycat-emacs 会有效果么?(因为文件路经的问题,后来没有继续尝试)

### mobaxterm xserver ###

[windows上完美的X-server服务器软件：MobaXterm](https://www.cnblogs.com/jinzhenshui/p/9089328.html)

设置成 xserver remote access : full 也没有达到效果.

说明问题不在这里.

### 去除 load-file */sdcv.el 

这种方式, 居然, `M-x sdcv-search-pointer+` 可以得到 结果.

说明:

- 与 popup window 无关
- 与 load-file */sdcv.el 相关

### 去 sdcv.el 文件中 debug ###

通过基本的 `(message ***)` 去 debug, 依次找到

- sdcv-search-pointer+
- sdcv-search-simple
- sdcv-search-with-dictionary
- sdcv-translate-result
- shell-command-to-string
- format
- sdcv-filter

最后,知道,原理,就是 format 成 string, 把 string 传给 shell-command-to-string 返回 shell 下执行 sdcv 命令的结果.

重点则放在检查 sdcv-translate-result 这个函数上.

因为,之前,我们知道, 如果不加载 load-file */sdcv.el 则有结果,那么,找到 这个情况下的 sdcv.el 文件. 

直接去比较这2个 sdcv.el 文件的差异就应该能知道了.  

```bash
+  (message "sdcv-translate-result word is %s" word)
+  (message "sdcv-translate-result dictionary-list is %s" dictionary-list)
   (sdcv-filter
    (shell-command-to-string
     ;; Set LANG environment variable, make sure `shell-command-to-string' can handle CJK character correctly.
-    (format "LANG=en_US.UTF-8 %s -x -n %s %s --data-dir=%s"
+    ;; (format "LANG=en_US.UTF-8 %s -x -n %s %s --data-dir=%s"
+    (format "LANG=en_US.UTF-8 %s -n %s %s --data-dir=%s"
```

最后找到了原因了. 
`(format "LANG=en_US.UTF-8 %s -x -n %s %s --data-dir=%s"` 变成 
`(format "LANG=en_US.UTF-8 %s -n %s %s --data-dir=%s"` 

结果就出来了.

其中这个 format 的输出类似于:

`LANG=en_US.UTF-8 sdcv -n -u "懒虫简明英汉词典" -u "懒虫简明汉英词典" -u "KDic11万英汉词典" hero --data-dir=~/.stardict/dic`

或

`LANG=en_US.UTF-8 sdcv -n -u "懒虫简明英汉词典" -u "懒虫简明汉英词典" -u "KDic11万英汉词典" hero --data-dir=/mnt/c/Users/a/wsl/home/v/lazycat-emacs/site-lisp/sdcv-dict`

按理说, 上面这些语句,直接放在 bash 下, 是可执行,且有返回的.

### (可跳过)emacs下lazycat-emacs 尝试

既然我们在spacemacs中成功了,那么emacs下,也应该可以

这部分,可参看 https://eiu.app/emacs-handbook/post/lazycat-emacs.html










### sdcv 发音 ###


(setq sdcv-say-word t)

```
- 直接 ssh 运行远程 Emacs  放弃治疗。
- tramp 或者反向穿透回来（讨论：关于远程文件编辑的方式选择 4），用的还是本地电脑的播放系统。
```


