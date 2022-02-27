[Linux系统后台运行应用三板斧](https://mp.weixin.qq.com/s/B-ip7Fs25jckxQOFc7BXQg)

[Linux Screen技巧：记录屏幕日志](https://blog.csdn.net/lovemysea/article/details/78344114)

[linux screen打印日志](https://blog.csdn.net/yanggd1987/article/details/39082699)
[screen命令]tps://blog.csdn.net/zyc_love_study/article/details/79282064)
screen:
1.普通模式
```
[root@test #]$ apt-get install screen -y
#创建会话hello，此时会登入新会话
[root@test #]$ screen 或 screen -S hello

#分离会话，此时程序不会中断,键盘ctrl+a+d 分离会话 ctrl+a + ctrl+d
[detached from 28877.hello]

#列出所有会话
[root@test #]$ screen -ls
There is a screen on:
  28877.hello  (Detached)
  28876.test   (Dead)
1 Socket in /var/run/screen/S-root.
#恢复会话
[root@test #]$ screen -r 28877或 screen -r hello
#清除dead会话
[root@test #]$ screen -wipe
```
2.分离模式 
```
#创建处于分离模式的会话，启动后直接断开会话
[root@test #]$ screen -dmS test ./test.sh
#此时会话已断开，但是任务仍在运行，相当于把任务放在后台运行  nohub

screen -L -dmS test的意思是启动一个开始就处于断开模式的会话，会话的名称是test。
screen -r test连接该会话，在会话中的所有屏幕输出都会记录到screenlog.0文件。
没有VIM 之前-t 也不会报错，知识没用而已
```
3.输出日志 
```
vim 让每个screen会话窗口有单独的日志文件。

在screen配置文件/etc/screenrc最后添加下面一行：
sudo -i   
echo "logfile ./screen_log/screenlog_%t.log " >> /etc/screenrc
echo "logfile /root/screen_%t.log" >> /etc/screenrc
logfile /tmp/screenlog_%t.log
logfile ./screen_log/screenlog_%t.log 则是把日志文件记录到当前目录下。  不会自动创建screen_log
logfile ./screenlog_%t.log 则是把日志文件记录到当前目录下。
%t是指window窗口的名称，对应screen的-t参数。所以我们启动screen的时候要指定窗口的名称，例如：
screen -L -t window1 -dmS test的意思是启动test会话，test会话的窗口名称为window1。其中%t 为标题，如screen_test.log
screen -L -t name -S name ./name
第一个name是记录日志的名字，第二个name是screen -ls 列表展示出来的名字，第三个name是需要运行的程序。
#-L 打开日志输出
#-t 为标题
screen -S senthil -d -m
screen -dmS senthil 
#执行命令后，会在/root下生成screen_test.log
)screen -L -t test -dmS test bash ./test.sh  
)screen -L -t test -dmS test sh ./test.sh   运行结束或者报错，会自动terminating，同nohub一样会有延迟
)screen  -t tes2 -dmS test  sh ./test.sh  可以单独加-t ctrl+a H 后按照-t内容生成log文件
)screen -dmS test  $sh ./test.sh  可以不加 -L -t ctrl+a H 后按照-t内容生成log文件 ./test.sh前的$生成文件名字
)screen -dmS test  ./test.sh  ---失败，不会生成screen ，Cannot exec './test.sh': 权限不够
)screen -L  -t tes2 -S test  sh ./test.sh 会进入那个screen
cat screen_log/screen_test.log | tail -n 5 |grep /  查看日志

如果启动的时候不加-L参数，启动后，在screen session下按ctrl+a H，同样会在当前目录下生成log文件。
再次按下ctrl+a H，屏幕左下角会提示Logfile "screenlog.0" closed.，停止记录日志。


```

**重要的是：screen+xxxx+ command.sh 不用重新进去conda环境 进去之后在command 就会失去原有的环境**

4如何在linux screen会话中使用鼠标进行上下滚动
```
如果想要在Linux screen会话中使用鼠标进行上下滚动。必须首先进入该screen的回滚(scrollback模式)才能进行上下滚动

第一步： 进入回滚模式
首先按ctr + a或者’command + a’. 然后按Esc

第二步: 使用鼠标滚轮进行上下滑动
第三步：离开回滚模式
按Esc就可以退出了。
[Ctrl]+[B] 翻页
```

```
#创建一个后台运行任务
[root@test #]$ vim test.sh
#!/bin/bash
n=0
while [ $n -le 50 ]
do 
    echo $n
    n=$(( $n + 1 ))
    sleep 1
done
```

```

在 screen session 外的常用命令
screen -S session_name 新建一个名叫session_name的session，并马上进入
screen -dmS session_name 新建一个名叫session_name的session，但暂不进入，可用于系统启动脚本里
screen -ls 列出当前所有session
screen -r session_name 恢复到 session_name 这个session，前提是已经是断开状态（-d可以远程断开会话）
screen -x session_name 连接到离线模式的会话（多窗口同步演示）
screen -wipe 检查目前所有的screen作业，并删除已经无法使用的screen作业

在每个 screen session 下，所有命令都以 ctrl+a(C-a) 开始。
C-a w 显示所有窗口列表
C-a k 这个快捷键杀死当前的窗口，同时也将杀死这个窗口中正在运行的进程。
C-a d detach，暂时离开当前session

新建一个 session 马上进入并执行一段脚本
screen ./bash_name.sh

新建一个暂不进入的 session 并执行一段脚本
screen -dmS session_name
screen -x -S session_name -p 0 -X stuff $'./bash_name.sh\n'
```
screen.sh
如何用bash脚本创建screen并向其发送命令？
为什么要用脚本创建screen？
为了利用服务器的多个cpu，我们经常需要同时创建多个screen，如果screen的个数非常多，手动创建会非常麻烦
```
screen_name=$"my_screen"
screen -dmS $screen_name
cmd=$"python test.py";
screen -x -S $screen_name -p 0 -X stuff "$cmd"
screen -x -S $screen_name -p 0 -X stuff $'\n'

```


script 命令学习  ttyplay  ttyrec
https://www.cnblogs.com/cornell/p/3833955.html

1: 背景
系统管理员经常需要SSH 或者telent 远程登录到Linux 服务器，经常运行一些需要很长时间才能完成的任务，比如系统备份、ftp 传输等等。通常情况下我们都是为每一个这样的任务开一个远程终端窗口，因为它们执行的时间太长了。必须等待它们执行完毕，在此期间不能关掉窗口或者断开连接，否则这个任务就会被杀掉，一切半途而废了。

2: 简介
GNU Screen是一款由GNU计划开发的用于命令行终端切换的自由软件。用户可以通过该软件同时连接多个本地或远程的命令行会话，并在其间自由切换。GNU Screen可以看作是窗口管理器的命令行界面版本。它提供了统一的管理多个会话的界面和相应的功能。

3: 特点
(1)会话恢复
只要Screen本身没有终止，在其内部运行的会话都可以恢复。这一点对于远程登录的用户特别有用——即使网络连接中断，用户也不会失去对已经打开的命令行会话的控制。只要再次登录到主机上执行screen -r就可以恢复会话的运行。同样在暂时离开的时候，也可以执行分离命令detach，在保证里面的程序正常运行的情况下让Screen挂起（切换到后台）。这一点和图形界面下的VNC很相似。

(2)多窗口
在Screen环境下，所有的会话都独立的运行，并拥有各自的编号、输入、输出和窗口缓存。用户可以通过快捷键在不同的窗口下切换，并可以自由的重定向各个窗口的输入和输出。Screen实现了基本的文本操作，如复制粘贴等；还提供了类似滚动条的功能，可以查看窗口状况的历史记录。窗口还可以被分区和命名，还可以监视后台窗口的活动。

(3)会话共享
Screen可以让一个或多个用户从不同终端多次登录一个会话，并共享会话的所有特性（比如可以看到完全相同的输出）。它同时提供了窗口访问权限的机制，可以对窗口进行密码保护。
screen -x screenname


(1) 窗口共享
screen -x screenname
在另一个pc或者是terminal window上面attach一个处于addtched状态的screen, 这样就会共享一个窗口, 操作同步, 相当于同步演示.

(2)会话锁定和解锁
Screen允许使用快捷键C-a s锁定会话。锁定以后，再进行任何输入屏幕都不会再有反应了。但是要注意虽然屏幕上看不到反应，但你的输入都会被Screen中的进程接收到。快捷键C-a q可以解锁一个会话.
解锁对话后window会处理显示在锁定期间的操作.
也可以使用C-a x锁定会话，不同的是这样锁定之后，会话会被Screen所属用户的密码保护，需要输入密码才能继续访问这个会话.
(但是ti2可以用C-a s锁定, 我的screen就不可以, 而且flow off也不行,奇怪)
(3)发送命令给screen
在Screen会话之外，可以通过screen命令操作一个Screen会话，这也为使用Screen作为脚本程序增加了便利。

screen -S screen1 -X screen ping 8.8.8.8
1
在screen1这个screen中临时建立一个新的window来执行ping 8.8.8.8这个命令. 命令完成或者中断之后, 就会结束, 这个window也会消失.
