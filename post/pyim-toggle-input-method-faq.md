
pyim 的相关报错

## env

### 安装 ###

- https://github.com/eiuapp/spacemacs-private-win10-tl/commit/768b96e8a535f9eb5c703d0af3825257dc5460a1

参考

- https://github.com/tumashu/pyim

## error

### "Odd number of elements in hash table data"

https://github.com/tumashu/pyim/issues/182


删除~/.emacs.d/pyim/dcache后可以解决

因为, 我这里, 包存放的地圵是 ~/spacemacs/ 中, 所以,

`rm -rf ~/spacemacs/pyim/dcache/` 

