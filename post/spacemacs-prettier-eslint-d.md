(未完成)
在 spacemacs 中使用 prettier-eslint-d 对 javascript 代码进行检查

## ENV ##


- os: ubuntu16

## 网站 ##

### 官网 ###

https://yarnpkg.com/en/package/prettier-eslint_d

### 成功 ###

https://gist.github.com/rstacruz/a2361d000a88e49472c4419116edaccf


## 安装 yarn ##


# Add prettier-eslint_d:
yarn add --dev prettier-eslint_d

这一步,就报错.而且一查,好像很多这样的情况.

```bash
DESKTOP-APB1HCJ% yarn add --dev prettier-eslint_d
yarn add v1.15.2
info No lockfile found.
warning package-lock.json found. Your project contains lock files generated by tools other than Yarn. It is advised not to mix package managers in order to avoid resolution inconsistencies caused by unsynchronized lock files. To clear this warning, remove package-lock.json.
[1/4] Resolving packages...
warning prettier-eslint_d > prettier_d@5.7.4: prettier_d now uses latest Prettier without extra features, install from github: https://github.com/josephfrazier/prettier_d
warning prettier-eslint_d > eslint_d > eslint > file-entry-cache > flat-cache > circular-json@0.3.3: CircularJSON is in maintenance only, flatted is its successor.
[2/4] Fetching packages...
[3/4] Linking dependencies...
error An unexpected error occurred: "ENOENT: no such file or directory, lstat '/mnt/c/Users/a/.cache/yarn/v4/npm-eslint-4.19.1-32d1d653e1d90408854bfb296f076ec7e186a300/node_modules/eslint/lib/rules/no-sparse-arrays.js'".
info If you think this is a bug, please open a bug report with the information provided in "/mnt/c/Users/a/Desktop/tianluo/lvchuang/src/lvchuang/Server/yarn-error.log".
info Visit https://yarnpkg.com/en/docs/cli/add for documentation about this command.
DESKTOP-APB1HCJ% ls /mnt/c/Users/a/.cache/yarn/v4/npm-eslint-4.19.1-32d1d653e1d90408854bfb296f076ec7e186a300/node_modules/eslint/lib/rules/no-sparse-arrays.js
/mnt/c/Users/a/.cache/yarn/v4/npm-eslint-4.19.1-32d1d653e1d90408854bfb296f076ec7e186a300/node_modules/eslint/lib/rules/no-sparse-arrays.js
DESKTOP-APB1HCJ%
```


https://github.com/yarnpkg/yarn/issues/1834
