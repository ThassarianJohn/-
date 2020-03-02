# Keras

- [神经网络](/机器学习/keras神经网络.md)
	- [网络层](/机器学习/keras网络层.md)
	- [激活函数](/机器学习/keras激活函数.md)
- [编译]()
	- [优化器](/机器学习/keras优化器.md)
	- [损失函数](/机器学习/keras损失函数.md)
	- [评估标准](/机器学习/keras评估标准.md)
- [训练]()

## 开发环境搭建

- 安装[anaconda](/Python/anaconda.md)集成开发环境

- 安装[tensorflow](/机器学习/tensorflow.md)环境

```cmd
conda install -c conda-forge tensorflow
```

- 安装keras

```cmd
conda install -c conda-forge keras
```

- 修改后台配置

在 **C:\Users\用户名** 路径下 有一个 **.keras** 文件夹 

修改 keras.json 文件

用theano的话，keras.json写入

```json
{
    "image_dim_ordering": "th", 
    "epsilon": 1e-07, 
    "floatx": "float32", 
    "backend": "theano"
}
```

用tensorflow的话，keras.json写入

```json
{
    "image_dim_ordering": "tf", 
    "epsilon": 1e-07, 
    "floatx": "float32", 
    "backend": "tensorflow"
}
```

- 最后确认安装

	- 打开一个命令行

	- 激活tensorflow环境：activate tf

	- 输入python打开命令行控制台

	- 执行：from keras.models import Sequential

	- 正常加载，则测试通过


- 查看当前 keras 版本

	- 输入"python"打开命令行控制台

	- 加载 keras 模块	：import keras

	- 打印当前 keras 版本	：```print(keras.__version__)```

- 更新 keras 版本

```cmd
conda update keras
```


```
环境搭建完成后，Anaconda的开始菜单目录下会多出一些对应环境配置的工具。
可以使用Spyder工具进行开发和调试。
当然也可以继续用我们熟悉的Sublime Text。
```


## 基本介绍

创建Sequential模型对象

```python
from keras.models import Sequential

model = Sequential()
```

通过.add()为模型添加网络层

```python
from keras.layers.core import Dense, Activation

model.add(Dense(output_dim=64, input_dim=100))
model.add(Activation("relu"))
model.add(Dense(output_dim=10))
model.add(Activation("softmax"))
```

完成模型的搭建后，使用.compile()方法编译模型

```python
model.compile(loss='categorical_crossentropy', optimizer='sgd', metrics=['accuracy'])
```

完成模型编译后，我们在训练数据上进行一定次数的迭代训练，以拟合网络

```python
model.fit(X_train, Y_train, nb_epoch=5, batch_size=32)
```

或者手动输入数据训练

```python
model.train_on_batch(X_batch, Y_batch)
```

然后，我们可以用一些测试数据对训练后模型进行评估

```python
X_test = [[1,1],[0,100]]
Y_test = [[2],[100]]

score = model.evaluate(X_test, Y_test, verbose=1)
```

最后，我们可以使用我们的模型，对新的数据进行预测

```python
Y_test = model.predict(X_test, batch_size=32)
```

## 详细教程

#### 创建模型

简单的模型通过Sequential 实例和合并层实现。

对于不能通过Sequential和Merge进行表示的复杂模型可以使用 [the functional API](https://keras.io/getting-started/functional-api-guide/) 。

#### 编译

在训练一个模型之前，需要配置它的学习过程，这是通过compile函数来做的。

它接受三个参数：

- **优化器([optimizers](https://keras.io/optimizers/))**：它可以是现有的优化器的字符串标识符（例如 rmsprop 或者 adagrad），也可以是优化器类的实例；
- **损失函数([losses](https://keras.io/losses/))**：这是模型想要最小化的目标函数，它可以是一个现存的损失函数的字符串标识符(比如 categorical_crossentropy 或者 mse)，也可以是一个目标函数；
- **度量值列表([metrics](https://keras.io/metrics/))**：对于任何的聚类问题你将要把它设置为metrics=['accuracy']，一个度量值可以是一个已存在的度量的字符串标识符或者是一个自定义度量函数。


#### 训练

**训练结果**

loss，训练损失

val_loss，验证损失，你用的测试数据，val_loss就是测试损失


#### 模型的保存与加载

```python
model.save('my_model.h5')
```

```python
from keras.models import load_model

model = load_model('my_model.h5')
```


## 参考资料

- [Keras官网](https://keras.io/)
- [Keras-github](https://github.com/fchollet/keras)
- [Keras 中文文档](http://keras-cn.readthedocs.io/en/latest/)
- [Keras 时序模型](http://blog.csdn.net/thinking_boy1992/article/details/53207177)
- [keras 快速搭建神经网络系列视频——莫烦](https://morvanzhou.github.io/tutorials/machine-learning/keras/)