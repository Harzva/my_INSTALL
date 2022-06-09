my_windows:
Step2 输入命令runas /users:管理员用户名 cmd

在目录：C:\Users\18452\AppData\Roaming\picgo>中进行操作

补充一点 如果安装缓慢 长时间卡住不动 去设置npm 的数据源为淘宝的。
```
1、命令 npm config set registry https://registry.npm.taobao.org
2、验证命令 npm config get registry 如果返回 https://registry.npm.taobao.org，说明镜像配置成功。
3、最后执行npm install picgo-plugin-gitee-uploader
```

Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux


https://blog.csdn.net/lunhui601/article/details/107722580

https://www.uud.me/site-notes/sharex-picgo-weibo.html



Ubuntu 20.04.4 LTS 报错解决方案
今天在安装WSL的时候连续报了几个错，这里记录以下解决方案。注意是20.04.4的版本。

\quad

WslRegisterDistribution failed with error: 0x8007019e
我遇到的第一个错如下：

```

Installing, this may take a few minutes...
Installation Failed!
Error: 0x8007019e
Press any key to continue...
```


出现这个error的原因是：未安装Windows子系统支持。

解决办法：

win+x，选择Windows PowerShell（管理员）
输入：Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
回车，输入Y，重启！
重新打开已经安装的子系统，等几分钟，输入账户和密码。
试了这个办法之后还是不行，新的错误出现了…

\quad

WslRegisterDistribution failed with error: 0x800701bc
继续排错，出现这个错误的原因是：wsl1升级到wsl2之后，内核却没有升级，所以会出现这种错误提示！

解决方法：

下载最新的wsl安装包，
安装包下载后，直接运行安装。
下载地址： [wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) 

安装之后发现还是不行，报了下面这个错…

\quad

WslRegisterDistribution failed with error: 0x80370102
继续排错，查到出现这个error的原因是：没有开启虚拟化。

解决方案：

控制面板->程序->启用或关闭windows功能，勾选虚拟机平台选项。
重启电脑



到这里，问题终于顺利的解决了！
https://blog.csdn.net/qq_37085158/article/details/125172803


2、WSL2 联网
安装好 Ubuntu 18.04 LTS，创建一个账号（PS：账号不能有大写字母），ping 百度失败后执行下面操作。

2.1 关闭防火墙
具体原因及其操作详见此链接。

2.2 在 Windows 用管理员运行以下代码
    netsh winsock reset 
    netsh int ip reset all
    netsh winhttp reset proxy
    ipconfig /flushdns