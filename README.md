# Installation




plug-in
```python
Git Graph和GitLens
python snippets
python preview
better comments
Bracket Pair Colorizer
indent-rainbow
Code Translate
_Markdown All in One_
All you need to write Markdown (keyboard shortcuts, table of contents, auto preview and more)
Markdown Editor  What You See Is What You Get (WYSIWYG)
icons
markdownlint 语法提示

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
```
五、VSCode的常用快捷键及特殊按法
VS Code的常用快捷键如下,熟练运用，提高效率：

1. 编辑器与窗口管理
Ctrl + Shift + P: 打开命令面板。
Ctrl + Shift + N: 新建窗口。
Ctrl + Shift + W: 关闭窗口。
切分窗口：Ctrl + 1 / Ctrl + 2 / Ctrl + 3
Ctrl + H：最小化窗口
Ctrl + B：显示/隐藏侧边栏
Ctrl + +：放大界面
Ctrl + -：缩小界面

2. 文件操作
Ctrl + N：新建文件
Ctrl + W：关闭文件
Ctrl + Tab：文件切换

3. 格式调整
Ctrl +C / Ctrl + V：复制或剪切当前行/当前选中内容
Alt + Up / Down：向上/下移动一行
Shift + Alt + Up / Down：向上/下复制一行
Ctrl+Delete：删除当前行
Shift + Alt + Left / Right：从光标开始向左/右选择内容

4. 代码编辑
Ctrl + D：选中下一个相同内容
Ctrl + Shift + L：选中所有相同内容
Ctrl + F：查找内容
Ctrl + Shift + F：在整个文件夹中查找内容

大家在读取资料时，可能会发现除了 ctrl + shift + p这类常规的快捷键之外，VS Code还有几类快捷键的按法设置会比较奇怪。

通常的快捷键按法，比如 ctrl + shift + p：一起按下 ctrl ，shift 和 p 键，调出命令帮助菜单

第一种，ctrl + k z：这种快捷键首先需要按下 ctrl 和 k，然后松开按下 z，可以切换 禅模式

第二种，ctrl + k ctrl + o：这种快捷键需要按下 ctrl 和 k，然后 ctrl 不放，松开 k 并按下 o，可以打开文件夹

虽然按VS Code这样设计，可以使快捷键更加丰富，但是对于新手来说无疑是增加了快捷键的上手难度，我们可以根据自己的习惯，通过 ctrl + k ctrl + s 可以自定义快捷键，修改快捷键的设置。

```
