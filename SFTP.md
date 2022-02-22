现在我们本地和远程均有一个文件夹“sftpFolder”，用VsCode打开本地文件夹“sftpFolder”，然后执行 ctrl+shift+p ，搜索 SFTP:Config ，回车后，会生成一个“.vscode/sftp.json”，这个就是配置文件。
同时，如下图左侧会多了一个“远程目录”。


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
