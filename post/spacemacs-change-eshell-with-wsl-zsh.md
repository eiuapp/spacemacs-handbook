
在 windows 用 wsl 中的 zsh 替换 eshell

## env

- host:
    - os: windows10
	- spacemacs: 26.1
- wsl:
	- zsh
	
## step

在 C:/Users/a/.spacemacs.d/init.el 中

```
   dotspacemacs-configuration-layers
   '(
     (shell :variables shell-default-shell 'eshell)
     ;; (shell :variables
     ;;        shell-default-shell 'ansi-term
     ;;        shell-default-term-shell "C:/Windows/System32/bash.exe"
     ;;        shell-default-height 30
     ;;        shell-default-position 'bottom)

     ;; (setq-default explicit-shell-file-name "c:/Windows/System32/bash.exe")
     ;; (shell :variables  shell-default-term-shell "c:/Windows/System32/bash.exe"
     ;;         shell-default-shell "c:/Windows/System32/bash.exe")
     ;; (setq explicit-shell-file-name "/bin/bash")
     ;; (setq shell-file-name (executable-find "bash.exe"))
     ;; (setq shell-file-name (executable-find "bash.exe"))
```