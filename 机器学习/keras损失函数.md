# 损失函数

## 常用损失函数

**mse**:mean_squared_error，均方差，常用的目标函数，公式为((y_pred-y_true)**2).mean()

**mae**:mean_absolute_error，绝对值均差，公式为(|y_pred-y_true|).mean()

**mape**:mean_absolute_percentage_error，绝对值均差百分比， 公式为：(|(y_true - y_pred) / clip((|y_true|),epsilon, infinite)|).mean(axis=-1) * 100，和mae的区别就是，累加的是（预测值与实际值的差）除以（剔除不介于epsilon和infinite之间的实际值)，然后求均值。

**msle**:mean_squared_logarithmic_error，均方差对数，公式为： (log(clip(y_pred, epsilon, infinite)+1)- log(clip(y_true, epsilon,infinite)+1.))^2.mean(axis=-1)，这个就是加入了log对数，剔除不介于epsilon和infinite之间的预测值与实际值之后，然后取对数，作差，平方，累加求均值。

squared_hinge 公式为：(max(1-y_true*y_pred,0))^2.mean(axis=-1)，取1减去预测值与实际值乘积的结果与0比相对大的值的平方的累加均值。

hinge 公式为：(max(1-y_true*y_pred,0)).mean(axis=-1)，取1减去预测值与实际值乘积的结果与0比相对大的值的的累加均值。

**binary_crossentropy**: 二元分类，常说的逻辑回归, 就是常用的交叉熵函数

**categorical_crossentropy**: 多元分类， 交叉熵函数的一种变形


## 自定义损失函数

```
TODO
```

内置损失函数的位置：

```
C:\ProgramData\Anaconda3\pkgs\keras-base-2.2.4-py36_0\Lib\site-packages\keras\losses.py
```

仿照内置的来写自己的损失函数：


## 参考资料

- [Keras中自定义目标函数（损失函数）的简单方法](https://www.aliyun.com/zixun/wenji/1255215.html)
- [使用Keras进行图像分类](https://blog.csdn.net/u010632850/article/details/77102821)