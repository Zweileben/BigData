## 5.7 Hive 内部表

Hive内部表与数据库中的Table在概念上是类似。

* 每一个Table在Hive中都有一个相应的目录存储数据。例如，一个表test，它在HDFS中的路径为：$/warehouse/test。warehouse是在hive-site.xml中由${hive.metastore.warehouse.dir}指定的数据仓库的目录
* 所有的Table数据（不包括External Table）都保存在这个目录中。
* 删除表时，元数据与数据都会被删除

**创建内部表**




