
Permission errors, had to execute following commands.

```

    cd /var/lib/

    chmod 755 hadoop-hdfs
    chmod 755 hadoop-httpfs
    chmod 755 hadoop-kms
    chmod 755 hadoop-mapreduce
    chmod 755 hadoop-yarn
    chmod 755 impala
    chmod 755 oozie
    chmod 755 zookeeper


    chown -R hdfs:hdfs hadoop-hdfs
    chown -R httpfs:httpfs hadoop-httpfs
    chown -R kms:kms hadoop-kms
    chown -R mapred:mapred hadoop-mapreduce
    chown -R yarn:yarn hadoop-yarn 
    chown -R zookeeper:zookeeper zookeeper
    chown -R impala:impala impala 
    chown -R oozie:oozie oozie 


```

### Add users

hdfs dfs -ls /user
hdfs dfs -mkdir /user/hilary
hdfs dfs -chown hilary:hilary /user/hilary
hdfs dfs -mkdir /user/anupam
hdfs dchown anunpam:anupam /user/anupam


```
    Found 8 items
    drwxr-xr-x   - admin   admin           0 2018-03-16 10:05 /user/admin
    drwxr-xr-x   - anunpam anupam          0 2018-03-16 10:04 /user/anupam
    drwxr-xr-x   - hilary  hilary          0 2018-03-16 10:03 /user/hilary
    drwxrwxrwx   - mapred  hadoop          0 2018-03-16 09:56 /user/history
    drwxrwxr-t   - hive    hive            0 2018-03-16 09:57 /user/hive
    drwxrwxr-x   - hue     hue             0 2018-03-16 09:57 /user/hue
    drwxrwxr-x   - impala  impala          0 2018-03-16 09:57 /user/impala
    drwxrwxr-x   - oozie   oozie           0 2018-03-16 10:00 /user/oozie


```

curl -u "admin:admin" http://ec2-35-177-177-228.eu-west-2.compute.amazonaws.com:7180/api/v14/hosts

```
[root@cdh-mgt-0 lib]# curl -u "admin:admin" http://ec2-35-177-177-228.eu-west-2.compute.amazonaws.com:7180/api/v14/hosts

    {
    "items" : [ {
        "hostId" : "059cbf27-b5e2-4c57-93ca-d0123cfa8654",
        "ipAddress" : "172.31.29.241",
        "hostname" : "cdh-mgt-0.localdomain",
        "rackId" : "/default",
        "hostUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/hostRedirect/059cbf27-b5e2-4c57-93ca-d0123cfa8654",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "commissionState" : "COMMISSIONED",
        "numCores" : 4,
        "numPhysicalCores" : 2,
        "totalPhysMemBytes" : 16171651072
    }, {
        "hostId" : "a296b6c7-650a-4df5-af60-b1d421917dcf",
        "ipAddress" : "172.31.23.151",
        "hostname" : "cdh-mgt-1.localdomain",
        "rackId" : "/default",
        "hostUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/hostRedirect/a296b6c7-650a-4df5-af60-b1d421917dcf",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "commissionState" : "COMMISSIONED",
        "numCores" : 4,
        "numPhysicalCores" : 2,
        "totalPhysMemBytes" : 16171651072
    }, {
        "hostId" : "4e349dfe-0081-4c39-b331-fd6f7f493558",
        "ipAddress" : "172.31.16.21",
        "hostname" : "cdh-wrk-0.localdomain",
        "rackId" : "/default",
        "hostUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/hostRedirect/4e349dfe-0081-4c39-b331-fd6f7f493558",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "commissionState" : "COMMISSIONED",
        "numCores" : 4,
        "numPhysicalCores" : 2,
        "totalPhysMemBytes" : 16171651072
    }, {
        "hostId" : "b876e2f6-2e5d-4b49-a6c5-8274a390ec64",
        "ipAddress" : "172.31.31.101",
        "hostname" : "cdh-wrk-1.localdomain",
        "rackId" : "/default",
        "hostUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/hostRedirect/b876e2f6-2e5d-4b49-a6c5-8274a390ec64",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "commissionState" : "COMMISSIONED",
        "numCores" : 4,
        "numPhysicalCores" : 2,
        "totalPhysMemBytes" : 16171651072
    }, {
        "hostId" : "68578cf7-a55d-42a5-8719-fccd8b6b9802",
        "ipAddress" : "172.31.29.238",
        "hostname" : "cdh-wrk-2.localdomain",
        "rackId" : "/default",
        "hostUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/hostRedirect/68578cf7-a55d-42a5-8719-fccd8b6b9802",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "commissionState" : "COMMISSIONED",
        "numCores" : 4,
        "numPhysicalCores" : 2,
        "totalPhysMemBytes" : 16171651072
    } ]


```

curl -u "admin:admin" http://ec2-35-177-177-228.eu-west-2.compute.amazonaws.com:7180/api/v8/clusters


```


{
    "items" : [ {
        "name" : "cluster",
        "displayName" : "JeKuOrdina",
        "version" : "CDH5",
        "fullVersion" : "5.13.2",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ]
    } ]
    }
```


curl -u "admin:admin" http://ec2-35-177-177-228.eu-west-2.compute.amazonaws.com:7180/api/v8/clusters/JeKuOrdina/services


```

    {
    "items" : [ {
        "name" : "zookeeper",
        "type" : "ZOOKEEPER",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/zookeeper",
        "serviceState" : "STARTED",
        "healthSummary" : "GOOD",
        "healthChecks" : [ {
        "name" : "ZOOKEEPER_CANARY_HEALTH",
        "summary" : "GOOD"
        }, {
        "name" : "ZOOKEEPER_SERVERS_HEALTHY",
        "summary" : "GOOD"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "ZooKeeper"
    }, {
        "name" : "oozie",
        "type" : "OOZIE",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/oozie",
        "serviceState" : "STARTED",
        "healthSummary" : "GOOD",
        "healthChecks" : [ {
        "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
        "summary" : "GOOD"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "Oozie"
    }, {
        "name" : "hue",
        "type" : "HUE",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/hue",
        "serviceState" : "STARTED",
        "healthSummary" : "BAD",
        "healthChecks" : [ {
        "name" : "HUE_HUE_SERVERS_HEALTHY",
        "summary" : "GOOD"
        }, {
        "name" : "HUE_LOAD_BALANCER_HEALTHY",
        "summary" : "BAD"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "Hue"
    }, {
        "name" : "hdfs",
        "type" : "HDFS",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/hdfs",
        "serviceState" : "STARTED",
        "healthSummary" : "GOOD",
        "healthChecks" : [ {
        "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
        "summary" : "GOOD"
        }, {
        "name" : "HDFS_CANARY_HEALTH",
        "summary" : "GOOD"
        }, {
        "name" : "HDFS_DATA_NODES_HEALTHY",
        "summary" : "GOOD"
        }, {
        "name" : "HDFS_FREE_SPACE_REMAINING",
        "summary" : "GOOD"
        }, {
        "name" : "HDFS_HA_NAMENODE_HEALTH",
        "summary" : "GOOD"
        }, {
        "name" : "HDFS_MISSING_BLOCKS",
        "summary" : "GOOD"
        }, {
        "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
        "summary" : "GOOD"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "HDFS"
    }, {
        "name" : "impala",
        "type" : "IMPALA",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/impala",
        "serviceState" : "STARTED",
        "healthSummary" : "GOOD",
        "healthChecks" : [ {
        "name" : "IMPALA_ASSIGNMENT_LOCALITY",
        "summary" : "DISABLED"
        }, {
        "name" : "IMPALA_CATALOGSERVER_HEALTH",
        "summary" : "GOOD"
        }, {
        "name" : "IMPALA_IMPALADS_HEALTHY",
        "summary" : "GOOD"
        }, {
        "name" : "IMPALA_STATESTORE_HEALTH",
        "summary" : "GOOD"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "Impala"
    }, {
        "name" : "yarn",
        "type" : "YARN",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/yarn",
        "serviceState" : "STARTED",
        "healthSummary" : "GOOD",
        "healthChecks" : [ {
        "name" : "YARN_JOBHISTORY_HEALTH",
        "summary" : "GOOD"
        }, {
        "name" : "YARN_NODE_MANAGERS_HEALTHY",
        "summary" : "GOOD"
        }, {
        "name" : "YARN_RESOURCEMANAGERS_HEALTH",
        "summary" : "GOOD"
        }, {
        "name" : "YARN_USAGE_AGGREGATION_HEALTH",
        "summary" : "DISABLED"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "YARN (MR2 Included)"
    }, {
        "name" : "hive",
        "type" : "HIVE",
        "clusterRef" : {
        "clusterName" : "cluster"
        },
        "serviceUrl" : "http://cdh-mgt-1.localdomain:7180/cmf/serviceRedirect/hive",
        "serviceState" : "STARTED",
        "healthSummary" : "GOOD",
        "healthChecks" : [ {
        "name" : "HIVE_HIVEMETASTORES_HEALTHY",
        "summary" : "GOOD"
        }, {
        "name" : "HIVE_HIVESERVER2S_HEALTHY",
        "summary" : "GOOD"
        } ],
        "configStalenessStatus" : "FRESH",
        "clientConfigStalenessStatus" : "FRESH",
        "maintenanceMode" : false,
        "maintenanceOwners" : [ ],
        "displayName" : "Hive"
    } ]
    }

```