https://mp.weixin.qq.com/s/B-ip7Fs25jckxQOFc7BXQg
https://blog.csdn.net/lovemysea/article/details/78344114


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
```
screen_name=$"my_screen"
screen -dmS $screen_name
cmd=$"python test.py";
screen -x -S $screen_name -p 0 -X stuff "$cmd"
screen -x -S $screen_name -p 0 -X stuff $'\n'

```

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
2.分离模式 暂时不需要
```
#创建处于分离模式的会话，启动后直接断开会话
[root@test #]$ screen -dmS test./test.sh
#此时会话已断开，但是任务仍在运行，相当于把任务放在后台运行  nohub

creen -L -dmS test的意思是启动一个开始就处于断开模式的会话，会话的名称是test。
screen -r test连接该会话，在会话中的所有屏幕输出都会记录到screenlog.0文件。
```
3.输出日志 
```
#其中%t 为标题，如screen_test.log
echo "logfile /root/screen_%t.log" >> /etc/screenrc
#-L 打开日志输出
#-t 为标题
#执行命令后，会在/root下生成screen_test.log
screen -L -t test -dmS test ./test.sh


2)
不加选项-L，启动后，在screen session下按ctrl+a H，同样会在当前目录下生成screenlog.0文件。
再次按下ctrl+a H，屏幕左下角会提示Logfile "screenlog.0" closed.，停止记录日志。
上面两个方法有个缺点：当创建多个screen会话的时候，每个会话都会记录日志到screenlog.0文件。screenlog.0中的内容就比较混乱了。
vim 
解决方法如下，让每个screen会话窗口有单独的日志文件。

在screen配置文件/etc/screenrc最后添加下面一行：sudo -i   echo "logfile /root/screen_%t.log" >> /etc/screenrc

logfile /tmp/screenlog_%t.log
logfile ./screenlog_%t.log 则是把日志文件记录到当前目录下。
%t是指window窗口的名称，对应screen的-t参数。所以我们启动screen的时候要指定窗口的名称，例如：
screen -L -t window1 -dmS test的意思是启动test会话，test会话的窗口名称为window1。 
#-L 打开日志输出 #-t 为标题
屏幕日志记录在/tmp/screenlog_window1.log。如果启动的时候不加-L参数，在screen session下按ctrl+a H，日志也会记录在/tmp/screenlog_window1.log。

screen -L -t name -S name ./name
第一个name是记录日志的名字，第二个name是screen -ls 列表展示出来的名字，第三个name是需要运行的程序。
```

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

script 命令学习  ttyplay  ttyrec
https://www.cnblogs.com/cornell/p/3833955.html
