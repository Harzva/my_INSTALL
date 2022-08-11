

一般上设定开机自动执行指令, 可以编辑 /etc/rc.local 档案, 而除了编辑 /etc/rc.local 外, 也可以用 crontab 完成。

## 1.crontab 是十分好用的排程自动执行工具, 它指定执行时间间隔十分灵活, 其中一个做法是用 @reboot 参数, 设定成每次开机自动执行。

首先开启 crontab:

`crontab -e`
加入以下一行:
```python

@reboot sleep 60 ; /root/my-script.sh

```
以上一行设定开机后等待 1 分钟 (60 秒), 自动执行 /root/my-script.sh, 将上面的 /root/my-script.sh 改成要执行的指令。


## 2.问题描述：假设有一个定时任务，内容如下：

```

00 00 * * * screen -S test; echo "test screen"; screen -d test
```


解释：每天晚上00:00， 用screen开启一个名为test会话，然后执行命令，之后将会话detached放在后台执行。

但该命令无法正常执行，你会在系统邮件中收到该任务的执行失败提示：


```
Must be connected to a terminal.
test screen
There is no screen to be detached matching test.
```


解决方法：

首先，在crontab命令之外，先用screen新建一个会话，比如还是上述的test
crontab中的命令写为如下形式：

`screen -S sessionname -X stuff 'command'`echo -ne '\015'``

该命令的含义：将特定command发送到特定的screen会话,其中，echo -ne '\015'模拟的是按下回车键。
注意： command与最后的echo命令之间没有空格。比如，依旧是上述定时任务，就可写成如下形式：

`screen -S test -X stuff 'echo ""test screen""'`echo -ne '\015'``

## 3 screen

screen使用-dmS参数以detached模式启动screen
screen名称和执行的命令使用变量传送，而不能直接在命令行指定。
虚拟环境需要从绝对路径激活。
上代码。创建/root/startup.sh,赋予执行权限，内容如下：


```
#!/bin/bash
screen_name="updatepic"  
screen -dmS $screen_name 
cmd1="source ~/.bashrc"
cmd2="source ~/.pyenv/versions/py366/bin/activate"
cmd3="python apscheduler_update_pic.py";  
screen -x -S $screen_name -p 0 -X stuff "$cmd1"
screen -x -S $screen_name -p 0 -X stuff '\n'
screen -x -S $screen_name -p 0 -X stuff "$cmd2"
screen -x -S $screen_name -p 0 -X stuff '\n'
screen -x -S $screen_name -p 0 -X stuff "$cmd3"  
screen -x -S $screen_name -p 0 -X stuff '\n' 
```


