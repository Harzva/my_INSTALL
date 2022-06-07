
```
def uploadToSVN(self, ret_excel_time):
 
	# upload xls file SVN
	filename = "result_" + ret_excel_time + ".xls"
	print "\n Upload xls file to SVN : --> \nsvn://192.168.xxx.xxx/trunk/data/sweepsCrawlerData/" + filename + "\n"
 
	#svn resolved %s & \
	#svn commit -m '' %s & \
	#svn update & \
	#svn revert %s & \
	cmd = '''start E:\sweepstake_site_crawlers\data\\result & \
	E: & \
	cd E:\sweepstake_site_crawlers\data\\result & \
	svn cleanup & \
	svn add %s & \
	svn resolved %s & \
	svn commit -m '' %s & \
	svn update & \
	''' % (filename,filename,filename)
	
	os.system(cmd)
```

os.system() 是python自带的并适用于各平台的一个函数，其主要作用就是执行终端命令。这里介绍了一下如何通过这个函数打开各个平台的终端，网上大多是关于如何执行终端命令，对终端的打开提及较少，这里做一个简单的总结。（有人可能会想为什么需要通过代码打开终端这种多此一举的行为，而不是直接打开，嘛，有些人的需求比较特殊。）

Windows：
打开一个终端：

os.system('start cmd')
1
打开终端的同时执行指令

command = "ls"
os.system('start cmd /k'+command)
os.system('start cmd /c'+command)
1
2
3
这里的 /k 是option，其作用是运行完command时候返回到cmd 窗口。/c 则是运行完command 终止终端，也就是关闭cmd窗口。更多具体的option请参考以下链接：CMD.

Linux:
打开一个终端

os.system("gnome-terminal")
1
打开终端的同时执行指令

command="ls"
os.system("gnome-terminal -e '%s"%command)
os.system("gnome-terminal -e 'bash -c \"%s; exec bash\"'"%command)
1
2
3
第一条 os.system 是执行一次命令并关闭终端。
第二条 os.system 是执行一次命令返回终端。

GNOME Terminal 是 Linux 系统默认的terminal app的名字。
这两条指令的出处 原始链接

mac:
打开一个终端

os.system("open -a Terminal .")
1
如果是执行一个文件

os.system("open %s"%path)
1
如果执行一个终端命令,需要其他的module (如果有不需要的方法，欢迎留言告知)

import applescript
comand="ls"
appscript.app('Terminal').do_script(command)
1
2
3
关于苹果执行命令的出处 点这里
Applescript 官方链接

以下是python 官网对这个函数的解释。官网说明

os.system(command)
在子 shell 中执行命令（字符串）。这是调用标准 C 函数 system() 来实现的，因此限制条件与该函数相同。对 sys.stdin 等的更改不会反映在执行命令的环境中。command 产生的任何输出将被发送到解释器标准输出流。在 Unix 上，返回值是进程的退出状态，编码格式与为 wait() 指定的格式相同。注意，POSIX 没有指定 C 函数 system() 返回值的含义，因此 Python 函数的返回值与系统有关。在 Windows 上，返回值是运行 command 后系统 Shell 返回的值。该 Shell 由 Windows 环境变量 COMSPEC: 给出：通常是 cmd.exe，它会返回命令的退出状态。在使用非原生 Shell 的系统上，请查阅 Shell 的文档。

