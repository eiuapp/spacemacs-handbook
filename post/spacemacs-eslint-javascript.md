(未完成)
在 spacemacs 中使用 eslint 对 javascript 代码进行检查

## ENV ##


- os: ubuntu16

## 网站 ##

### 官网

https://github.com/eslint/eslint

https://github.com/flycheck/flycheck

https://github.com/syl20bnr/spacemacs/tree/master/layers/%2Blang/javascript

### flycheck

http://www.flycheck.org/en/latest/languages.html#javascript

### 成功经验

http://andrwj.com/blog/2018/11/spacemacs%EC%97%90%EC%84%9C-nodejs-express-vuejs-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-prettier-es6-lint-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0/ 这个是写得比较全的, 最与我们的情况接近

http://codewinds.com/blog/2015-04-02-emacs-flycheck-eslint-jsx.html  这个是写得比较全的,但是,比较老了,且是 emacs 下的,我玩不来


### 相似情况

https://github.com/syl20bnr/spacemacs/issues/10562

https://github.com/syl20bnr/spacemacs/issues/5792

https://github.com/syl20bnr/spacemacs/issues/10131

https://github.com/flycheck/flycheck/issues/1087

https://stackoverflow.com/questions/40735669/how-where-i-can-set-eslint-config-file-in-spacemacs

### 其它思路 ###

https://gist.github.com/rstacruz/a2361d000a88e49472c4419116edaccf


## spacemacs rocks season 1

在第一季的视频中有提到的信息是:

### Syntax check {#syntax-check} ###

1.  flycheck with jshint / eslint
2.  js2-mode checking


#### 开启语法检查 {#开启语法检查} ####

> SPC t S

在 ubuntu 下,会发现失效了. 怎么办?



#### 查看语法错误信息 {#查看语法错误信息} ####

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



## 学习 韩国

http://andrwj.com/blog/2018/11/spacemacs%EC%97%90%EC%84%9C-nodejs-express-vuejs-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-prettier-es6-lint-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0/ 这个是写得比较全的, 最与我们的情况接近

