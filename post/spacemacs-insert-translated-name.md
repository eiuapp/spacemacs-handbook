spacemacs 使用 翻译插件 insert-translated-name 

## env

env-wsl

## url

https://manateelazycat.github.io/emacs/2018/12/01/emacs-study-english.html

https://github.com/manateelazycat/insert-translated-name

## step

我的操作

https://github.com/eiuapp/spacemacs-private-wsl-tl/commit/0f37fd4ebd82943778c63ab51e42c9641f9435ce

## command 

https://github.com/manateelazycat/insert-translated-name#%E4%BD%BF%E7%94%A8


- | insert-translated-name-replace                     | 按照当前语言风格自动替换中文为翻译后的名字 |
- | insert-translated-name-insert                      | 按照当前语言风格自动插入翻译后的名字       |

## 修改 默认间隔符号

修改 insert-translated-name.el 文件

```bash
-(defvar insert-translated-name-default-style "underline"
+(defvar insert-translated-name-default-style "origin"
   "The default translation style, which can be set to \"origin\", \"line\", \"camel\" or \"underline\".")
```

## 来自官网

### 安装

1.  下载 [insert-translated-name](https://github.com/manateelazycat/insert-translated-name) 里面的 insert-translated-name.el 放到 ~/elisp 目录
2.  把下面的配置加入到 ~/.emacs 中
```
(add-to-list 'load-path (expand-file-name "~/elisp"))
(require 'insert-translated-name)
```

### 使用

| 命令                                               | 描述                                       |
| :--------                                          | :----                                      |
| insert-translated-name-insert                      | 按照当前语言风格自动插入翻译后的名字       |
| insert-translated-name-insert-with-underline       | 按照下划线风格自动插入翻译后的名字         |
| insert-translated-name-insert-with-camel           | 按照骆驼风格自动插入翻译后的名字           |
| insert-translated-name-insert-with-line            | 按照连接线风格自动插入翻译后的名字         |
| insert-translated-name-insert-original-translation | 按照当前语言风格自动插入翻译               |
| insert-translated-name-replace                     | 按照当前语言风格自动替换中文为翻译后的名字 |
| insert-translated-name-replace-with-underline      | 按照下划线风格自动替换中文为翻译后的名字   |
| insert-translated-name-replace-with-camel          | 按照骆驼风格自动替换中文为翻译后的名字     |
| insert-translated-name-replace-with-line           | 按照连接线风格自动替换中文为翻译后的名字   |

`insert-translated-name-insert` 命令会根据当前的环境来自动切换不同的翻译风格， 如果匹配下面的规则， 则直接使用返回的翻译结果：

1. 当前模式如果设置了变量 ```insert-translated-name-original-translation``` （由函数 insert-translated-name-use-original-translation 设置）
2. 在字符串或者注释中
3. 在magit commit buffer 中
4. 在minibuffer中

当然，你也可以在调用命令 ```insert-translated-name-insert``` 之前按一下 C-u 也是可以的。

下面是各种语言预定的风格, 如果你不喜欢默认风格, 可以定制以下变量的内容:

```
(defvar insert-translated-name-origin-style-mode-list
  '(text-mode))

(defvar insert-translated-name-line-style-mode-list
  '(web-mode emacs-lisp-mode))

(defvar insert-translated-name-camel-style-mode-list
  '(js-mode))

(defvar insert-translated-name-underline-style-mode-list
  '(ruby-mode))
```

### 自定义

#### 翻译引擎
默认使用 google.cn 翻译(不需要梯子), 如果你更喜欢有道, 修改 ```insert-translated-name-translate-engine``` 的值为 "youdao" 即可.
Google 的长句翻译更加准确一点.

自己拯救自己的英语, 哒哒.

#### 添加英文模式
如果你想在其它模式激活 ```insert-translated-name-insert``` 的时候自动使用英文翻译， 而不是变量名， 可以用下面的方式来支持：
```
(dolist (hook (list
               'atomic-chrome-edit-mode-hook
               ))
  (add-hook hook '(lambda () (insert-translated-name-use-original-translation))))
```


## FAQ(已解决)
## FAQ(未解决)

### insert-translated-name-insert 无法连续输入

每一次,都是输入一下`M-x insert-translated-name-insert`,然后,又需要重新输入 `M-x insert-translated-name-insert`, 这样明显太麻烦了.

### rcirc 插件自动翻译成英文

`好怀念十几年前, 我在Emacs中读中文, 我的一个 rcirc 插件自动翻译成英文和老外在IRC频道里神拽的年代.`

作者在 文章中提到的 rcirc 插件自动翻译成英文, 如何实现 

