现在我们本地和远程均有一个文件夹“sftpFolder”，用VsCode打开本地文件夹“sftpFolder”，然后执行 ctrl+shift+p ，搜索 SFTP:Config ，回车后，会生成一个“.vscode/sftp.json”，这个就是配置文件。
同时，如下图左侧会多了一个“远程目录”。


https://github.com/liximomo/vscode-sftp

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

