Anaconda
---

## 简介

Anaconda是一个用于科学计算的Python集成开发环境，它能够：

- 方便快捷地下载和管理7,500多 Python/R 数据科学软件包
- 使用 Conda管理软件库、软件依赖关系和开发环境

Anaconda包括[Conda](#Conda)、Anaconda-navigator、Spyder、ipython和Jupyter Notebook等工具，本文将重点介绍[Conda](#Conda)。

- [Conda](#Conda)：命令行开发环境管理与包管理工具
- Anaconda-navigator：图形化的开发环境管理与包管理工具


## 安装

Anaconda **windows版的安装**非常简单，从[官网](https://www.continuum.io/)上下载安装包并按步骤安装即可。

**centOS7下Anaconda安装步骤**：

安装bzip2：

```bash
$ yum install -y bzip2
```

到官网找到Linux版下载链接下载：

```bash
$ wget https://repo.anaconda.com/archive/Anaconda3-5.3.1-Linux-x86_64.sh
```

安装

```bash
$ bash Anaconda3-4.4.0-Linux-x86_64.sh
```

完成后，输入命令使系统路径立即生效：

```bash
$ source /root/.bashrc
```


## Conda

Conda是Anaconda的常用可执行命令工具，其核心功能是**包管理**与**环境管理**。


#### Conda的环境管理

这里我们以一个名为python34的环境为例，进行相关操作。

指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）

* 创建环境

```cmd
$ conda create --name python34 python=3.4
```

* 激活环境

```cmd
$ activate python34
```

* 退出环境

```cmd
$ deactivate python34
```

* 删除环境

```cmd
$ conda remove --name python34 --all
```

* 查看已安装的环境

```cmd
$ conda info -e
```


#### Conda的包管理

* 查看当前环境下已安装的包

```cmd
$ conda list
```

* 查看某个指定环境的已安装包

```cmd
$ conda list -n python34
```

* 查找package信息

```cmd
$ conda search numpy
```

* 给某个指定环境安装package

```cmd
$ conda install -n python34 numpy
```

*如果不用-n指定环境名称，则被安装在当前活跃环境*

*也可以通过-c指定通过某个channel安装*

* 更新package

```cmd
$ conda update -n python34 numpy
```

* 删除package

```cmd
$ conda remove -n python34 numpy
```

**补充**：

新建的环境只安装了指定的包，如果希望像默认环境那样，需安装anaconda集合包。

* 在当前环境下安装anaconda集合包

```cmd
$ conda install anaconda
```

* 结合创建环境的命令，以上操作可以合并为

```cmd
$ conda create -n python34 python=3.4 anaconda
```

*也可以不用全部安装，根据需求安装自己需要的package即可*


#### 用Conda升级Anaconda

用Conda升级Anaconda需要先升级conda

```
conda update conda
conda update anaconda
conda update anaconda-navigator
```


#### 为Conda设置国内镜像

因为Anaconda.org的服务器在国外，conda下载的速度可能会很慢。

所幸的是，清华TUNA镜像源有Anaconda仓库的镜像，我们将其加入conda的配置即可：

```cmd
# 添加Anaconda的TUNA镜像
$ conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

# TUNA的help中镜像地址加有引号，需要去掉
 
# 设置搜索时显示通道地址
$ conda config --set show_channel_urls yes
```


## 参考资料

- [Anaconda官网](https://www.anaconda.com/)
- [Anaconda使用总结](http://python.jobbole.com/86236/)
- [centos安装 Anaconda3及使用](http://www.cnblogs.com/xiao-apple36/p/9052102.html)
- [conda升级命令-升级conda、anaconda及各种包](https://blog.csdn.net/weixin_41481113/article/details/88410648)