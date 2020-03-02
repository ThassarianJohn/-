# TensorFlow

[TensorFlow-Github](https://github.com/tensorflow/tensorflow)

TensorFlow是一个使用数据流图进行数值计算的开源软件库。

图中的节点代表数学运算，而图中的边则表示在这些节点间流动（flow）的多维数组数据（tensors）。

这种灵活的架构，使你可以将它部署到拥有一个或多个CPU或GPU的桌面PC、服务器或移动设备上，而无需重写代码。

TensorFlow还包括数据可视化工具包tensorboard。

TensorFlow项目最初是由，来自谷歌机器智能研究组织谷歌大脑研究团队的研究人员和工程师，为了实现

机器学习与深层神经网络而进行的研究。

该系统通用性极强，足以适用于各种各样的其他领域。

## 安装

安装的步骤在官网上有详细的介绍。由于网络的原因，目前TensorFlow的官网必须通过科学上网才能够访问。

这里简单介绍下基于anaconda的开发环境安装流程。

```
我的环境配置
操作系统：windows 10
CPU    ：AMD 64位
Python ：Anaconda4.8.2 python3.6.8
```

* 创建tensorflow环境

```cmd
conda create -n tf python=3.5 anaconda
```

* 激活tensorflow环境

```cmd
activate tf
```

* 安装tensorflow

```cmd
conda install -c conda-forge tensorflow
```

* 或者用pip安装

```cmd
pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow-1.0.0-cp35-cp35m-win_amd64.whl
```

注意，此处的包路径，以及包名，应当根据具体情况填写。

- 最后确认安装

  - 打开一个命令行

  - 激活 tf 环境：activate tf

  - 创建一个测试文件 "test.py"

  - 执行测试文件：python test.py

  - 打印 'Hello, TensorFlow!'，测试通过

```py
# test.py
import tensorflow as tf

hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(hello))
```

- 查看当前 tensorflow 版本

  - 输入python打开命令行控制台

  - 加载 tensorflow 模块		：import tensorflow as tf

  - 打印当前 tensorflow 版本	：```print(tf.__version__)```


- 更新 tensorflow 版本

```cmd
conda update tensorflow
```

