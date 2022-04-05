参考地址：
[csdn](https://blog.csdn.net/yifengchaoran/article/details/113447773)
[知乎](https://www.zhihu.com/search?type=content&q=%E5%A6%82%E4%BD%95%E5%B0%86%E8%87%AA%E5%B7%B1%E7%9A%84%E5%8C%85%E4%B8%8A%E4%BC%A0%E5%88%B0PyPi%E5%B9%B6%E5%8F%AF%E9%80%9A%E8%BF%87pip%E5%AE%89%E8%A3%85)

# 一、创建包
## 1.1 包概念简述
```
Python语言如其他编程语言，讲求代码最大化复用，函数和类是最初级的复用，模块（本质是一个py文件）是更高一级的复用，而包（本质是包含py文件且包含一个__init__.py文件的文件夹）则是最高程度的复用，一般情况下，一个包会包含一种完成的解决方案，比如scrapy，其中包含了完整的爬虫解决方案。
```
此处只是简单介绍以上概念，详细的可以通过学习基础Python知识获得。
## 1.2 创建包结构
通常意义上的包结构如下：
```
example_package
----example_pkg
    ----__init__.py
```
其中，example_package和example_pkg均为一个文件夹，而__init__.py则为文件夹example_pkg内的一个py文件，该文件为包的标示，是必须有的，可以为空，至于__init__.py文件的作用，此处不进行介绍

当然包可以有多层结构，比如下面的结构：
## 1.3 本地使用
一般在日常使用python时，可将处理关联性较高的代码和模块，包含到一个包内，比如下面的包，即包含了处理媒体相关的模块
```
media
----__init__.py
----video
    ----__init__.py
    ----volume.py     #包含处理声音相关函数等
    ----convert.py    #包含转码相关功能
    ----combine.py    #包含视频合成相关
----audio
    ----__init__.py
    ----convert.py    #包含转码相关功能
    ----compile.py    #包含编译相关功能
```
然后将以上包移动到python的根site_packages文件夹内，或者指定虚拟环境内的site_packages内，然后就可以直接使用import导入以上包或者指定模块，python会按照包和模块搜索路径完成加载

一般日常中，我们基本达到这个程度，不过，如果自己感觉自己维护的包足够优秀，或者在解决特定领域问题时，足够强大且性能优异，可上传到PyPi并与他人共享，说不定自己的包后面很有可能成为python后续版本内的buildin模块。
# 二、上传前准备
## 2.1 完善包相关信息
我们接着使用example项目举例，需要在该文件夹内创建以下文件，以为接下来创建可供分发的文件做准备
```
example_package
----LICENSE.txt    #版权声明文件
----README.md      #分发包的详细介绍文件
----example_pkg
    ----__init__.py
----setup.py       #为打包做准备的设置文件
----tests          #测试文件夹，一般用不到
```
### 2.1.2 setup.py简述
setip.py文件相对比较关键，一般在该文件内约定此次分发的包的版本号、名称、作者、联系方式、项目地址、python版本要求等信息，其文件内最基本的主信息如下：
```
import setuptools #导入setuptools打包工具
 
with open("README.md", "r", encoding="utf-8") as fh:
    long_description = fh.read()
 
setuptools.setup(
    name="example-pkg-YOUR-USERNAME", # 用自己的名替换其中的YOUR_USERNAME_
    version="0.0.1",    #包版本号，便于维护版本
    author="Example Author",    #作者，可以写自己的姓名
    author_email="author@example.com",    #作者联系方式，可写自己的邮箱地址
    description="A small example package",#包的简述
    long_description=long_description,    #包的详细介绍，一般在README.md文件内
    long_description_content_type="text/markdown",
    url="https://github.com/pypa/sampleproject",    #自己项目地址，比如github的项目地址
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.6',    #对python的最低版本要求
)
```
### 2.1.3 README.md文件简述
README.md文件主要是用来对此次发行的包的详细说明，包括用法和注意事项等

# Example Package
#在此文件内，可使用markdown撰写对包的详细介绍和说明，便于别人熟悉和使用，在此不再赘述
This is a simple example package. You can use
[Github-flavored Markdown](https://guides.github.com/features/mastering-markdown/)
to write your content

### 2.1.4 LICENSE文件简述
版权声明文件，一般告诉使用者可以在什么场景下使用，如果想详细了解，可访问 ```https://choosealicense.com``` 进行了解，此处不再详细展开，一般直接将以下文案复制至文件内即可
```
Copyright (c) 2021 The Python Packaging Authority
 
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
 
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
 
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
Copyright (c) 2021 The Python Packaging Authority
 
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
 
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
 
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
## 2.2 创建可供分发的包
### 2.2.1 安装或更新setuptools 和wheel
一般使用setuptools和wheel工具打包生成可上传和分发，并可使用pip安装的包文件
#安装或更新setuotools和wheel
```
python3 -m pip install  --upgrade setuptools wheel
```
### 2.2.2 打包并生成tar.gz和whl文件
然后，在终端或cmd命令窗，将当前路径cd到setup.py文件所在文件夹，并正式打包
#以mac为例
```
cd example_packages/example_pkg
```
#运行以下命令
```
python setup.py sdist bdist_wheel
```
运行完毕后，如果顺利，则会在与setup.py文件同一层级，产生一个dist文件夹，此时文件夹结构如下：
```
example_package
----LICENSE.txt    #版权声明文件
----README.md      #分发包的详细介绍文件
----example_pkg
    ----__init__.py
----setup.py       #为打包做准备的设置文件
----tests          #测试文件夹，一般用不到
----dist
```
该文件夹内会包含whl和tar.gz类型文件，此时，其实可以直接将该文件转发给朋友，朋友保存到本地，就可通过pip进行安装，不过这样还没达到我们的目的。
# 三、上传包至PyPi
## 3.1 使用PyPi测试环境先熟悉上传步骤
PyPi为了便于大家练习上传过程，所以还同步提供了功能与PyPi完全一样但相互隔离的测试环境，一般通过twine包将以上打包好的文件上传至PyPi

在这之前，大家需要首先注册一个test环境的PyPi账号，可通过链接 https://test.pypi.org/account/register/ 进行注册。

然后大家需要在我的→account setting处设置自己用API上传时使用的token信息，工作原理类似git hub，快速传送门 https://test.pypi.org/manage/account/#api-tokens。

好了，一切准备就绪

### 3.1.1 安装twine
首先使用以下命令安装或更新twine
python -m pip install --user --upgrade twine
### 3.1.2 使用twine上传
此处，我们将dist下的分发文件，先上传到PyPi的测试环境，上传完毕后，可以在测试环境的PyPi自己的主页，your projects处查看并管理（包括版本信息等，一般就是setup.py文件内设置的信息）

注意，在终端或cmd窗内运行以下命令时，均需保证当前文件夹路径与setpy.py一致

python -m twine upload --repository testpypi dist/*
当运行以上命令后，一般会出现Enter your username和Enter your password提示，其中username输入__token__，password输入token值（使用测试环境的token值），然后按Enter即可

## 3.2 正式上传至PyPi
当在测试环境上传成功后，便可上传至PyPi的生产环境

python -m twine upload dist/*
当运行以上命令后，一般会出现Enter your username和Enter your password提示，其中username输入__token__，password输入token值（使用正式环境的token值），然后按Enter即可

到此，大功告成，接下来，便可直接用pip进行安装了

# 四、使用pip安装测试
## 4.1 安装PyPi测试环境的包
运行以下命令，则会从PyPi测试环境下载并安装上传的分发包

python3 -m pip install --index-url https://test.pypi.org/simple/ --no-deps example-pkg-YOUR-USERNAME #其中 example-pkg-YOUR-USERNAME 即自己指定的包名
## 4.2 安装PyPi正式环境的包
pip install example-pkg-YOUR-USERNAME
# 五、包版本更新
后续，如果需要对自己的包发布新版本，照以上步骤完成即可，别忘了修改setup.py文件内的版本号信息
在[这里](https://test.pypi.org/project/example-pkg-your-username/)检查你的包是否上test.pypi成功。
# 六、
官方教程 https://packaging.python.org/tutorials/packaging-projects/
classifiers 格式规范 https://pypi.org/classifiers/

code step

#安装或更新setuotools和wheel

python -m pip install  --upgrade setuptools wheel
cd example_packages/example_pkg 打包
#运行以下命令

1、python setup.py sdist bdist_wheel  产生dist文件夹 所包含.whl .tar.gz 文件至此可以完成本地pip安装 打包至whl

pip install twine(python3 -m pip install --user --upgrade twine)

2、python -m twine upload --repository testpypi dist/*  上传到PyPi的测试环境

python -m twine upload dist/* 正式上传

3、上传 

https://test.pypi.org/

https://test.pypi.org/account/register/ 进行注册
然后大家需要在我的→account setting处设置自己用API上传时使用的token信息（名字随便起），创建成功后会返给一串密匙用来之后上传时登入，工作原理类似git hub，快速传送门 https://test.pypi.org/manage/account/#api-tokens。
问题
NOTE: Try --verbose to see response content.
HTTPError: 403 Forbidden from https://upload.pypi.org/legacy/
Invalid or non-existent authentication information. See https://pypi.org/help/#invalid-auth for more information.


参考https://packaging.python.org/specifications/pypirc/  最新格式，在你的本地电脑根目录创建~/.pypirc
more question 参考(https://segmentfault.com/a/1190000008663126)


https://packaging.python.org/guides/using-testpypi/

问题
NOTE: Try --verbose to see response content.
HTTPError: 400 Bad Request from https://test.pypi.org/legacy/
This filename has already been used, use a different version. See https://test.pypi.org/help/#file-name-reuse for more information.
删除dist文件夹内旧版本内容即可



[distutils]
  2 index-servers =
  3     pypi
  4     testpypi
  5 
  6 [pypi]
  7 repository = https://upload.pypi.org/legacy/
  8 
  9 [testpypi]
 10 repository = https://test.pypi.org/legacy/
 11 username =__token__
 12 password =pypi-AgENdGVzdC5weXBpLm9yZwIkOTFhMmM1ZTgtYmYyMS00ZmFhLWI0ZDItMmU0YjZkODkxNTQ3AAIleyJwZXJtaXNzaW9ucyI6ICJ1c2VyIiwgInZlcnNpb24iOiAxfQAABiA8lkrqlsLke5oFkOnavW0ZMekC6_KbSMyBR3KN    FQ8eOw

 起到免密码的作用


 导入的问题
 from impport 
 如果不显示有可能是vscode 问题再次重启即可
 import 导入的一定是class 对象
 __int__.py存在的文件夹都会当成包了来导入
 可以有多个 每个代码目录下都要有，最外面的名字可以不是harzvatool 因为里面可以变 
 from 导入的也是内层的pkg

python setup.py build develop
python setup.py install 
python setup.py develop

test failed: build/bdist.linux-x86_64/egg does not support .pth files error: bad install directory 
export PYTHONPATH="${PYTHONPATH}:/home/user1/lib/python3.7/site-packages/"
The command should be python setup.py develop, not python setup.py install develop