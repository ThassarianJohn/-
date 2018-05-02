# data.table包

```
R语言data.table包是自带包data.frame的升级版，用于数据框格式数据的处理，最大的特点快。
```

基本操作请看data.frame一文。

## 创建data.table

《[rdocumentation——data.table](https://www.rdocumentation.org/packages/data.table/versions/1.10.4-2/topics/data.table-package)》

将矩阵转为DT(data.table)：

```
DT = data.table(someMatrix)
```

## 文件读写

**fread 读文件**

对于数量较大（上万行）的文件，请使用data.table包的fread函数读取。

**fwrite 写文件**



## 拆分与合并

**melt**

**dcast**

[R之data.table -melt/dcast(数据拆分和合并)](https://www.cnblogs.com/nxld/p/6067137.html)


## setDT


## set


## 行列操作

添加行

删除行

添加列

删除列

## duplicated

[duplicated](https://www.rdocumentation.org/packages/data.table/versions/1.10.4-2/topics/duplicated)


## 参考文件

更多内容见[R语言数据分析利器data.table包 —— 数据框结构处理精讲](https://www.cnblogs.com/ywliao/p/6561219.html)一文。


