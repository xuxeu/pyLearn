# 虚拟环境Python

[TOC]

确保pip可用：

```python
$ pip --version
```

如果您使用 [python.org](https://python.org) 或 [Homebrew](https://brew.sh) 的安装程序来安装 Python，您应该已经有 pip 了。 如果您使用的是Linux，并使用操作系统的包管理器进行安装，则可能需要单独 [安装 pip](https://pip.pypa.io/en/stable/installing/)。

### 安装pipenv

pipenv是Python项目的依赖管理器。如果您熟悉node.js的npm或ruby的bunder，那么他们在思路上与这些工具类似。尽管pip可以安装Python包，但仍推荐使用pipenv，因为它是一种更高级的工具，可简化依赖关系管理的常见使用情况。

```python
$ pip install --user pipenv
```

### 为你的项目安装包

pipenv管理每一个项目的依赖关系，要安装包时，请更改到您的项目目录，并运行：

```python
$ cd myproject
$ pipenv install requests
```

pipenv将在你的项目目录中安装一个超赞的requests库，并为你创建一个pipfile。pipfile用于跟踪你的项目中需要重新安装的依赖。例如在与他人共享项目时。您应该得到类似的输出(尽管显示的确切路径会有所不同)：

```python
Creating a Pipfile for this project...
Creating a virtualenv for this project...
Using base prefix '/usr/local/Cellar/python3/3.6.2/Frameworks/Python.framework/Versions/3.6'
New python executable in ~/.local/share/virtualenvs/tmp-agwWamBd/bin/python3.6
Also creating executable in ~/.local/share/virtualenvs/tmp-agwWamBd/bin/python
Installing setuptools, pip, wheel...done.

Virtualenv location: ~/.local/share/virtualenvs/tmp-agwWamBd
Installing requests...
Collecting requests
  Using cached requests-2.18.4-py2.py3-none-any.whl
Collecting idna<2.7,>=2.5 (from requests)
  Using cached idna-2.6-py2.py3-none-any.whl
Collecting urllib3<1.23,>=1.21.1 (from requests)
  Using cached urllib3-1.22-py2.py3-none-any.whl
Collecting chardet<3.1.0,>=3.0.2 (from requests)
  Using cached chardet-3.0.4-py2.py3-none-any.whl
Collecting certifi>=2017.4.17 (from requests)
  Using cached certifi-2017.7.27.1-py2.py3-none-any.whl
Installing collected packages: idna, urllib3, chardet, certifi, requests
Successfully installed certifi-2017.7.27.1 chardet-3.0.4 idna-2.6 requests-2.18.4 urllib3-1.22

Adding requests to Pipfile's [packages]...
P.S. You have excellent taste! ✨ 🍰 ✨
```

#### 使用安装好的库

现在安装了requests库，可以创建一个简单的main.py文件来使用它：

```python
import requests
response = requests.get('https://httpbin.org/ip')
print('Your IP is {0}'.format(response.json()['origin']))
```

然后你就可以使用pipenv run运行这段脚本：

```python
pipenv run python main.py
```

你应该获取到类似的输出：

```python
your IP is 8.8.8.8
```

使用`pipenv run`可确保你的安装包可用于你的脚本。我们还可以生成一个新的shell，确保所有的命令都可以使用`pipenv shell`访问已安装的包。

### 更低层次：virtualenv

virtualenv是一个创建隔绝的Python环境的工具。virtualenv创建一个包含所有必要的可执行文件的文件夹，用来使用Python工程所需要的包。

他可以独立使用，代替pipenv！

```python
$ pip install virtualenv
```

测试你的安装：

```python
virtualenv --version
```

#### 基本安装

为一个工程创建一个虚拟环境：

```python
$ cd my_project_folder
$ virtualenv my_project
```

`virtualenv my_project`将会在当前的目录中创建一个文件夹，包含了Python可执行文件，以及pip库的一份拷贝，这样就能安装其他包了。虚拟环境的名字（此例中是my_project）可以是任意的；若省略将会把文件均放在当前目录。

在任何你运行命令的目录中，这会创建Python的拷贝，并将之放在叫做my_project的文件中。

您可以选择使用一个Python解释器（比如python3.7）

