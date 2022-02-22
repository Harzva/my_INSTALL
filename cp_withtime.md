```
alias cp='rsync -av --progress'


vi ~/.bashrc
alias cp='rsync -av --progress'

source ~/.bashrc

令实例及说明

------

a) rsync -av  --progress <src-dir>/ <dst-dir>             *** 注意(/) ***

同步src-dir目录下所有文件到dst-dir目录下



b) rsync -av  --progress <src-dir>  <dst-dir>

同步src-dir整个目录到dst-dir目录下（会创建src-dir目录）



c) rsync -avu --progress --delete <src-dir>/  <dst-dir>    *** 注意(/) ***

对src-dir目录内容向dst-dir目录下进行差异更新，有增加/更新则添加替换，有减少则对其删减



d) rsync -av  --progress --temp-dir=/tmp <src-dir>/ <dst-dir>

比a)多了--temp-dir=/tmp，即指定/tmp为临时交换区，这样可以避免因目标目录空间不够引起的无法同步文件的错误。

```
