
打开有x服务器的远程shell工具，比如mobaxterm，Xshell等，连接远程主机（vscode连接的主机）

1.输入

`env | grep DISPLAY # 在系统终端上查看DISPLAY`
```bash
DISPLAY=localhost:10.0
```
2.回到vscode，在终端输入,仅对本次打开有效
export DISPLAY=localhost:10.0



 _注意：此方法必须保持shell工具打开，且下一次打开工程还要打开shell共工具并在vscode输入
export DISPLAY=localhost:10.0_ 


