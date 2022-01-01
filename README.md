# Installation
安装遇到的软件或者框架

在 windows 客户端生成秘钥
# 进入 cmd 命令行，直接执行以下命令
ssh-keygen
为了简单起见，这里一路回车，不需要设置任何密码。

# 结果
会在 用户/.ssh/ 目录下生成两个文件，私钥： id_rsa，公钥： id_rsa.pub

将公钥放到服务端
# 将公钥上传到目录 /home/.ssh 
将公钥密写入文件：
```
cat id_rsa.pub >> authorized_keys
```

重新打开vscode 项目即可。
如果有问题，还无法打开， 请见检查服务端文件权限：
```
chmod 664 authorized_keys
chmod 700 .ssh/
```

