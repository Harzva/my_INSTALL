
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
docker exec -it ubcu10 /bin/bash 进入正在运行的容器


重启容器：docker restart 容器ID

重启容器后进入交互式：docker start -i 5c6ce895b979

进入容器：docker attach 容器ID

 docker exec -it 容器ID /bin/bash 
```

## docker 容器默认的目录：
```/var/lib/docker/containers目录下 12 位开头的 就是 容器ID

inspect 内容就是 config.v2.json 文件

cat /var/lib/docker/containers/23defb07e362b81fa9d282382dfb5101e7a269f97b3d167493a5b1e031d15120/config.v2.json
```

[史上最全Docker初学者命令大全](http:///cloud.tencent.com/developer/article/1698107)

[Linux Screen技巧：记录屏幕日志](https://blog.csdn.net/lovemysea/article/details/78344114)


sudo docker run -it --gpus all --name ubcu10 -p 10001:22 -p 10002:10002  -v /media/ubuntu/T7/hzh/:/media/ubuntu/T7/hzh   nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04  /bin/bash

sudo docker run -it --gpus all --name ubcu10-t1.3 -p 10003:22 -p 10004:10004  -v /media/ubuntu/T7/hzh/:/media/ubuntu/T7/hzh  huicongzhang/pytorch1.3-cuda10-cudnn7   /bin/bash

镜像重命名
 docker  tag  镜像id  仓库：标签

容器重命名
docker rename ubcu10-t1.3 ubcu10-p3.6-t1.3



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

[docker-修改容器挂载目录的3种方法小结](docker-修改容器挂载目录的3种方法小结)

[systemctl和service、chkconfig命令的关系](https://cshihong.github.io/2018/10/15/Linux%E4%B8%8Bsystemctl%E5%91%BD%E4%BB%A4%E5%92%8Cservice%E3%80%81chkconfig%E5%91%BD%E4%BB%A4%E7%9A%84%E5%8C%BA%E5%88%AB/#:~:text=%E6%89%80%E8%B0%93%E7%B3%BB%E7%BB%9F%E6%9C%8D%E5%8A%A1%20%28service%29%EF%BC%8C%E5%B0%B1%E6%98%AF%E9%9A%8F%E7%B3%BB%E7%BB%9F%E5%90%AF%E5%8A%A8%E8%80%8C%E5%90%AF%E5%8A%A8%EF%BC%8C%E9%9A%8F%E7%B3%BB%E7%BB%9F%E5%85%B3%E9%97%AD%E8%80%8C%E5%85%B3%E9%97%AD%E7%9A%84%E7%A8%8B%E5%BA%8F%E3%80%82%20systemctl%E5%91%BD%E4%BB%A4%E6%98%AF%E7%B3%BB%E7%BB%9F%E6%9C%8D%E5%8A%A1%E7%AE%A1%E7%90%86%E5%99%A8%E6%8C%87%E4%BB%A4%EF%BC%8C%E5%AE%83%E5%AE%9E%E9%99%85%E4%B8%8A%E5%B0%86%20service%20%E5%92%8C,chkconfig%20%E8%BF%99%E4%B8%A4%E4%B8%AA%E5%91%BD%E4%BB%A4%E7%BB%84%E5%90%88%E5%88%B0%E4%B8%80%E8%B5%B7%E3%80%82%20systemctl%E6%98%AFRHEL%207%20%E7%9A%84%E6%9C%8D%E5%8A%A1%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7%E4%B8%AD%E4%B8%BB%E8%A6%81%E7%9A%84%E5%B7%A5%E5%85%B7%EF%BC%8C%E5%AE%83%E8%9E%8D%E5%90%88%E4%B9%8B%E5%89%8Dservice%E5%92%8Cchkconfig%E7%9A%84%E5%8A%9F%E8%83%BD%E4%BA%8E%E4%B8%80%E4%BD%93%E3%80%82)
