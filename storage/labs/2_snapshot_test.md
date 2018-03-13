
```

    [ec2-user@cdh-agent-0 ~]$ hdfs dfs -mkdir /user/ec2-user/precious
    [ec2-user@cdh-agent-0 ~]$ hadoop dfs -put SEBC.zip /user/ec2-user/precious/
    DEPRECATED: Use of this script to execute hdfs command is deprecated.
    Instead use the hdfs command for it.

    [ec2-user@cdh-agent-0 ~]$ hdfs dfs -ls /user/ec2-user/precious
    Found 1 items
    -rw-r--r--   3 ec2-user supergroup     470034 2018-03-13 11:17 /user/ec2-user/precious/SEBC.zip


```

Remove snapshot directory

```

    rmr: Failed to move to trash: hdfs://cdh-agent-0.localdomain:8020/user/ec2-user/precious: The directory /user/ec2-user/precious cannot be deleted since /user/ec2-user/precious is snapshottable and already has snapshots

```

Add hdfs httpfs service
stop hive
Backup metastore
Update hive metastore for HA

```

    [ec2-user@cdh-server-0 ~]$ mysqldump -uroot -p --databases metastore --single-transaction > hive.sql

```
