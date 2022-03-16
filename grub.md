```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden  #zhushi hou xianshi yindan grub
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT="text" xianshi  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
GRUB_CMDLINE_LINUX=""
```
````
有可能是因为系统独立显卡的启动导致黑屏，这时如果在quiet splash之后，加上nomodeset，就可以告诉内核，系统启动过程中，暂时不运行图像驱动程序，过程如下：
（1）

sudo vim /etc/default/grub


（2）splash后加上nomodeset

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodest"
GRUB_CMDLINE_LINUX=""


（3）:wq保存后

sudo update-grub


（1）（2）（3）的作用是系统正常启动之后，为了防止黑屏，永久生效的解决办法

如果无法进入系统，那么，开机之后，按下’e’键盘，找到quiet splash，其后加上nomodeset，然后ctrl+x，就可以重新启动，但这只能暂时解决黑屏的问题
2.quiet

quiet参数的作用：启动系统的过程中，如果没有quiet，那么内核就会输出很多内核消息，这些内核消息就包括的了系统启动过程中运行了哪些程序，如果系统运行正常，那么就不必要看到这些消息，所以就加上quiet
3.splash

splash是一个不可或缺的参数，系统很多核心程序，都需要这个参数，且这个参数与可视化界面有关，没有就可能导致屏幕一片空白
4.GRUB_CMDLINE_LINUX和GRUB_CMDLINE_LINUX_DEFAULT

区别：
GRUB_CMDLINE_LINUX：一直生效
GRUB_CMDLINE_LINUX_DEFAULT：仅引导过程中生效

也就是说，一般linux系统启动后，内核先走GRUB_CMDLINE_LINUX
然后走GRUB_CMDLINE_LINUX_DEFAULT，
而如果是恢复模式recovery mode，只会生效GRUB_CMDLINE_LINUX

GRUB_CMDLINE_LINUX="acpi_backlight=vendor"


参数acpi_backlight=vendor，选择背景亮度为vendor型，可以用Fn调亮度
试过，但没成功

补充：1中解决黑屏的方法，不知为什么，有时候可以，有时候不行，后来把
quiet删掉之后，好像效果更好，有的时候，启动项时按’e‘，然后ctrl+x,就不能正常进入系统，启动项时按’e‘，然后按Esc，就可以进入系统，很玄学
亲测很玄学
这中能进吗 但是没有grub,能进,问题不大,分辨率可能会出问题
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
同上,没有grub高级选项,去掉nomodeset,最终分辨率是正确的因为加载了视频驱动程序
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
同上,没有grub高级选项,去掉nomodeset,splash 无非是多显示了些开机信息
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""
```
同上,去掉nomodeset,splash,quiet开机不在正常,紫屏,但是有grub高级选项可以手动进入仍然是默认引导,不用改采用玄学方式e+esc就可以进入
```
GRUB_CMDLINE_LINUX_DEFAULT=""

```
同上,只有splash??理论上是 无高级选项但开机正常无需玄学手动操作如果满足就停止  符合理论 不在进行grub实验 恶心了
``
GRUB_CMDLINE_LINUX_DEFAULT="splash"

```
```
有grub 不可以正常进入 grub高级引导显示和quiet splash不可兼得 尽管加上nomodeset
```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
```

有grub 可以正常进入 并且显示详细开机信息 应该和去掉quiet有关 ----------最终版本
```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""
```

quiet意思是内核启动时候简化提示信息
splash意思是启动的时候使用图形化的进度条代替init的字符输出过程

永久启动进入命令行,非图形用户界面
```
如果你想要永久启动进入命令行，你需要更新定义了内核启动参数GRUB设置。

在文本编辑器中打开默认的GRUB配置文件。

代码如下:

$ sudo vi /etc/default/grub

查找以GRUB_CMDLINE_LINUX_DEFAULT开头的行，并用“#”注释这行。这会禁止初始屏幕，而启动详细模式（也就是说显示详细的的启动过程）。

更改GRUBCMDLINELINUX="" 成：

代码如下:

GRUB_CMDLINE_LINUX="text"

接下来取消“#GRUB_TERMINAL=console”的注释。

```
```
来自`nomodeset`是做什么的，关于nomodeset：

    最新的内核已将视频模式设置移入内核。因此，在X服务器启动时，所有针对硬件的时钟速率和视频卡上寄存器的编程都在内核中进行，
    而不是在X驱动器中进行。.这样就可以拥有高分辨率的漂亮的启动（启动）屏幕和闪烁从启动启动画面到登录屏幕的免费过渡。
    不幸的是，在某些卡上这不能正常工作，并且最终出现黑屏。添加nomodeset参数指示内核在加载X之前不加载视频驱动程序，而改用BIOS模式。
来自Unix & Linux，关于quiet splash：

    闪屏（最终会在您的/boot/grub/grub.cfg中结束）将显示闪屏。 同时，您希望引导过程安静一些，否则所有类型的消息都会破坏启动屏幕。 尽管在GRUB中指定了这些参数，但是它们是影响内核或其模块加载的内核参数，而不是改变GRUB行为的参数。来自GRUB_CMDLINE_LINUX_DEFAULT的重要部分是CMDLINE_LINUX

```

1. sudo gedit /etc/default/grub

将代码:GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

改为： GRUB_CMDLINE_LINUX_DEFAULT="text"

然后sudo update-grub

2. sudo gedit /etc/default/grub

设置:GRUB_CMDLINE_LINUX="text"

然后sudo update-grub 1启动时没有splash闪过，2

有命令行模式下需要返回图形模式，输入命令： startx反过来，图形模式下返回命令行模式，在终端按ctrl+alt+F1