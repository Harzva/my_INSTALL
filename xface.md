## 1.安装谷歌浏览器

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

sudo dpkg -i google-chrome-stable_current_amd64.deb
```

#若提示缺失包，先安装缺失包再运行该命令 
## 2.安装中文输入法
`sudo apt install ibus-libpinyin`
#安装完后可能需要重启一下电脑，另外需要自行打开ibus
#左上角点击application，点击settings，点击iBus Preferences

## 3.桌面美化
https://connectwww.com/how-to-install-macos-theme-on-your-linux-xfce-desktop/61588/

## 4.如果安装tim等软件会出现乱码，可以安装一下中文环境
sudo apt update && sudo apt install language-pack-zh-hans

修改配置文件：
`sudo vim /etc/default/locale`
#替换成如下内容

```
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh"
LC_NUMERIC="zh_CN"
LC_TIME="zh_CN"
LC_MONETARY="zh_CN"
LC_PAPER="zh_CN"
LC_NAME="zh_CN"
LC_ADDRESS="zh_CN"
LC_TELEPHONE="zh_CN"
LC_MEASUREMENT="zh_CN"
LC_IDENTIFICATION="zh_CN"
LC_ALL="zh_CN.UTF-8"
```


修改环境文件:
vim /etc/environment
不修改原有内容！！！直接在原内容下面新开一行加入下列内容：
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh"
LC_NUMERIC="zh_CN"
LC_TIME="zh_CN"
LC_MONETARY="zh_CN"
LC_PAPER="zh_CN"
LC_NAME="zh_CN"
LC_ADDRESS="zh_CN"
LC_TELEPHONE="zh_CN"
LC_MEASUREMENT="zh_CN"
LC_IDENTIFICATION="zh_CN"
LC_ALL="zh_CN.UTF-8"


## 5.不小心添加了三方源：

 在Ubuntu下软件源的文件是/etc/apt/sources.list，那么sourdces.list.d目录下的文件又是什么作用呢？
 该文件夹下的文件是第三方软件的源，可以分别存放不同的第三源地址，只需“扩展名”为list即可

所以可以去/etc/apt/sources.list.d目录下把不想保留的第三方源的文件给删除就行了

## 6.给WSL2终端和git配置代理





### 一.在 Windows主机内通过 Clash开启代理，并允许通过LAN连接

### 二.假设 Windows 上的 Clash 已允许 LAN 连接，监听在7890端口，
SOCKS5 代理监听在 1080端口:
[运行sudo vim ~/.bashrc添加以下内容到 ~/.bashrc]

#获取 Windows 主机 ip
export hostip=$(cat /etc/resolv.conf |grep -oP '(?<=nameserver\ ).*')
#配置终端代理
export https_proxy="http://${hostip}:7890
export http_proxy="http://${hostip}:7890"
export all_proxy="socks5://${hostip}:1080"


### 三.git代理配置

在终端运行cat /etc/resolv.conf |grep -oP '(?<=nameserver\ ).*'
#获取 Windows 主机 ip

将下面内容中的${hostip}替换成输出结果(获取到的windows主机ip)
运行sudo vim ~/.gitconfig将替换后的内容添加到.gitconfig


#需要将${hostip}替换成获取到的windows主机ip
[https]
    proxy = http://${hostip}:7890
[http]
    proxy = http://${hostip}:7890

