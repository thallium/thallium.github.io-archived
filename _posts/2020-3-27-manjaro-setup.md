---
published: true
title: Manjaro 折腾记录
category: Linux
tags: 
- Linux
layout: post
---
随缘更新，想到啥就记啥
<!-- more -->
## 配置

### 触摸板

一开始发现触摸板右键和左键效果是一样的，双指轻按还是中键……

解决方法：

```shell
/etc/X11/xorg.conf.d/30-touchpad.conf
---
Section "InputClass"
    Identifier "touchpad"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "libinput"
    Option "Tapping" "on"
    Option "ButtonMapping" "1 3 2"
    Option "TappingButtonMap" "lmr"
EndSection

```

### 映射caps+hjkl为方向键

```shell
~/.Xmodmap
---
clear lock
add mod3 = Caps_Lock
keycode  43 = h H Left H
keycode  44 = j J Down J
keycode  45 = k K Up K
keycode  46 = l L Right L
keycode  66 = Mode_switch
```

Then update xmodmap:

```shell
xmodmap ~/.Xmodmap
```

已知bug：

xmodmap有时候会失效，重新运行指令即可。

## 软件

### vim配置

待更新

### fcitx码表

待更新

### Autojump

快速跳转文件夹，再也不用长长的cd了～

#### 安装

```shell
yay autojump
```

#### Source the correct autojump file

```shell
echo "/usr/share/autojump/autojump.bash" >> ~/.bashrc
chmod 755 /usr/share/autojump/autojump.bash
source ~/.bashrc
```

#### 注意事项

快速跳转的文件夹需要正常访问一次。

## 问题解决

### 修改`/etc/profile`导致循环登录

2020.03.27

一般的解决方法是从命令行登录然后恢复之前的修改，但我从命令行也是循环登录……于是想到能不能从windows修改然后发现有个软件叫linux file system for windows，然后问题就解决了。真的太不容易了，心态差点崩了……
