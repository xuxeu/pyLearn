# 正确的安装Python

通常来说，您所使用的操作系统自带安装好的Python。

如此可以省却自己安装、配置Python的过程。话虽如此，我还是强烈建议各位，在正式开始Python应用开发前，安装接下来教程中所介绍的工具和库。特别要提到如setuptools，pip和virtualenv这样的工具----它们将简化安装和使用Python第三方库的流程。

对于Windows安装，记得把默认使用的Python版本加到PATH环境变量中，避免每次使用时都要冗余地写全Python解释器路径。假设安装路径是`C:\Python37\;C:\Python37\Scripts`。

第二个路径Scripts可接收已安装包的命令文件，添加这个路径很有益处。虽然以上步骤完成后，就可以开始正式使用Python了，但我还是强烈建议各位，在正式开始Python应用开发前，安装接下来教程中所介绍的工具和库。特别应该安装setuptools，她将简化安装和使用Python第三方库的流程。

### setuptools+pip

`setuptools+pip`是最重要的两个第三方Python包。

安装完成以后，您可以使用单个命令下载、安装和卸载任何兼容的Python应用包。还可以轻松地这种网络安装的方式加入到自己开发的Python应用中。

所有受支持的Python3版本都包含pip，因此请确保它是最新的：

```
python -m pip install -U pip
```

### pipenv&虚拟环境

下一步安装pipenv，然后就可以安装依赖关系并管理虚拟环境。

虚拟环境工具通过为不同项目创建专属的Python虚拟环境，以实现其依赖的库独立保存在不同的路径。这解决了“项目X依赖于1.x版本，但项目Y需要4.x”的难题，并且维持全局的site packages目录干净、易管理。



