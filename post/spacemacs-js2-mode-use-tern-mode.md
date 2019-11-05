
在 spacemacs 中使用 tern 对 javascript 代码进行补全

## ENV

https://v.youku.com/v_show/id_XMTQwNTg3MDY4NA==.html 有提到使用 使用 company-tern 对 javascript 进行补全, 但是没有给出怎么配置.

## 网站 ##

找到官网

tern 

https://github.com/ternjs/tern

http://ternjs.net/doc/manual.html#emacs

对应与 spacemacs

https://github.com/syl20bnr/spacemacs/tree/master/layers/%2Blang/javascript#install

对应的 blog 

https://qiita.com/sune2/items/e54bb5db129ae73d004b

https://emacs.cafe/emacs/javascript/setup/2017/05/09/emacs-setup-javascript-2.html

https://simpletutorials.com/c/2784/How+to+setup+JavaScript+auto-complete+in+Spacemacs+on+Windows

其它

https://github.com/proofit404/company-tern


类似情况

https://www.reddit.com/r/emacs/comments/aejg0o/eldoc_and_companytern_are_not_working_properly_in/

https://emacs-china.org/t/emacs-js-dom/2858/13

https://emacs-china.org/t/spacemace-comyany-mode-tern/2223/7

https://emacs-china.org/t/topic/2247

## debug tern 是否生效的检查过程. ##

https://emacs-china.org/t/spacemacs-js/2731/6

```bash
如果跟着文档走了一遍还不行，就要自己诊断。可以从以下几个地方入手：

tern 服务有没有运行(ps, pgrep 等终端命令)
手动能不能启动 (M-x tern-mode)
手动调用 tern 的函数是否可行
*Messages* 有没有出错信息
…
这是我解决问题经常使用的方法（或者说习惯）。

tern 的问题排除之后再看 company-backends, 逐步缩小范围。我不用 Spacemacs，也不能给一段代码直接就能运行。
```

https://emacs-china.org/t/emacs-js-dom/2858/13

```bash
tern 是否启动？

在终端 ps aux | grep tern 看看是否有 tern 的进程。

tern 启动之后会在项目目录下创建一个 .tern-port 文件，里边的端口跟 M-x describe-variabble tern-known-port 看到的一致。

tern-mode 是否启用？

M-x describe-variabel tern-mode 结果应该是 t。

company-tern 是否安装？

手动调用 M-x company-tern 应该会出现补全菜单。如果手动能补全，就是 company 设置不对了。
```


## 手动安装并调用 ##


M-x package-install RTN company-tern RTN

启动 

M-x tern-mode

当前buffer生效

M-x company-tern 


这样下来,能生效,说明是可以使用的啦.但是,如何让它们自动生效呢?

## 自动在javascript js2-mode的company-mode 中生效


## 安装 company-tern 

怎么老是被认为是 Orphan package, 被自动删除的问题

http://develop.spacemacs.org/doc/FAQ.html#why-are-packages-installed-with-package-install-automatically-deleted-by-spacemacs-when-it-boots

或者

https://emacs-china.org/t/orphan-package-solarzed/859/3

把 ~/.spacemacs.d/init.el 中的

```
dotspacemacs-delete-orphan-packages nil))
```

后面再看一下,怎么处理.

怎么还不行? 还是会自动删除.

妈妈的呀.原来是在 `dotspacemacs-excluded-packages` 里面有 `company-tern` 呀,我了个去.

还有,  官网的第3种方法, ` set the variable dotspacemacs-install-packages to used-but-keep-unused` 
虽然, 不删除这个package, 但是, 重启spacemacs后,你也用不了这个package, 所以,这种方法, 最好别用.

## auto-complete-mode is not enabled ##


每一次,在 fs 后输 . 号,应该会出现补全菜单,但是,没有, *message* 里提示是

auto-complete-mode is not enabled

这个怎么办?

https://stackoverflow.com/questions/8095715/emacs-auto-complete-mode-at-startup

(defun dotspacemacs/user-config () 下加入
```
  (require 'auto-complete)
  (global-auto-complete-mode t)
```
确实是生效了.但是,会不会影响其它的mode的体验呀?哈哈,不管了,先用着吧.



## 修改

https://simpletutorials.com/c/2799/How%20to%20resolve%20%26quot%3BUndeclared%20variable%20or%20function%20%26%23x27%3Bmodule%26%23x27%3B%26quot%3B%20error%20thrown%20by%20Tern%20in%20Spacemacs

If you've setup Tern for Spacemacs, and you're seeing the following error:

```
Undeclared variable or function 'module'
```

add the following line to the user-init section of your .spacemacs file:

```
(setq js2-include-node-externs t)
```



