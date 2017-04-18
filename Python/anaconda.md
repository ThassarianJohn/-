# Anaconda

Anaconda是一个用于科学计算的Python发行版。

Anaconda windows版的安装非常简单，从官网上下载安装包并安装即可。

conda是它的常用可执行命令工具，其核心功能是**包管理**与**环境管理**。

## Conda的环境管理

这里我们以一个名为python34的环境为例，进行相关操作

指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）

* 创建环境

```cmd
conda create --name python34 python=3.4
```

* 激活环境

```cmd
activate python34
```

* 退出环境

```cmd
deactivate python34
```

* 删除环境

```cmd
conda remove --name python34 --all
```

* 查看已安装的环境

```cmd
conda info -e
```

## Conda的包管理

* 查看当前环境下已安装的包

```cmd
conda list
```

* 查看某个指定环境的已安装包

```cmd
conda list -n python34
```

* 查找package信息

```cmd
conda search numpy
```

* 给某个指定环境安装package

```cmd
conda install -n python34 numpy
```

*如果不用-n指定环境名称，则被安装在当前活跃环境*

*也可以通过-c指定通过某个channel安装*

* 更新package

```cmd
conda update -n python34 numpy
```

* 删除package

```cmd
conda remove -n python34 numpy
```

**补充**：

新建的环境只安装了指定的包，如果希望像默认环境那样，需安装anaconda集合包。

* 在当前环境下安装anaconda包集合

```cmd
conda install anaconda
```

* 结合创建环境的命令，以上操作可以合并为

```cmd
conda create -n python34 python=3.4 anaconda
```

*也可以不用全部安装，根据需求安装自己需要的package即可*

## 设置国内镜像

因为Anaconda.org的服务器在国外，conda下载的速度可能会很慢。

所幸的是，清华TUNA镜像源有Anaconda仓库的镜像，我们将其加入conda的配置即可：

```cmd
# 添加Anaconda的TUNA镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

# TUNA的help中镜像地址加有引号，需要去掉
 
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```

## 参考资料

[Anaconda使用总结](http://python.jobbole.com/86236/)
