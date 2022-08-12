[docker gpu报错Error response from daemon: could not select device driver  with capabilities](https://blog.csdn.net/weixin_44966641/article/details/123760614)

[Debug docker: docker: Error response from daemon: could not select device driver ““ with capabilitie](https://blog.csdn.net/weixin_38812492/article/details/114338589)

安装toolkit
关于配置docker19使用gpu，其实只用装官方提供的toolkit即可，把github上的搬下来：
Ubuntu 16.04/18.04, Debian Jessie/Stretch/Buster：

```
# Add the package repositories
$ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
$ curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

$ sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
$ sudo systemctl restart docker

```



测试安装是否成功
  经过以上大部分linux系统的docker toolkit应该都能安装成功，如不能安装成功，可参考github官网，查看是否安装成功：
(1) 查看–gpus 参数是否安装成功：


```
$ docker run --help | grep -i gpus
      --gpus gpu-request               GPU devices to add to the container ('all' to pass all GPUs)
```


(2) 运行nvidia官网提供的镜像，并输入nvidia-smi命令，查看nvidia界面是否能够启动：

`docker run --gpus all nvidia/cuda:9.0-base nvidia-smi`

运行gpu的容器
# 使用所有GPU
`$ docker run --gpus all nvidia/cuda:9.0-base nvidia-smi`

# 使用两个GPU
`$ docker run --gpus 2 nvidia/cuda:9.0-base nvidia-smi`

# 指定GPU运行

```
$ docker run --gpus '"device=1,2"' nvidia/cuda:9.0-base nvidia-smi
$ docker run --gpus '"device=UUID-ABCDEF,1"' nvidia/cuda:9.0-base nvidia-smi
```

