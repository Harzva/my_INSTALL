现在我们本地和远程均有一个文件夹“sftpFolder”，用VsCode打开本地文件夹“sftpFolder”，然后执行 ctrl+shift+p ，搜索 SFTP:Config ，回车后，会生成一个“.vscode/sftp.json”，这个就是配置文件。
同时，如下图左侧会多了一个“远程目录”。需要两边同时vscode在线吗 不用 但是1》2 》3 1想到3  2必须在线
同时，profiles activate 状态的服务器会更新 切换另一个时并不会更新除非保存文件才会更新，或者全部上传，但profiles模式下的全部上传 ignore有问题，不能忽略


https://github.com/liximomo/vscode-sftp
```
{
    "name": "alisure",
    "host": "10.170.15.237",
    "protocol": "sftp",
    "port": 22,
    "username": "ubuntu",
    "password":"asdfg",
    "remotePath": "/media/ubuntu/4T/hzh/lj/One-Shot-Object-Detection-main/",
    "uploadOnSave": true,
    "downloadOnOpen":false,
    "ignore": [
        "**/.vscode/**",#.vscode/
        "**/.git/**",
        "**/.DS_Store",
        "**/models/**",
        "**/models_taitan4_2/**",
        "**/models_taitan4/**",
        "**/models_Alisure/**",
        "**/output/**",
        "**/logs/**",
        "**/data/**",
        "**/lib/build/**",#"**/build/**", build, "*/build/*"
        "**/lib/dist/**",
        "**/lib/faster_rcnn.egg-info/**",
        "test"#无论哪一深度的test都不会 同步等同于"**/data  axxx/** 作用在于穿文件夹但内容不穿
    ],
    "watcher": {
        "files": "*",
        "autoUpload": false,
        "autoDelete": false
    }
}
```



```
{
    "name": "my_sftp",
    "protocol": "sftp",
    "port": 22,
    "uploadOnSave": true,
    "downloadOnOpen":false,
    "context": "/mnt/4T/hzh/One-Shot-Object-Detection",
    "ignore": [
        ".vscode",
        ".git",
        ".DS_Store",
        "node_modules",
        "dist" ,
        "**/.vscode/**",
        "**/.git/**",
        "**/.DS_Store",
        "**/models/**",
        "**/models_taitan4_2/**",
        "**/models_taitan4/**",
        "**/models_Alisure/**",
        "**/output/**",
        "**/logs/**",
        "**/data/**",
        "**/lib/build/**",
        "**/lib/dist/**",
        "**/lib/faster_rcnn.egg-info/**"
    ],
    "watcher": {
        "files": "*",
        "autoUpload": false,
        "autoDelete": false
    },
    "profiles" : {
        "server_name1": {
            "name": "alisure1",
            "username": "ubuntu",
            "host": "10.170.15.237",
            "password": "asdfg",
            "remotePath": "/media/ubuntu/4T/hzh/lj/One-Shot-Object-Detection-main/" 
        },
        "server_name2": {
            "name": "out21080",
            "username": "ubuntu",
            "host": "10.170.21.105",
            "password": "asdfg",
            "remotePath": "/home/ubuntu/Dataset/Partition1/hzh/lj/One-Shot-Object-Detection-main/"
        }
    }
}

http://www.javashuo.com/article/p-ztwbyexy-bt.html
```
