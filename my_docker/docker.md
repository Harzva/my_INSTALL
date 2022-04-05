
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



# 一、基础命令
## 1. 帮助命令

```
docker --version  # 显示docker的版本信息
docker info    # 显示docker的系统信息
docker 命令 --help    # 显示帮助命令
```

## 2. 镜像命令
### 2.1 搜索镜像

```
# 搜索镜像
docker search mysql
# 条件过滤搜索结果
docker search --filter=STARS=5000

image-20200906131527917

「列表解释」

「NAME: 镜像名称」
「DESCRIPTION: 镜像介绍」
「STARS: 镜像的stars」
「OFFICIAL: 是否是官方提供的」
「AUTOMATED:  是不是自动化的」
```

### 2.2 拉取镜像

```
# 默认拉取最新的镜像
docker pull mysql
# 指定版本下载
docker pull mysql:5.7
```

### 2.3 查看所有镜像

```
# 查看所有镜像信息
docker images -a
# 查看所有的镜像id
docker images -aq

image-20200906130452865

「列表解释」

「REPOSITORY: 镜像的仓库源」
「TAG:                镜像的标签」
「IMAGE ID:       镜像的id」
「CREATE:          镜像的创建时间」
「SIZE:                镜像的大小」
```

### 2.4 删除镜像


```
[#删除指定id的镜像
docker rmi 镜像id
docker rmi 镜像id 镜像id 镜像id 镜像id
#删除指定名称的镜像
docker rmi mysql:5.7
#迭代删除所有的镜像
docker rmi -f $(docker images  -aq)
```

## 3. 容器命令
### 3.1 运行镜像

```
docker run [可选参数] image
# 运行实例
docker run --name=mycat -d -p 8080:8080 tomcat
# 用完即删
docker run -it --rm tomcat
# 指定环境变量（实例）
docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx512m"  elasticsearch:7.6.2
「参数说明」

「--name="Name"：容器名字 tomacat01、tomacat02区分容器」
-「e」: 「指定环境变量」
「-d：后台守护进程运行」
「-it：使用交互方式运行，进入容器查看内容」
「-p：指定容器的端口 -p 8080:8080」
「-p ：主机端口：容器端口」
「-p ：容器端口」
「-P：随机指定端口」
「-v:  指定数据卷」
「-v 容器文件位置:宿主机文件位置」
「--volumes-from: 指定容器的数据卷共享（指定谁，就同步谁的数据！继承！）」
「--volumes-from:继承自那个容器」（父容器删除不影响已存在数据）
「--net: 缺省 bridge」
```

### 3.2 进入容器

```
# 运行一个centos并进入到容器里面
docker run -it centos /bin/bash
# 退出容器
exit
```

### 3.3 查看容器

```
# 查看正在运行中的容器
docker ps
# 查看所有容器
docker ps -a
```

### 3.4 退出容器

```
exit   # 直接容器停止并退出
Ctrl + P + Q  # 容器退出不停止
```

### 3.5 删除容器

```
# 删除指定容器
docker rm bde00bc086cf
# 强制删除运行中的容器
docker rm -f bde00bc086cf
# 迭代删除全部的容器
docker rm -f $(docker ps -aq)
```

### 3.6 容器的启动与停止

```
# 启动容器
docker start 容器id
# 重启容器
docker restart 容器id
# 停止容器
docker stop 容器id
# 强制杀死容器
docker kill 容器id
```

### 3.7 进入当前在正在运行中的命令

```
# 进入到指定容器内部进行修改  开启一个新的终端
docker exec -it 0cd4d9d94de2 /bin/bash
# 进入到正在执行中的终端
docker attach 容器id
```

### 3.8 将文件从容器拷贝到宿主机上

```
docker cp 容器id:容器内文件的路径 宿主机路径
#实例
docker cp 0cd4d9d94de2:/Test.java /Test.java
```

### 3.9 其他常用命令

```
「查看日志命令」

# 查看容器运行产生的日志
docker logs -ft --tail 10 容器id
「参数解析：」

「f:  格式化日志」
「t: 携带日志时间戳」
「查看进程」

# 查看cpu等信息
docker top 0cd4d9d94de2
# 查看容器元信息
docker inspect 容器id
```

# 二、可视化面板
## 1、安装

```
# 安装可视化面板 portainer （数据卷路径不可改变）
docker run -d -p 8088:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer

image-20200906161505532
```


# 三、提交容器为一个镜像
## 1.提交容器

```
# 提交一个容器为一个镜像（将容器打包）
docker commit [可选参数] 服务id 自定义镜像名称[:版本标签]
# 示例代码提交
docker commit  -a="huangfu" -m="增加了主页" 19329ae6df90  diytomcat:1.0
「参数解释：」

「-a: 作者」
「-m: 备注」
「-c: 将Dockerfile指令应用于创建的映像」
「-p: 提交期间暂停容器（默认为true）」
```

# 四、Docker数据卷使用
## 1.数据卷的基本使用

```
# 关联数据卷
docker run [可选参数] -v /主机路径/:/容器路径/ 镜像名称
# 关联数据卷的实例命令
docker run -d -p 8080:8080 --name mytomcat -v /home/tomcat/webapps/:/usr/local/tomcat/webapps tomcat
```

## 2.mysql安装实战

```
docker run -d -p 3366:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7
「命令解析：」

「-d: 守护进程运行」
「-v: 添加数据卷（宿主机位置和容器位置映射）」
「-p: 堆对外映射端口」
「-e: 指定环境变量」
「--name: 容器名称」
```

# 五、Dockerfile
## 1. 构建镜像文件
```
# 创建一个Dockerfile

vim Dockerfile

FROM centos

VOLUME ["volume01","volume02"]

CMD echo "-----end---"
CMD /bin/bash

:x

# 构建docker镜像
# -f dockerfile的路径   
# -t 生成的镜像名称
# . 以当前路径为上下文打包
docker build -f /home/docker-volom/Dockerfile -t huangfu/centos:1.0 .

# 构建基本命令
docker build [OPTIONS] PATH | URL | -
##2. Dockerfile概念
每个保留关键字（指令）都必须是大写字母
执行顺序从上到下
# 表示注释
每一个指令都会创建提交一个新的镜像层并提交！
```

## 3. Dockerfile语法浅析

```

image-20200906203902072

「FROM: 基础镜像，一切都从这里开始构建」
「MAINTAINER: 镜像是谁写的，姓名+邮箱」
「RUN: 镜像构建需要运行的命令」
「ADD: 添加一个内容，比如需要添加一个tomcat，则需要传递一个压缩包，便于在容器内构建！」
「WORKDIR: 镜像的工作目录」
「VOLUME: 挂在的目录」
「EXPOSE: 暴露端口」
「CMD: 一个指令，指定这个容器启动的时候要运行的命令」
「ENTRYPOINT: 指定这个容器启动的时候要运行的命令！可以追加命令！」
「ONBUILD: 当构建一个被继承的Dockerfile 这个时候就会运行指令，触发命令！」
「COPY: 类似与ADD，将文件拷贝到镜像中」
「ENV：构建的时候设置环境变量」
# 构建一个具有复杂命令行的centos
vim Dockerfile

# 镜像继承自centos
FROM centos
# 作者信息
MAINTAINER huangfu<huangfusuper@163.com>
# 设置环境变量
ENV MYPATH /usr/local
# 设置工作目录
WORKDIR $MYPATH
# 执行命令安装指令
RUN yum -y install vim
RUN yum -y install net-tools
# 暴露端口
EXPOSE 80
# 执行一些指令
CMD echo "-------end------"
CMD echo $MYPATH
CMD /bin/bash
```


:x

# 构建镜像
docker build -f /home/docker-volom/Dockerfile -t huangfu/diycentos:1.0 .
# 六、自定义网络
## 1. 网络模式详解

```
「bridge: 桥接网络（默认）」
「host：和宿主机共享」
「none：不配置网络」
「container：容器网络联通」
```

## 2. 查看所有的网络模式

```
# 查看所有的网络模式
docker network ls
```

## 3. 创建自定义的网络

```
# 创建一个网络
docker network create [OPTIONS] NETWORK

# 创建一个mynet
# create 创建
# driver 使用的网络模式
# subnet 子网掩码
# gateway 网关
# mynety 自定义的名称
docker netywork create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 mynety
## 4. 使用自定义网络
docker run -d --net mynety --name tom01  tomcat
docker run -d --net mynety --name tom02  tomcat

# 进入到tom02
docker exec -it 7d75a637a90b865fe70259bd4e0b3f5c95133dc65693b05abaf078d31a362529 /bin/bash
# 结果是互通的
ping tom01

image-20200906213345122

## 5. 容器网络互通
# 把自定义网络和容器打通    容器一个容器两个ip
# 把不在该网络的容器加入当前网络
docker network connect 自定义网络 容器
```

# 七、打包SpringBoot jar项目
## 1. Dockerfile编写

```
FROM java:8

COPY *.jar /app.jar

CMD ["--server.port=8080"]

EXPOSE 8080

ENTRYPOINT ["java","-jar","/app.jar"]
```

## 2. 构建镜像

```
mkdir idea

cd idea

# 将 Dockerfile与jar包发送到idea目录
# 构建镜像
docker build -t huangfutest:1.0 .
# 后面运行不说了
```
