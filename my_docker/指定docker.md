### 1.保证apt源的codename和系统版本一致
### 2.安装依赖

```
$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```


### 3.添加 Docker 官方的 GPG 密钥（为了确认所下载软件包的合法性，需要添加软件源的 GPG 密钥）

```
（官方）$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
（国内）$ curl -fsSL https://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

```

### 4.设置稳定版本的apt仓库地址
（官方）

```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
（国内）
$ sudo add-apt-repository \
     "deb [arch=amd64] https://mirrors.aliyun.com/docker-ce/linux/ubuntu \
     $(lsb_release -cs) \
     stable"
```


### 5.刷新源
`$ sudo apt-get update`

### 6.查看版本
`[$ sudo apt-cache madison docker-ce](http://)`

### 7.安装

```
（最新版本）$ sudo apt-get install docker-ce docker-ce-cli containerd.io
（指定版)$ sudo apt-get install docker-ce=5:19.03.5~3-0~ubuntu-bionic docker-ce-cli=5:19.03.5~3-0~ubuntu-bionic containerd.io
```


### 8.验证
`$ sudo docker --version`

### 9.镜像加速配置
`$ sudo curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://f1361db2.m.daocloud.io`

### 10.重启docker服务
`$ sudo systemctl restart docker`
