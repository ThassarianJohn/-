# Elephas

Elephas 是 Keras 的扩展, 允许你使用 Spark 进行分布式深度学习。

Elephas的核心思想是将数据集用RDD来表示，将数据集分成多个分区分别训练，每个分区的训练作为一个Spark任务在不同的节点（Worker）运行，对RDD的每个分区的数据设计Keras模型，并通过Spark的Driver收集各个分区的训练权重参数来更新Keras模型的参数。


## 参考资料

- [elephas on Github](https://github.com/maxpumperla/elephas)
- [Keras On Spark](https://blog.csdn.net/choushi5845/article/details/100747143)