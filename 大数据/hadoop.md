# Hadoop

hadoop

yarn：资源管理器

zookeeper：服务管理

HDFS：分布式文件系统

hbase：分布式数据库

## hadoop的安装和配置

下载压缩包，完成后进行解压。

需要修改的配置文件有七个：

- core-site.xml
- hdfs-site.xml
- yarn-site.xml
- mapred-site.xml
- slaves
- hadoop-env.sh
- yarn-env.sh

#### core-site.xml


```xml
<property>
   <name>hadoop.tmp.dir</name>
   <value>file:/home/hadoop/hadoop-2.7.3/hdfs/tmp</value>
   <description>A base for other temporary directories.</description>
 </property>
 <property>
  <name>io.file.buffer.size</name>
   <value>131072</value>
 </property>
 <property>
   <name>fs.defaultFS</name>
   <value>hdfs://master:9000</value>
 </property>
```

#### hadoop-env.sh

```xml
export JAVA_HOME=/...
```

#### yarn-env.sh

```xml
export JAVA_HOME=/...
```

#### hdfs-site.xml

```xml
<property>
 <name>dfs.replication</name>
   <value>1</value>
 </property>
 <property>
   <name>dfs.namenode.name.dir</name>
   <value>file:/home/hadoop/hadoop-2.7.3/hdfs/name</value>
   <final>true</final>
</property>
 <property>
   <name>dfs.datanode.data.dir</name>
   <value>file:/home/hadoop/hadoop-2.7.3/hdfs/data</value>
   <final>true</final>
 </property>
 <property>
  <name>dfs.namenode.secondary.http-address</name>
   <value>master:9001</value>
 </property>
 <property>
   <name>dfs.webhdfs.enabled</name>
   <value>true</value>
 </property>
 <property>
   <name>dfs.permissions</name>
   <value>false</value>
 </property>
```

#### mapred-site.xml

```xml
<property>
   <name>mapreduce.framework.name</name>
   <value>yarn</value>
 </property>
```

#### yarn-site.xml

```xml
<property>
 <name>yarn.resourcemanager.address</name>
   <value>master:18040</value>
 </property>
 <property>
   <name>yarn.resourcemanager.scheduler.address</name>
   <value>master:18030</value>
 </property>
 <property>
   <name>yarn.resourcemanager.webapp.address</name>
   <value>master:18088</value>
 </property>
 <property>
   <name>yarn.resourcemanager.resource-tracker.address</name>
   <value>master:18025</value>
 </property>
 <property>
   <name>yarn.resourcemanager.admin.address</name>
   <value>master:18141</value>
 </property>
 <property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
 </property>
 <property>
     <name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>
     <value>org.apache.hadoop.mapred.ShuffleHandler</value>
 </property>
```

#### slaves

按照自己的配

**由于不明的BUG，以上配置完成后，还需要按照[《hadoop：datanode连接不上namenode》](https://blog.csdn.net/qq_32506963/article/details/78206516)一文的说明操作，才能正常启动hadoop。**

#### 测试



第一次启动hadoop服务之前，必须执行格式化namenode 

```cmd
$ hdfs namenode -format
```

启动hadoop

```cmd
$ ./start-all.sh
```

运行测试程序，如能看到输出，则部署成功！

```cmd
$ hadoop  jar  /root/hadoop-2.9.2/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.9.2.jar  pi 1 10
```

## 参考资料

- [Hadoop集群搭建教程（详细）](https://blog.csdn.net/fanxin_i/article/details/80425461)
- [hadoop：datanode连接不上namenode](https://blog.csdn.net/qq_32506963/article/details/78206516)