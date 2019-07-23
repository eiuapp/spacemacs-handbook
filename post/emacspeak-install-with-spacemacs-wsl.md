---
title: "emacspeak install with spacemacs ubuntu wsl"
date: 2018-08-28T23:53:02+08:00
draft: false
tags: ["spacemacs"]
categories: ["spacemacs"]
subtitle: "安装emacspeak(基于spacemacs, ubuntu, wsl)"
descriptions: ""
bigimg:
---

在 macos 成功搭建 emacspeak 的基础上, 实现 wsl + ubuntu + spacemacs 中搭建

## env ##

- https://www.emacswiki.org/emacs/EmacSpeak

## step ##

### 通过源码安装 ###

尝试 http://tvraman.github.io/emacspeak/manual/Quick-Installation.html#Quick-Installation

#### 下载源码 ####

```
git clone https://github.com/tvraman/emacspeak 
```

#### 编译 ####

```
cd emacspeak
make config
make
```

### text-to-speech engine ###
#### Open Source ESpeak on Linux ####

原理：使用开源的 espeak .

http://espeak.sourceforge.net/
https://itsfoss.com/espeak-text-speech-linux/
https://en.wikipedia.org/wiki/ESpeak

##### install espeak #####

```
sudo apt-get install espeak
```

##### use espeak #####

输入"hello world", 并没有发出声音来，且报错如下


```
DESKTOP-APB1HCJ% espeak
hello world
Assertion 'pthread_mutex_unlock(&m->mutex) == 0' failed at pulsecore/mutex-posix.c:108, function pa_mutex_unlock(). Aborting.
[1]    18180 abort (core dumped)  espeak
DESKTOP-APB1HCJ%
```

##### 展望 #####

微软最初发布 WSL 的时候就明确表示这是一个只针对开发者的平台, 所以, 可能并没有支持桌面应用的计划，导致，在这上面播放声音，有点免为其难了。

等待以后的版本吧。

更多可参考：

- [在 WSL 中使用 pulseaudio 播放声音](http://martincl2.me/archives/916)


##### try #####

`cd servers/native-espeak; make` 报错如下:

```
DESKTOP-APB1HCJ% cd servers/native-espeak && make
g++ -g    -O2 -fPIC  -DPIC  -pedantic -ansi -Wall -Wno-long-long -I/usr/include/tcl8.6   -c -o tclespeak.o tclespeak.cpp
tclespeak.cpp:41:33: fatal error: espeak-ng/speak_lib.h: No such file or directory
compilation terminated.
<builtin>: recipe for target 'tclespeak.o' failed
make: *** [tclespeak.o] Error 1
DESKTOP-APB1HCJ%
```

不知道怎么继续下去, 先放弃.

#### ViaVoice Outloud ####

https://tvraman.github.io/emacspeak/manual/Quick-Installation.html#Quick-Installation

只能尝试使用 `ViaVoice Outloud` 的方式了.

https://voxin.oralux.net/

https://soft.oralux.net/emacspeak/emacspeak_voxin_install/

https://github.com/Oralux/emacspeak_voxin_install/releases

下载 49.0-6 版本, 回到这个项目的首页

https://github.com/Oralux/emacspeak_voxin_install

看了一下,好像,是我要的.

`./install.sh` 提示,要先去安装依赖包 `sudo ./bin/installDep.sh` , 然后, 又回来执行 `./install.sh`

发现,会重新下载`emacspeak-49.0.tar.bz2`, 并自动安装. 

安装过程最后的输出如下:

```
make[1]: Leaving directory '/mnt/c/Users/a/emacs/emacspeak-src/emacspeak_voxin_install-49.0-6/build/emacspeak-49.0/servers/linux-espeak'                      
~/emacs/emacspeak-src/emacspeak_voxin_install-49.0-6                                                                                                          
                                                                                                                                                              
# Configuration                                                                                                                                               
# To add user u to the audio group, type as superuser:                                                                                                        
usermod -aG audio u                                                                                                                                           
# Add these lines to the top of your emacs init file (e.g. in  ~/.emacs )                                                                                     
(load-file "/mnt/c/Users/a/emacs/emacspeak-src/emacspeak_voxin_install-49.0-6/build/emacspeak-49.0/lisp/emacspeak-setup.el")                                  
# Now you may want to reboot your system, before launching emacs                                                                                              
# These instructions are copied at the end of log/install.*                                                                                                   
DESKTOP-APB1HCJ%                                                                                                                                              
```

就按提示做一下

```
DESKTOP-APB1HCJ% sudo usermod -aG audio u
```







### (可过)通过 emacswiki-EmacSpeak 安装 ###

https://www.emacswiki.org/emacs/EmacSpeak

#### ubuntu 安装 emacspeak ####

https://www.howtoinstall.co/en/ubuntu/trusty/emacspeak

apt-get install tclx8.3 tclx8.3-dev


```
sudo apt-get update
sudo apt-get install emacspeak
```

然后,会让你选择,我是选择 `espeak` , `none` 

http://emacspeak.sourceforge.net/install-guide/index.html

```
sudo apt-get install tcl
```

发现, tcl 已经安装过了.

google searching for “Download the ViaVoice TTS SDK and TTS Run Time Kit for Linux” 

http://emacspeak.sourceforge.net/install-guide/appendixb.html

这个时候, 感觉, 这条路,还是行不通呀. 还是回官方文档吧.

