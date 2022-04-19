

```

CANNOT LINK EXECUTABLE "curl": library "libssl.so.1.1" not found: needed by /data/data/com.termux/files/usr/lib/libcurl.so in namespace (default)

apt upgrade
```

termux-change-repo

termux-setup-storage
快捷方式 手机内容存放在storge上


```
apt install proot-distro
proot-distro list
proot-distro install ubuntu-20.04 
proot-distro login ubuntu-20.04
```

如果认为每次进入 ubuntu的命令太长，可以在 Termux 环境新建一个sh文件，比如新建u20.sh。


```
vim u20.sh
输入如下内容（就是esc键+i键）：
```


```

proot-distro login ubuntu-20.04
然后退出（esc键+:键，再输入wq，回车）
```


最后，在终端输入：

./u20.sh
就进入了真正的linux环境了。之后，传统操作比如换源，安装软件等等，一条龙走起来吧。

输入exit可以退出登录的linux系统：

exit
