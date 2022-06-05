my_windows:
Step2 输入命令runas /users:管理员用户名 cmd

在目录：C:\Users\18452\AppData\Roaming\picgo>中进行操作

补充一点 如果安装缓慢 长时间卡住不动 去设置npm 的数据源为淘宝的。
```
1、命令 npm config set registry https://registry.npm.taobao.org
2、验证命令 npm config get registry 如果返回 https://registry.npm.taobao.org，说明镜像配置成功。
3、最后执行npm install picgo-plugin-gitee-uploader
```


https://blog.csdn.net/lunhui601/article/details/107722580
