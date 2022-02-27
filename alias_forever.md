2in1080
alias hzh="cd /home/ubuntu/dataset/hzh/One-Shot-Object-Detection-main/ ; source /opt/conda/bin/activate /home/ubuntu/miniconda3/envs/hzh36t12"
taitan
alias hzh="cd /media/ubuntu/data1/hzh/One-Shot-Object-Detection-main/ ; conda activate hzh36t11"
alisure1
alias hzh="cd /mnt/4T/hzh/One-Shot-Object-Detection/ ; conda activate hzh36t11"
2out1080
alias hzh="cd /home/ubuntu/Dataset/Partition1/hzh/lj/One-Shot-Object-Detection-main/ ; conda activate hzh36t11"
screen -dms osod1 bash xx.sh


1.首先我们查看一下系统的环境变量-全局的，我们可以看到在文件头部有一行信息，提示函数和别名在/etc/bashrc中

2.查看/etc/bashrc我们发现又有一个提示，说不建议修改该文件，最好是在/etc/profile.d/建立一个shell脚本
3.我们进入到/etc/profile.d/新建一个脚本，格式为：脚本名（任意）.sh，这里我新建一个叫alias_bash.sh的脚本，写入自己的别名代码
命令：vim alias_bash.sh


source alias_bash.sh
