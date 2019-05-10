spacemacs 使用 company-english-helper

## env

env-wsl

## url

https://www.jianshu.com/p/8390dcb7f3e6

https://github.com/manateelazycat/company-english-helper

## step

我的操作

https://github.com/eiuapp/spacemacs-private-wsl-tl/commit/3f4cda9f54d872f78d220ab004ae2f81adda5100

## command 

执行命令 `toggle-company-english-helper' , 就可以在Emacs中飞速的编写英文文档了.

## 自定义词典

默认的词典是从 stardict KDict 这个词典转换出来的, 包括11万单词.

如果你不喜欢默认的词库, 可以用我写的 stardict 词典转换库 [stardict.py](https://raw.githubusercontent.com/manateelazycat/company-english-helper/master/stardict.py) 来转换你喜欢的 stardict 词典.

```bash
python ./stardict.py stardict-kdic-ec-11w-2.4.2/kdic-ec-11w.ifo
```

把 stardict-kdic-ec-11w-2.4.2/kdic-ec-11w.ifo 替换成你喜欢的 stardict 字典, 命令执行完成后, 会自动生成新的 company-english-helper-data.el 文件


