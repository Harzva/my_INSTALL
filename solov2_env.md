 python 3.6 cuda 10.0 cuda 10.2 pytorch1.6 vscode nvidia quadro p2200 5gnvidia
查看nvidia信息

[Windows cuda](https://blog.csdn.net/Geoffrey0718/article/details/123772477)

[windows 换源](https://blog.csdn.net/moshiyaofei/article/details/103317983)
卸载原有python
# 一、安装anconda（python3.6）
## 1.下载 Anaconda3-5.2.0-Windows-x86_64 这个版本自带python3.6
[Anaconda3-5.2.0-Windows-x86_64.exe](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.2.0-Windows-x86_64.exe)
## 2.安装anconda（管理员权限）
参考 [Windows 10中Anaconda及Python环境的下载与安装方法](https://zhuanlan.zhihu.com/p/461960116/)
# 二、vscode
# 三、 pytorch
pip install torch==1.6.0+cu102 torchvision==0.7.0+cu102 -f https://download.pytorch.org/whl/torch_stable.html

pip install torch==1.6.0+cu101 torchvision==0.7.0+cu101 -f https://download.pytorch.org/whl/torch_stable.html

pip install torch==1.6.0+cu102 torchvision==0.7.0+cu102  -ihttps://mirrors.aliyun.com/pypi/simple/

