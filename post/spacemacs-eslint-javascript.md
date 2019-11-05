(未完成)
在 spacemacs 中使用 eslint 对 javascript 代码进行检查

## ENV ##

- os: ubuntu16

## step

主要参考：

- https://after.dev/emacs-flycheck-eslint-incorrect-config/ 及其 参考url

### 配置 spacemacs

- https://github.com/eiuapp/spacemacs-private/commit/ed2a78a1e33a5512907b2b355429e7cdc5c2dd99

### 配置 eslint 环境

本地主机

```
npm i babel-eslint eslint-config-egg eslint-plugin-eggache eslint-plugin-jsdoc -g
```

修改本机的 ~/.eslintrc 文件

```JSON
{
  "extends": ["eslint-config-egg"],
  "parserOptions": {
    "ecmaVersion": 6,
    "ecmaFeatures": {
      "experimentalObjectRestSpread": true
    }
  },
  "parser": "babel-eslint",
  "rules": {
    "array-bracket-spacing": 0
  }
}
```

### 代码放在本地主机

`M-x flycheck-verify-checker javascript-eslint` 显示

```
Syntax checker in buffer app.js<src> in js2-mode:

  javascript-eslint
    - major mode:  `js2-mode' supported
    - may enable:  yes
    - executable:  Found at /mnt/c/Users/a/Desktop/tianluo/fangyuan/src/fangyuan-server/node_modules/.bin/eslint
    - config file: found

Flycheck can use this syntax checker for this buffer.

Flycheck Mode is enabled. Use SPC u C-c ! x to enable disabled checkers.

--------------------

Flycheck version: 32snapshot (package: 20190411.1707)
Emacs version:    26.1
System:           x86_64-pc-linux-gnu
Window system:    x
```

`M-x flycheck-verify-setup` 显示

```
Syntax checkers for buffer app.js<src> in js2-mode:

  javascript-eslint
    - may enable:  yes
    - executable:  Found at /mnt/c/Users/a/Desktop/tianluo/fangyuan/src/fangyuan-server/node_modules/.bin/eslint
    - config file: found

  javascript-jshint (disabled)
    - may enable:         yes
    - executable:         Found at /mnt/c/Users/a/.nvm/versions/node/v11.14.0/bin/jshint
    - configuration file: Not found

  javascript-standard
    - may enable: yes
    - executable: Found at /mnt/c/Users/a/.nvm/versions/node/v11.14.0/bin/standard

Flycheck Mode is enabled. Use SPC u C-c ! x to enable disabled checkers.

--------------------

Flycheck version: 32snapshot (package: 20190411.1707)
Emacs version:    26.1
System:           x86_64-pc-linux-gnu
Window system:    x

[back]
```

说明，正在使用 eslint 检查代码了。耶耶耶~

经验：

```
    - may enable:  yes
    - executable:  Found at /mnt/c/Users/a/.nvm/versions/node/v11.14.0/bin/eslint
    - config file: found
```

- `- major mode:  `与  `(flycheck-add-mode 'javascript-eslint 'js2-mode)` 这样的配置相关
- `- may enable:  `与  `(flycheck-add-mode 'javascript-eslint 'js2-mode)` 这样的配置相关
- `- executable:  `与  `(add-hook 'flycheck-mode-hook #'my/use-eslint-from-node-modules)` 这样的配置相关
- `- configuration file: ` 与  本机或本地的 `.eslintrc` 文件相关

然后，在配置前，一定要保证 `eslint --print-config .` 运行正确。

## （可跳过）下面是之前的研究过程 ##

### 网站 ###

#### 官网 ####

https://github.com/eslint/eslint

https://github.com/flycheck/flycheck

https://github.com/syl20bnr/spacemacs/tree/master/layers/%2Blang/javascript

#### flycheck ####

http://www.flycheck.org/en/latest/languages.html#javascript

#### 成功经验 ####

http://andrwj.com/blog/2018/11/spacemacs%EC%97%90%EC%84%9C-nodejs-express-vuejs-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-prettier-es6-lint-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0/ 这个是写得比较全的, 最与我们的情况接近

http://codewinds.com/blog/2015-04-02-emacs-flycheck-eslint-jsx.html  这个是写得比较全的,但是,比较老了,且是 emacs 下的,我玩不来


#### 相似情况 ####

https://github.com/syl20bnr/spacemacs/issues/10562

https://github.com/syl20bnr/spacemacs/issues/5792

https://github.com/syl20bnr/spacemacs/issues/10131

https://github.com/flycheck/flycheck/issues/1087

https://stackoverflow.com/questions/40735669/how-where-i-can-set-eslint-config-file-in-spacemacs

#### 其它思路 ####

https://gist.github.com/rstacruz/a2361d000a88e49472c4419116edaccf


### spacemacs rocks season 1 ###

在第一季的视频中有提到的信息是:

#### Syntax check {#syntax-check} ####

1.  flycheck with jshint / eslint
2.  js2-mode checking


##### 开启语法检查 {#开启语法检查} #####

> SPC t S

在 ubuntu 下,会发现失效了. 怎么办?



##### 查看语法错误信息 {#查看语法错误信息} #####

> SPC e l

在 ubuntu 下,会发现失效了. 怎么办?











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



### 学习 韩国 ###

http://andrwj.com/blog/2018/11/spacemacs%EC%97%90%EC%84%9C-nodejs-express-vuejs-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-prettier-es6-lint-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0/ 这个是写得比较全的, 最与我们的情况接近
