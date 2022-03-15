## 安装CUDA和CUDNN


### 安装NVIDIA驱动

可以参考：[Installation/NVIDIA.md](https://github.com/alisure-ml/Installation/blob/master/NVIDIA.md)


### 安装CUDA

* 下载完CUDA 9.0之后执行如下语句，运行.run文件

```
sudo sh cuda_9.0.176_384.81_linux.run
sudo ./cuda_9.0.176_384.81_linux.run 报错
```

单击回车，一路往下运行。

```
Do you accept the previously read EULA?
accept/decline/quit: accept

Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 384.81?
(y)es/(n)o/(q)uit: n  # 选择否，因为已经安装好驱动程序了

Install the CUDA 9.0 Toolkit?
(y)es/(n)o/(q)uit: y

Enter Toolkit Location
 [ default is /usr/local/cuda-9.0 ]:  # 记住安装位置， 默认是安装在/usr/local/cuda文件夹下

Do you want to install a symbolic link at /usr/local/cuda?
(y)es/(n)o/(q)uit: n  # 根据需要选择y或者n

Install the CUDA 9.0 Samples?
(y)es/(n)o/(q)uit: y

Enter CUDA Samples Location
 [ default is /home/ubuntun ]: 

Installing the CUDA Toolkit in /usr/local/cuda-9.0 ...
Missing recommended library: libGLU.so
Missing recommended library: libXmu.so

Installing the CUDA Samples in /home/ubuntun ...
Copying samples to /home/ubuntun/NVIDIA_CUDA-9.0_Samples now...
Finished copying samples.

安装cuda时可能有下面的信息

Installing the CUDA Toolkit in /usr/local/cuda-8.0 …
Missing recommended library: libGLU.so
Missing recommended library: libX11.so
Missing recommended library: libXi.so
Missing recommended library: libXmu.so

原因是缺少相关的依赖库,安装相应库就解决了：
sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev 
————————————————

```

* 配置环境变量，方法一（所有用户，建议使用方法二）：

运行如下命令打开profile文件

```
sudo gedit /etc/profile
```

打开文件后在文件末尾添加路径，也就是安装目录，命令如下：

```
export PATH=/usr/local/cuda-9.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64:$LD_LIBRARY_PATH
```

保存，然后重启电脑:

```
sudo reboot
```

* 配置环境变量，方法二（当前用户，建议使用该方法）：

运行如下命令打开.bashrc文件

```
sudo gedit ~/.bashrc
```

打开文件后在文件末尾添加路径，也就是安装目录，命令如下：

```
export PATH=/usr/local/cuda-10.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64:$LD_LIBRARY_PATH
```

保存，然后使之生效:

```
source ~/.bashrc
```

* 测试安装是否成功

```
cd /usr/local/cuda/samples/1_Utilities/deviceQuery
sudo make
./deviceQuery
```

如果显示关于GPU的信息就是成功了。


* 多个`CUDA`之间切换

```
sudo rm -rf cuda
sudo ln -s /usr/local/cuda-x.x /usr/local/cuda
```

### 安装cudnn——my
https://developer.nvidia.com/rdp/cudnn-archive
cuDNN Library for Linux 是最好的 
cp  cudnn-10.0-linux-x64-v7.6.5.32.solitairetheme8   cudnn-10.0-linux-x64-v7.6.5.32.tgz
tar -xvf cudnn-10.0-linux-x64-v7.6.5.32.tgz


复制解压好的文件到对应的目录
```
sudo cp cuda/include/cudnn.h /usr/local/cuda/include
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
```
3安装多版本CUDA
按照上面两节安装另外版本的CUDA。假设都是默认的安装路径/usr/local/，现在安装了两个版本的CUDA
```
/usr/local/cuda-10.0
/usr/local/cuda-10.1
```
查看当前cuda软链接指向的是哪个版本
```
stat /usr/local/cuda
```
切换版本

# 建立需要切换版本的软链接,替换现有的软链接
sudo ln -sf /usr/local/cuda-10.1 /usr/local/cuda

4 使用中可能会遇到的问题
1、libcudnn.so.7 is not a symbolic link

找不到软链接，到cuda的lib64目录，默认的是/usr/local/cuda/lib64，建立软链接

cd /usr/local/cuda/lib64
sudo ln -sf libcudnn.so.7 libcudnn.so

2、Could not dlopen library 'libcudnn.so.7’

到cuda的lib64目录，默认的是/usr/local/cuda/lib64，找到自己安装的cudnn的版本对应的ibcudnn.so

# 建立软链接
sudo ln -sf libcudnn.so.7.6.5 libcudnn.so.7

# 加载动态库
sudo ldconfig /usr/local/cuda/lib64

如果还不行

# 编辑配置文件
sudo vim /etc/ld.so.conf.d/cuda.conf

# 添加cuda的lib64路径到文件中
/usr/local/cuda/lib64

# 加载动态库
sudo ldconfig

### 安装cudnn

> Inference: [Install_AND_path/install nvidiaDriver_cuda_cudnn.md](https://github.com/waallf/Install_AND_path/blob/master/install%20nvidiaDriver_cuda_cudnn.md)

1. 下载对应版本的[cudnn](https://developer.nvidia.com/cudnn)

2. 需要下载两个版本，runtime版和developer版

```
cuDNN Runtime Library for Ubuntu18.04 (Deb)
cuDNN Developer Library for Ubuntu18.04 (Deb)
```

3. 将下载的文件格式改为.tgz，然后解压

4. 一个里版本里面有头文件(在include中)，一个里面有动态连接文件（在lib中）

  * 将`include`中头文件`cudnn.h`拷贝到`/usr/local/cuda/include`
  * 将`lib`中的动态连接文件拷贝到`/usr/local/cuda/lib64`

5. 添加环境变量

> 如果添加过环境变量，就可以不添加。可以通过`echo $LD_LIBRARY_PATH`查看是否添加。

运行如下命令打开.bashrc文件
```
sudo gedit ~/.bashrc
```

打开文件后在文件末尾添加路径，也就是安装目录，命令如下：
```
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

保存，然后使之生效:
```
source ~/.bashrc
```

6. 对拷贝进来的两个动态连接库创建软链接

```
cd /usr/local/cuda/lib64/
sudo ln -s libcudnn.so.7 libcudnn.so
# sudo ln -s libcudnn.so.7.x.x libcudnn.so.7
```


### 问题一：Pycharm中找不到cuda

> Inference: [Install_AND_path/无法找到cuda9.0](https://github.com/waallf/Install_AND_path/blob/master/%E6%97%A0%E6%B3%95%E6%89%BE%E5%88%B0cuda9.0.md)

在添加cuda环境变量后，一直无法找到cuda9.0:
1. 有可能是在sudo下执行的，需要在sudo下添加环境变量

2. 添加lib

打开文件`cuda.conf`：
```
sudo gedit /etc/ld.so.conf.d/cuda.conf
```

添加如下内容并保存：
```
/usr/local/cuda/lib64 
/lib
/usr/lib
/usr/lib32
```


### 问题二：ImportError: libcublas.so.x.x: cannot open shared object file: No such file or directory

> Inference: [ImportError: libcublas.so.9.0: cannot open shared object file: No such file or directory](https://blog.csdn.net/qq_34374211/article/details/81018320)

* 确保安装了对应版本的`CUDA`：否则，回到`安装CUDA`的步骤

* 确保路经在`PATH`环境变量中(`echo $PATH`)：否则，回到安装`配置环境变量`的步骤

* 如果还不行，检查`/usr/local/cuda-x.x/lib64`下是否有libcublas.so.x.x：如果有，则`sudo ldconfig /usr/local/cuda-x.x/lib64`

