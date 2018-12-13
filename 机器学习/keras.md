# Keras

[Keras官网](https://keras.io/)

[Keras-github](https://github.com/fchollet/keras)

[Keras中文文档](http://keras-cn.readthedocs.io/en/latest/)

## 开发环境搭建

- 安装[anaconda](/大数据分析/机器学习/Anaconda.md)开发环境

- 安装[tensorflow](/大数据分析/机器学习/TensorFlow.md)环境

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

 * 打开一个命令行

 * 激活tensorflow环境：activate tf

 * 输入python打开命令行控制台

 * 执行：from keras.models import Sequential

 * 正常加载，则测试通过

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
- **度量值列表([metrics](https://keras.io/metrics/))**：对于任何的聚类问题你将要把它设置为metrics=[‘accuracy’]，一个度量值可以是一个已存在的度量的字符串标识符或者是一个自定义度量函数。

**optimizers**优化器

**loss**损失函数

**mse**:mean_squared_error，均方差，常用的目标函数，公式为((y_pred-y_true)**2).mean()

**mae**:mean_absolute_error，绝对值均差，公式为(|y_pred-y_true|).mean()

**mape**:mean_absolute_percentage_error，绝对值均差百分比， 公式为：(|(y_true - y_pred) / clip((|y_true|),epsilon, infinite)|).mean(axis=-1) * 100，和mae的区别就是，累加的是（预测值与实际值的差）除以（剔除不介于epsilon和infinite之间的实际值)，然后求均值。

**msle**:mean_squared_logarithmic_error，均方差对数，公式为： (log(clip(y_pred, epsilon, infinite)+1)- log(clip(y_true, epsilon,infinite)+1.))^2.mean(axis=-1)，这个就是加入了log对数，剔除不介于epsilon和infinite之间的预测值与实际值之后，然后取对数，作差，平方，累加求均值。

squared_hinge 公式为：(max(1-y_true*y_pred,0))^2.mean(axis=-1)，取1减去预测值与实际值乘积的结果与0比相对大的值的平方的累加均值。

hinge 公式为：(max(1-y_true*y_pred,0)).mean(axis=-1)，取1减去预测值与实际值乘积的结果与0比相对大的值的的累加均值。

binary_crossentropy: 常说的逻辑回归, 就是常用的交叉熵函数

categorical_crossentropy: 多分类的逻辑， 交叉熵函数的一种变形吧，没看太明白

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

[Keras中文文档](http://keras-cn.readthedocs.io/en/latest/)

[Keras 时序模型](http://blog.csdn.net/thinking_boy1992/article/details/53207177)
