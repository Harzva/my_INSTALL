
# 一、基础配置

1.安装指定版本的pyqt5，版本新点好。

`sudo pip install pyqt5`

2.安装pyqt5的依赖项

`sudo apt install pyqt5*`

3.安装qtdesigner


```
sudo apt install qt5-default qttools5-dev-tools

```

4.测试代码


```
# !/usr/bin/env python
from PyQt5.QtWidgets import (QApplication, QLabel)
import sys

if __name__ == "__main__":
app = QApplication(sys.argv)
label = QLabel("<center>Hello World with PyQt5!</center>")
label.resize(200, 50)
label.show()
sys.exit(app.exec_())
```
# 二、技巧教程

```




```


## 错误
运行后显示：Hello World with PyQt5! 的弹窗

> > qt.qpa.xcb: could not connect to display 
> > qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
> > This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.
> > 
> > Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, webgl, xcb.

远程开发VsCode终端中运行PyQt5程序报错qt.qpa.xcb: could not connect to display，原因是vscode没有办法显示远程的图。
通过 mobaxterm，Xshell中转

不确定是否全部导入是否会导致最后编译为可执行文件时会增加大小。后续要确认一下。
```
from PyQt5.QtWidgets import * 	# QAction,QFileDialog
from PyQt5.QtGui import *       # QIcon,QPixmap
from PyQt5.QtCore import *      # QSize
```



```
1.修改配置文件：

sudo gedit ~/.bashrc

2.在最末尾添加如下语句并保存，在运行测试用例的时候会列出详细的错误提示：

export QT_DEBUG_PLUGINS=1
```
