
# libSM.so.6

ImportError: libSM.so.6: cannot open shared object file: No such file or directory

ImportError: libXrender.so.1: cannot open shared object file: No such file or directory

ImportError: libXext.so.6: cannot open shared object file: No such file or directory

ImportError: libgthread-2.0.so.0: cannot open shared object file: No such file or directory

首先，需要更新一下apt源。这一步是因为我经常遇到，直接 apt-get install 指定的包找不到的情况。没有问题的同学可以直接到下一步。

apt-get update
接下来是安装libsm6，libxrender1 和 libxext-dev。

apt-get install libsm6

apt-get install libxrender1

apt-get install libxext-dev

apt-get install libglib2.0-dev
 
