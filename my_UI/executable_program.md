# Windows
- [x] sd 
- [ ] test2
- [ ] test4

1.首先，安装pyinstaller模块，这个直接在cmd窗口输入命令“pip install pyinstaller”就行，如下：

2.安装完成后，我们就可以直接打包Python程序了，这里为了方便演示，我新建了py文件，测试代码如下，一个非常简单的GUI窗口程序，后面就是对这个程序进行打包，转化为exe可执行程序：

3.接着就是打包，打开cmd窗口，cd切换到py文件所在的目录，运行命令“pyinstaller -F -w py脚本”就会自动开始打包，参数F代表打包成一个独立的exe文件，w代表去掉调试窗口，如下：

4.成功打包后，会在当前目录下生成一个dist目录，里面就有生成好的exe可执行程序，如下，直接双击就可运行：

# Linux

1.首先，也是安装pyinstaller模块，这个直接到官网下载源码，执行“python setup.py intsall”就行，如下：

2.安装完成后，我们就可以直接打包Python程序了，还是以上面的py脚本为例，运行命令也一样—“pyinstaller -F -w py脚本”就会自动开始打包过程，如下：

3.打包完成后，也会在当前目录下生成一个dist目录，里面就有打包好的可执行程序@