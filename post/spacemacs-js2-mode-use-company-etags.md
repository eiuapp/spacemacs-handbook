(未完成)
在 spacemacs 中使用 etags 对 javascript 代码进行补全

## ENV ##

https://v.youku.com/v_show/id_XMTQwNTg3MDY4NA==.html 有提到使用 使用 company-etags 对 javascript 进行补全, 但是没有给出怎么配置.

https://emacs-china.org/t/topic/784

os: ubuntu16

## 生成 etags ##

在视频中, 使用的是 macOS, 所以, 直接使用

`ctags -eR .` 会报错,我们要知道 参数的含义

-e : 生成 emacs 能识别的 tags 
-R : 递归文件夹

因为,我们现在是 ubuntu16 , 所以对应的命令,应该是:




## 网站 ##

https://github.com/emacs-china/Spacemacs-rocks/issues/20







