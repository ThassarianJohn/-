# Spark安装

**安装jdk**

yum安装：

```
$ yum -y install java-1.8.0-openjdk java-1.8.0-openjdk-devel
```

或手动安装：

下载并解压

配置环境变量

打开/etc/profile文件

```
$ vi /etc/profile
```

在文件末尾插入如下内容

```
export JAVA_HOME=/home/soft/jdk1.8.0_111
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```

检查安装是否成功

```
java -version
```


**安装Hadoop**

下载并解压

将bin目录加到PATH环境变量中

配置部署测试详见《Hadoop》一文。

**python版的需先安装Anaconda**

**安装scala**

**安装Spark**

详见《[spark学习-spark安装和启动](https://blog.csdn.net/xfks55/article/details/80784424)》。

**分派任务j进行测试**



## 参考资料

- [Spark官网](https://spark.apache.org/)
- [Spark源代码 on Github](https://github.com/apache/spark)
- [Spark快速指南](http://spark.apache.org/docs/latest/quick-start.html)
- [Hadoop](https://hadoop.apache.org/)
- [**spark学习-spark安装和启动**](https://blog.csdn.net/xfks55/article/details/80784424)
- [Spark之各类启动命令汇总](https://blog.csdn.net/mmake1994/article/details/79921833)
- [Intellij 创建spark项目的两种方式](https://blog.csdn.net/a532672728/article/details/79455024)
- [通过IDEA搭建scala开发环境开发spark应用程序](https://www.cnblogs.com/wcwen1990/p/7860716.html)
- [Windows下搭建hadoop 搭建本地hadoop开发环境](https://blog.csdn.net/wangaz521/article/details/79717177)
- [编译Windows版本的hadoop](https://blog.csdn.net/qq_32782059/article/details/80590278)
- [提交任务到spark](https://www.cnblogs.com/Mrwan/p/7380574.html)
- [winutils下载](https://github.com/steveloughran/winutils)
- [centos yum 安装 jdk1.8](https://blog.csdn.net/lyflyyvip/article/details/78265747)