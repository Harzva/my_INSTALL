
## docker命令去除sudo
```
# 添加docker用户组，一般已存在，不需要执行
sudo groupadd docker     
# 将登陆用户加入到docker用户组中
sudo gpasswd -a ${USER} docker
# 更新用户组
newgrp docker   
# 测试docker命令是否可以使用sudo正常使用
docker version  
```
## 查看容器状态：
```
docker状态
docker stats xxx
docker top xxx
docker ps -a 所有
docker ps 运行的
docker inspect  test2
docker inspect --format='{{.NetworkSettings.IPAddress}}' test2
docker inspect --format '{{.Name}} {{.State.Running}}' test2
```

## docker 容器默认的目录：
```/var/lib/docker/containers目录下 12 位开头的 就是 容器ID

inspect 内容就是 config.v2.json 文件

cat /var/lib/docker/containers/23defb07e362b81fa9d282382dfb5101e7a269f97b3d167493a5b1e031d15120/config.v2.json
```

[史上最全Docker初学者命令大全](http:///cloud.tencent.com/developer/article/1698107)

[Linux Screen技巧：记录屏幕日志](https://blog.csdn.net/lovemysea/article/details/78344114)


sudo docker run -it --gpus all --name test2 bitnami/pytorch:1.3.0-r11 /bin/bash

