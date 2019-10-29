# csv读写

csv
pandas
tenserflow

推荐使用csv方式。

```python
my_train_file = 'filename.csv'

csv_file = csv.reader(open(my_train_file, 'r'))

for line in csv_file:
	#do something
	pass
```

## 参考资料

- [使用Python读写csv文件的三种方法](https://www.cnblogs.com/cloud-ken/p/8432999.html)