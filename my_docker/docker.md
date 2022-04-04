
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
docker rmi 镜像id
docker rm bde00bc086cf
docker exec -it ubcu10 /bin/bash
 
```

## docker 容器默认的目录：
```/var/lib/docker/containers目录下 12 位开头的 就是 容器ID

inspect 内容就是 config.v2.json 文件

cat /var/lib/docker/containers/23defb07e362b81fa9d282382dfb5101e7a269f97b3d167493a5b1e031d15120/config.v2.json
```

[史上最全Docker初学者命令大全](http:///cloud.tencent.com/developer/article/1698107)

[Linux Screen技巧：记录屏幕日志](https://blog.csdn.net/lovemysea/article/details/78344114)


sudo docker run -it --gpus all --name ubcu10 -p 10001:22 -p 10002:10002  -v /media/ubuntu/T7/hzh/:/media/ubuntu/T7/hzh   nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04  /bin/bash

sudo docker run -it --gpus all --name ubcu10-t1.3 -p 10003:22 -p 10003:10003  -v /media/ubuntu/T7/hzh/:/media/ubuntu/T7/hzh  huicongzhang/pytorch1.3-cuda10-cudnn7   /bin/bash



一般用到的是1到65535,其中0不使用。
1-1023为知名端口（Well-Known Ports）。
1024-49151为用户端口（Registered ports）。
49152-65535称为动态端口（Dynamic Ports）。
知名端口即众所周知的端口号，范围从0到1023，这些端口号一般固定分配给一些服务。
用户端口由IANA负责分配，需要走申请流程，申请手续相对系统端口来说不那么严格。
动态端口的范围从49152到65535，这些端口号一般不固定分配给某个服务，也就是说许多服务都可以使用这些端口。

常用端口记录
21端口：FTP 文件传输服务
22端口：SSH 远程连接服务
23端口：TELNET 终端仿真服务
25端口：SMTP 简单邮件传输服务
53端口：DNS 域名解析服务
80端口：HTTP 超文本传输服务
443端口：HTTPS 加密的超文本传输服务
3306端口：MYSQL数据库端口
3389端口：WIN2003远程登陆
8080端口：TCP服务端
8888端口：Nginx服务器

UDP67，UDP68：DHCP服务
