## Generate data

500 MB = 5000000 * 100 Bytes

```
   
    hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen 5000000 /user/ec2-user/JenYinOrdina 

```

### Issues

```

    18/03/13 10:05:35 ERROR tools.DistCp: Invalid arguments:
    java.net.ConnectException: Call From cdh-agent-0.localdomain/172.31.27.86 to ec2-54-229-221-110.eu-west-1.compute.amazonaws.com:8020 failed on connection exception: java.net.ConnectException: Connection refused; For more details see:  http://wiki.apache.org/hadoop/ConnectionRefused
            at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
            at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
            at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
            at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
            at org.apache.hadoop.net.NetUtils.wrapWithMessage(NetUtils.java:791)
            at org.apache.hadoop.net.NetUtils.wrapException(NetUtils.java:731)
            at org.apache.hadoop.ipc.Client.call(Client.java:1506)
            at org.apache.hadoop.ipc.Client.call(Client.java:1439)
            at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
            at com.sun.proxy.$Proxy9.getFileInfo(Unknown Source)
            at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.getFileInfo(ClientNamenodeProtocolTranslatorPB.java:771)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
            at java.lang.reflect.Method.invoke(Method.java:498)
            at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:256)
            at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
            at com.sun.proxy.$Proxy10.getFileInfo(Unknown Source)
            at org.apache.hadoop.hdfs.DFSClient.getFileInfo(DFSClient.java:2123)
            at org.apache.hadoop.hdfs.DistributedFileSystem$19.doCall(DistributedFileSystem.java:1215)
            at org.apache.hadoop.hdfs.DistributedFileSystem$19.doCall(DistributedFileSystem.java:1211)
            at org.apache.hadoop.fs.FileSystemLinkResolver.resolve(FileSystemLinkResolver.java:81)
            at org.apache.hadoop.hdfs.DistributedFileSystem.getFileStatus(DistributedFileSystem.java:1211)
            at org.apache.hadoop.fs.FileSystem.exists(FileSystem.java:1415)
            at org.apache.hadoop.tools.DistCp.setTargetPathExists(DistCp.java:206)
            at org.apache.hadoop.tools.DistCp.run(DistCp.java:131)
            at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
            at org.apache.hadoop.tools.DistCp.main(DistCp.java:441)
    Caused by: java.net.ConnectException: Connection refused
            at sun.nio.ch.SocketChannelImpl.checkConnect(Native Method)
            at sun.nio.ch.SocketChannelImpl.finishConnect(SocketChannelImpl.java:717)
            at org.apache.hadoop.net.SocketIOWithTimeout.connect(SocketIOWithTimeout.java:206)
            at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:530)
            at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:494)
            at org.apache.hadoop.ipc.Client$Connection.setupConnection(Client.java:648)
            at org.apache.hadoop.ipc.Client$Connection.setupIOstreams(Client.java:744)
            at org.apache.hadoop.ipc.Client$Connection.access$3000(Client.java:396)
            at org.apache.hadoop.ipc.Client.getConnection(Client.java:1555)
            at org.apache.hadoop.ipc.Client.call(Client.java:1478)
            ... 21 more

```

Connection refused, listen to private ip ?

```

# HDFS?
    [ec2-user@cdh-agent-0 hadoop-0.20-mapreduce]$ telnet ec2-54-229-221-110.eu-west-1.compute.amazonaws.com 8020
    Trying 54.229.221.110...
    telnet: connect to address 54.229.221.110: Connection refused

```

# http://:50070/webhdfs/v1/user/ec2-user/?op=LISTSTATUS
Clusters are located in different networks. Namenode and Datanode listen on private ip. Listening to multiple ips (Multihoming) is not supported for
hadoop daemons. Copy to local to local instead. 


```

    [ec2-user@cdh-agent-0 ~]$ hadoop distcp hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/user/ec2-user/JenYinOrdina hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/user/ec2-user/jocv
    18/03/13 10:49:12 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/user/ec2-user/JenYinOrdina], targetPath=hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/user/ec2-user/jocv, targetPathExists=false, filtersFile='null'}
    18/03/13 10:49:12 INFO client.RMProxy: Connecting to ResourceManager at cdh-agent-0.localdomain/172.31.27.86:8032
    18/03/13 10:49:13 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 4; dirCnt = 1
    18/03/13 10:49:13 INFO tools.SimpleCopyListing: Build file listing completed.
    18/03/13 10:49:13 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
    18/03/13 10:49:13 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
    18/03/13 10:49:13 INFO tools.DistCp: Number of paths in the copy list: 4
    18/03/13 10:49:13 INFO tools.DistCp: Number of paths in the copy list: 4
    18/03/13 10:49:13 INFO client.RMProxy: Connecting to ResourceManager at cdh-agent-0.localdomain/172.31.27.86:8032
    18/03/13 10:49:14 INFO mapreduce.JobSubmitter: number of splits:3
    18/03/13 10:49:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1520932758114_0004
    18/03/13 10:49:14 INFO impl.YarnClientImpl: Submitted application application_1520932758114_0004
    18/03/13 10:49:14 INFO mapreduce.Job: The url to track the job: http://cdh-agent-0.localdomain:8088/proxy/application_1520932758114_0004/
    18/03/13 10:49:14 INFO tools.DistCp: DistCp job-id: job_1520932758114_0004
    18/03/13 10:49:14 INFO mapreduce.Job: Running job: job_1520932758114_0004
    18/03/13 10:49:19 INFO mapreduce.Job: Job job_1520932758114_0004 running in uber mode : false
    18/03/13 10:49:19 INFO mapreduce.Job:  map 0% reduce 0%
    18/03/13 10:49:25 INFO mapreduce.Job:  map 33% reduce 0%
    18/03/13 10:49:28 INFO mapreduce.Job:  map 100% reduce 0%
    18/03/13 10:49:28 INFO mapreduce.Job: Job job_1520932758114_0004 completed successfully
    18/03/13 10:49:28 INFO mapreduce.Job: Counters: 33
            File System Counters
                    FILE: Number of bytes read=0
                    FILE: Number of bytes written=378810
                    FILE: Number of read operations=0
                    FILE: Number of large read operations=0
                    FILE: Number of write operations=0
                    HDFS: Number of bytes read=500001897
                    HDFS: Number of bytes written=500000000
                    HDFS: Number of read operations=56
                    HDFS: Number of large read operations=0
                    HDFS: Number of write operations=13
            Job Counters
                    Launched map tasks=3
                    Other local map tasks=3
                    Total time spent by all maps in occupied slots (ms)=17649
                    Total time spent by all reduces in occupied slots (ms)=0
                    Total time spent by all map tasks (ms)=17649
                    Total vcore-seconds taken by all map tasks=17649
                    Total megabyte-seconds taken by all map tasks=18072576
            Map-Reduce Framework
                    Map input records=4
                    Map output records=0
                    Input split bytes=357
                    Spilled Records=0
                    Failed Shuffles=0
                    Merged Map outputs=0
                    GC time elapsed (ms)=436
                    CPU time spent (ms)=7260
                    Physical memory (bytes) snapshot=824590336
                    Virtual memory (bytes) snapshot=8376619008
                    Total committed heap usage (bytes)=857210880
            File Input Format Counters
                    Bytes Read=1540
            File Output Format Counters
                    Bytes Written=0
            org.apache.hadoop.tools.mapred.CopyMapper$Counter
                    BYTESCOPIED=500000000
                    BYTESEXPECTED=500000000
                    COPY=4
    [ec2-user@cdh-agent-0 ~]

```

## Display HDFS blocks

```

    [ec2-user@cdh-agent-0 ~]$ hdfs fsck /user/ec2-user/jocv -files -blocks
    Connecting to namenode via http://cdh-agent-0.localdomain:50070
    FSCK started by ec2-user (auth:SIMPLE) from /172.31.27.86 for path /user/ec2-user/jocv at Tue Mar 13 10:53:44 UTC 2018
    /user/ec2-user/jocv <dir>
    /user/ec2-user/jocv/_SUCCESS 0 bytes, 0 block(s):  OK

    /user/ec2-user/jocv/part-m-00000 250000000 bytes, 2 block(s):  OK
    0. BP-1815098863-172.31.27.86-1520873756784:blk_1073743330_2506 len=134217728 Live_repl=3
    1. BP-1815098863-172.31.27.86-1520873756784:blk_1073743332_2508 len=115782272 Live_repl=3

    /user/ec2-user/jocv/part-m-00001 250000000 bytes, 2 block(s):  OK
    0. BP-1815098863-172.31.27.86-1520873756784:blk_1073743331_2507 len=134217728 Live_repl=3
    1. BP-1815098863-172.31.27.86-1520873756784:blk_1073743333_2509 len=115782272 Live_repl=3

    Status: HEALTHY
    Total size:    500000000 B
    Total dirs:    1
    Total files:   3
    Total symlinks:                0
    Total blocks (validated):      4 (avg. block size 125000000 B)
    Minimally replicated blocks:   4 (100.0 %)
    Over-replicated blocks:        0 (0.0 %)
    Under-replicated blocks:       0 (0.0 %)
    Mis-replicated blocks:         0 (0.0 %)
    Default replication factor:    3
    Average block replication:     3.0
    Corrupt blocks:                0
    Missing replicas:              0 (0.0 %)
    Number of data-nodes:          3
    Number of racks:               1
    FSCK ended at Tue Mar 13 10:53:44 UTC 2018 in 2 milliseconds


    The filesystem under path '/user/ec2-user/jocv' is HEALTHY

```

