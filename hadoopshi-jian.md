## 3.4 Hadoop实践

### 3.4.1 HDFS命令

**常用介绍下列常用HDFS命令**

本节所有命令，我们都在master虚拟机的“终端”程序中运行。

| 命令 | 说明 |
| :--- | :--- |
| hadoop fs -mkdir | 创建HDFS目录 |
| hadoop fs -ls | 列出HDFS目录 |
| hadoop fs -copyFrontLocal | 使用-copyFrontLocal复制本地\(Local\)文件到HDFS |
| hadoop fs -put | 使用-put复制本地\(local\)文件到HDFS |
| hadoop fs -copyToLocal | 使用-copyToLocal将HDFS上的文件复制到本地\(Local\) |
| hadoop fs -get | 使用-get将HDFS上的文件复制到本地\(Local\) |
| hadoop fs -cp | 使用HDFS文件 |
| hadoop fs -mv | 删除HDFS文件 |

**新建文件夹**

```
$hadoop fs -mkdir /u01
$hadoop fs -mkdir /u01/tmp

#创建多级HDFS目录
```

**查看文件夹权限**

```
$hadoop fs -ls -d /u01/tmp
drwxr-xr-x   - hadoop supergroup          0 2017-07-16 02:43 /u01/tmp
```

**上传文件**

hadoop fs –put \[本地地址\] \[hadoop目录\]

> 同时也可以上传文件夹

```
$hadoop fs –put /home/file.txt /user/u01/

#查看文件夹下内容
[hadoop@hadoopmaster home]$ hadoop fs -ls -R /u01/tmp/
-rw-r--r--   2 hadoop supergroup       1659 2017-07-16 02:57 /u01/tmp/1.txt
```

**查看文件内容**

hadoop dfs –cat \[文件目录\]

```
$hadoop fs -cat /u01/tmp/1.txt
```

**复制、移动、删除文件**

```
#复制
$hadoop fs -cp /u01/tmp/1.txt /u01/tmp/2.txt

#移动
$hadoop fs -mv /u01/tmp/2.txt /u01/tmp/3.txt

#删除
$hadoop fs -rm /u01/tmp/3.txt
Deleted /u01/tmp/3.txt
```

**创建新的空文件**

```
$hadoop fs -touchz /u01/tmp/5.txt
```

**下载Hadoop上的文件**

hadoop fs -get \[文件目录\] \[本地目录\]

```
$hadoop fs -get /u01/tmp/2.txt /home/hadoop
```

**删除文件夹**

```
$hadoop fs –rm -r /u01/tmp
```

> HDFS提供了一些方便选项，比如可以在命令中加上 -R,R代表recursive\(递归\)

**在Hadoop HDFS Web用户界面浏览HDFS**

打开地址： [http://192.168.44.131:50070/explorer.html\#/](http://192.168.44.131:50070/explorer.html#/)

![](/assets/3.4.1_1.png)![](/assets/3.4.1_2.png)可以输入完整路径直接查看该目录下的文件。

![](/assets/3.4.1_3.png)

### 3.4.2 MapReduce

MapReduce是一种程序开发模式，可以使用大量服务器来并行处理。MapReduce，简单地说，Map就是分配工作、Reduce就是将工作整理汇总。

* 首先使用Map将待处理的数据分割成很多的小份数据，由每台服务器分别运行。
* 再通过Reduce程序进行数据合并，最后汇总整理出结果。

本章将用wordCount.java作为范例来介绍MapReduce。

介绍wordCount.java


