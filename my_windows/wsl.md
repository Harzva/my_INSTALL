admin 权限打开termianl

执行下面的命令：
```
Dism /Online /Cleanup-Image /CheckHealth  是检查映像以查看是否有检测到损坏
Dism /Online /Cleanup-Image /ScanHealth   是扫描你全部系统文件并和官方系统文件对比
```


check结果全部ok
3. 停止wsl， 重新启动

`wsl --shutdown`

输入bash 等待重启
