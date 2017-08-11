## 6.3 HBase安装和配置

在安装HBase之前，请先安装好Hadoop集群，Hadoop集群具体的安装和配置请参照之前的文档。

整个步骤为，安装和配置Zookeeper，安装和配置HBase。

| HostName | HBase角色 | Zookeeper | Hadoop角色 |
| :--- | :--- | :--- | :--- |
| hadoopmaster | master | YES | master |
| hadoopslave1 | backup master & Region Server | YES | slave1 |
| hadoopslave2 | Region Server | YES | slave2 |


