

一般上设定开机自动执行指令, 可以编辑 /etc/rc.local 档案, 而除了编辑 /etc/rc.local 外, 也可以用 crontab 完成。

crontab 是十分好用的排程自动执行工具, 它指定执行时间间隔十分灵活, 其中一个做法是用 @reboot 参数, 设定成每次开机自动执行。

首先开启 crontab:

# crontab -e
加入以下一行:
@reboot sleep 60 ; /root/my-script.sh
以上一行设定开机后等待 1 分钟 (60 秒), 自动执行 /root/my-script.sh, 将上面的 /root/my-script.sh 改成要执行的指令。