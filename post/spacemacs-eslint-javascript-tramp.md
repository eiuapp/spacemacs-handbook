(未成功)
在 spacemacs 中使用 eslint 对 远程主机的 javascript 代码（tramp）进行检查

## ENV ##

- 本地os: ubuntu16
- 远程os: ubuntu16

## （不成功）代码放在远程主机

远程主机

```
npm i babel-eslint eslint-config-egg eslint-plugin-eggache eslint-plugin-jsdoc -g
./node_modules/eslint/bin/eslint.js --print-config .
eslint --print-config .
```



`M-x flycheck-verify-setup` 显示

```
Syntax checkers for buffer app.js in js2-mode:

  javascript-eslint (disabled)
    - may enable:  yes
    - executable:  Found at /mnt/c/Users/a/.nvm/versions/node/v11.14.0/bin/eslint
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

在 *message* 中可看到类似这样的输出：

```
Tramp: Inserting ‘/ssh:ubuntu@192.168.168.137#2222:/home/ubuntu/code-server/fangyuan/fangyuan-server/app.js’...failed
error in process sentinel: tramp-file-name-handler: Couldn’t find exit status of ‘test -e /home/ubuntu/code-server/fangyuan/fangyuan-server/app.js/\(\(\"\‘/home/ubuntu/code-server/fangyuan/fangyuan-server/app.js\’\"\)\ 1\ 1000e0\ 1000e0\ 1572944327e0\ 1572944327e0\ 1572944327e0\ 586e0\ \"-rwxrwxrwx\"\ t\ 20998454e0\ -1\)’
error in process sentinel: Couldn’t find exit status of ‘test -e /home/ubuntu/code-server/fangyuan/fangyuan-server/app.js/\(\(\"\‘/home/ubuntu/code-server/fangyuan/fangyuan-server/app.js\’\"\)\ 1\ 1000e0\ 1000e0\ 1572944327e0\ 1572944327e0\ 1572944327e0\ 586e0\ \"-rwxrwxrwx\"\ t\ 20998454e0\ -1\)’
Type "q" to restore previous buffer. [2 times]

```

感觉上是，`eslint --print-config .` 在 tramp 后成功了，但是，为什么，还是 disabled 状态呢？
