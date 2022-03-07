# Installation
安装遇到的软件或者框架

plug-in
```
python snippets
python preview
better comments
Bracket Pair Colorizer
indent-rainbow
Code Translate
_Markdown All in One_
All you need to write Markdown (keyboard shortcuts, table of contents, auto preview and more)


#  ! 红色的高亮注释
# ? 蓝色的高亮注释
#  * 绿色的高亮注释
#  todo 橙色的高亮注释
```


[不使用插件，实现vscode中python文件头部注释和函数注释](https://blog.csdn.net/weixin_43876014/article/details/121124820?spm=1001.2101.3001.6650.3&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-3.pc_relevant_antiscan&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-3.pc_relevant_antiscan&utm_relevant_index=6)
```
1. 安装插件Python Docstring Generator
在vscode左侧extension里面输入autoDocstring,找到Python Docstring Generator，点击安装。

2. 配置Docstring Format以及快捷键
（1） 按以下路径：File —> Preferences —> Settings，找到配置参数的地方；
（2） 在搜索栏输入 autoDocstring，找到 Auto Docstring: Docstring Format；
（3） 选中要用的格式，其中 sphinx 和 pycharm的reStructuredText有些像；
（4） 注意 Auto Docstring: Quote Style 里面可以设置用双引号（""" “”"）还是单引号(’’’ ‘’’)来触发autoDocstring
```
```


"better-comments.tags": [  {    "tag": "!",    "color": "#FF2D00",    "strikethrough": false,    "backgroundColor": "transparent"  },  {    "tag": "?",    "color": "#3498DB",    "strikethrough": false,    "backgroundColor": "transparent"  },  {    "tag": "//",    "color": "#474747",    "strikethrough": true,    "backgroundColor": "transparent"  },  {    "tag": "todo",    "color": "#FF8C00",    "strikethrough": false,    "backgroundColor": "transparent"  },  {    "tag": "*",    "color": "#98C379",    "strikethrough": false,    "backgroundColor": "transparent"  }]
```
