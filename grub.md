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

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset"
GRUB_CMDLINE_LINUX=""

```
有grub,并且正常进入
```
GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
```
