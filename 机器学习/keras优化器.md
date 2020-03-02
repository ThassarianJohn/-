# 优化器optimizers

优化器是编译Keras模型必要的两个参数之一

```python
model = Sequential()
model.add(Dense(64, init='uniform', input_dim=10))
model.add(Activation('tanh'))
model.add(Activation('softmax'))

sgd = SGD(lr=0.01, decay=1e-6, momentum=0.9, nesterov=True)
model.compile(loss='mean_squared_error', optimizer=sgd)
```

可以在调用model.compile()之前初始化一个优化器对象，然后传入该函数（如上所示），也可以在调用model.compile()时传递一个预定义优化器名。在后者情形下，优化器的参数将使用默认值。

```python
# pass optimizer by name: default parameters will be used
model.compile(loss='mean_squared_error', optimizer='sgd')
```




## 所有优化器都可用的参数

参数 clipnorm 和 clipvalue 是所有优化器都可以使用的参数，用于控制梯度下降：

```python
from keras import optimizers

# all parameter gradients will be clipped to
# a maximum norm of 1.
sgd = SGD(lr=0.01, clipnorm=1.)
```

```python
from keras import optimizers

# all parameter gradients will be clipped to
# a maximum value of 0.5 and
# a minimum value of -0.5.
sgd = SGD(lr=0.01, clipvalue=0.5)
```


## [SGD](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L164)

```python
keras.optimizers.SGD(lr=0.01, momentum=0.0, nesterov=False)
```

随机梯度下降法，支持动量参数，支持学习衰减率，支持Nesterov动量

参数

- lr      ：float >= 0，学习率
- momentum：float >= 0，动量参数
- nesterov：boolean   ，确定是否使用Nesterov动量


## [RMSprop](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L229)

```python
keras.optimizers.RMSprop(lr=0.001, rho=0.9)
```

除学习率可自由调整外，建议保持优化器的其他默认参数不变

该优化器通常是面对递归神经网络时的一个良好选择

参数

- lr ：float >= 0，学习率
- rho：float >= 0

#### 参考资料

- [rmsprop: Divide the gradient by a running average of its recent magnitude](lecture_slides_lec6.pdf)


## [Adagrad](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L303)

```python
keras.optimizers.Adagrad(lr=0.01)
```

建议保持优化器的默认参数不变

参数

- lr     ：float >= 0，初始学习率


#### 参考资料

- [Adaptive Subgradient Methods for Online Learning and Stochastic Optimization](duchi11a.pdf)


## [Adadelta](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L376)

```python
keras.optimizers.Adadelta(lr=1.0, rho=0.95)
```

建议保持优化器的默认参数不变

参数

- lr ：float >= 0，学习率
- rho：float >= 0

#### 参考资料

- [Adadelta - an adaptive learning rate method](https://arxiv.org/abs/1212.5701)


## [Adam](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L467)

```python
keras.optimizers.Adam(learning_rate=0.001, beta_1=0.9, beta_2=0.999, amsgrad=False)
```

该优化器的默认值来源于参考文献

参数

- lr  ：float >= 0，学习率
- beta_1：float， 0<beta<1，通常很接近1
- beta_2：float， 0<beta<1，通常很接近1
- amsgrad: boolean.

#### 参考资料

- [Adam - A Method for Stochastic Optimization](https://arxiv.org/abs/1412.6980v8)
- [On the Convergence of Adam and Beyond](on_the_convergence_of_adam_and_beyond.pdf)


## [Adamax](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L567)

```python
keras.optimizers.Adamax(lr=0.002, beta_1=0.9, beta_2=0.999)
```

Adamax优化器来自于Adam的论文的Section7，该方法是基于无穷范数的Adam方法的变体。

默认参数由论文提供

参数

- lr  ：float >= 0，学习率
- beta_1：float， 0<beta<1，通常很接近1
- beta_2：float， 0<beta<1，通常很接近1

#### 参考资料

- [Adam - A Method for Stochastic Optimization](https://arxiv.org/abs/1412.6980v8)


## [Nadam](https://github.com/keras-team/keras/blob/master/keras/optimizers.py#L645)

```python
keras.optimizers.Nadam(lr=0.002, beta_1=0.9, beta_2=0.999)
```

Nadam优化器，即Nesterov Adam optimizer: Adam本质上像是带有动量项的RMSprop，Nadam就是带有Nesterov 动量的Adam RMSprop

默认参数来自于论文，推荐不要对默认参数进行更改。

参数

- lr：大于0的浮点数，学习率
- beta_1：float， 0<beta<1，通常很接近1
- beta_2：float， 0<beta<1，通常很接近1

#### 参考资料

- [Nadam report](054_report.pdf)
- [On the importance of initialization and momentum in deep learning](momentum.pdf)


## 参考资料

- [Optimizers](https://keras.io/optimizers/)

