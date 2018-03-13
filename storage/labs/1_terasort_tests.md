### Create user

On every machine: 

```

    [ec2-user@cdh-agent-1 ~]$ sudo adduser JeKuOrdina

```

Create user on hdfs 

```

    [ec2-user@cdh-agent-0 ~]$ sudo su hdfs -c "hadoop fs -mkdir /user/JeKuOrdina"
    [ec2-user@cdh-agent-0 ~]$ sudo su hdfs -c "hadoop fs -chown JeKuOrdina /user/JeKuOrdina"

```

Generate new Teragen dataset

```

    [JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen


    18/03/13 11:10:15 INFO mapreduce.Job: Job job_1520932758114_0005 completed successfully
    18/03/13 11:10:15 INFO mapreduce.Job: Counters: 31
            File System Counters
                    FILE: Number of bytes read=0
                    FILE: Number of bytes written=246452
                    FILE: Number of read operations=0
                    FILE: Number of large read operations=0
                    FILE: Number of write operations=0
                    HDFS: Number of bytes read=170
                    HDFS: Number of bytes written=10000000000
                    HDFS: Number of read operations=8
                    HDFS: Number of large read operations=0
                    HDFS: Number of write operations=4
            Job Counters
                    Launched map tasks=2
                    Other local map tasks=2
                    Total time spent by all maps in occupied slots (ms)=118184
                    Total time spent by all reduces in occupied slots (ms)=0
                    Total time spent by all map tasks (ms)=118184
                    Total vcore-seconds taken by all map tasks=118184
                    Total megabyte-seconds taken by all map tasks=121020416
            Map-Reduce Framework
                    Map input records=100000000
                    Map output records=100000000
                    Input split bytes=170
                    Spilled Records=0
                    Failed Shuffles=0
                    Merged Map outputs=0
                    GC time elapsed (ms)=620
                    CPU time spent (ms)=109170
                    Physical memory (bytes) snapshot=796487680
                    Virtual memory (bytes) snapshot=5575663616
                    Total committed heap usage (bytes)=738721792
            org.apache.hadoop.examples.terasort.TeraGen$Counters
                    CHECKSUM=214760662691937609
            File Input Format Counters
                    Bytes Read=0
            File Output Format Counters
                    Bytes Written=10000000000

    real    1m9.435s
    user    0m5.475s
    sys     0m0.278s


```

Sort teragen directory

```

    time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort /user/JeKuOrdina/teragen /user/JeKuOrdina/teragen_sorted

    Authenticating with public key "imported-openssh-key" from agent
     ┌────────────────────────────────────────────────────────────────────┐
     │                        • MobaXterm 10.2 •                          │
     │            (SSH client, X-server and networking tools)             │
     │                                                                    │
     │ ➤ SSH session to ec2-user@ec2-35-176-150-212.eu-west-2.compute.amazonaws.com│
     │   • SSH compression : ✔                                            │
     │   • SSH-browser     : ✔                                            │
     │   • X11-forwarding  : ✘  (disabled or not supported by server)     │
     │   • DISPLAY         : 192.168.43.119:0.0                           │
     │                                                                    │
     │ ➤ For more info, ctrl+click on help or visit our website           │
     └────────────────────────────────────────────────────────────────────┘

Last login: Tue Mar 13 09:26:32 2018 from 77.95.96.78
[ec2-user@cdh-agent-0 ~]$ hadoop distcp hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/JeKuOrdina hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/jocv
18/03/13 10:47:36 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/JeKuOrdina], targetPath=hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/jocv, targetPathExists=false, filtersFile='null'}
18/03/13 10:47:36 INFO client.RMProxy: Connecting to ResourceManager at cdh-agent-0.localdomain/172.31.27.86:8032
18/03/13 10:47:36 ERROR tools.DistCp: Invalid input:
org.apache.hadoop.tools.CopyListing$InvalidInputException: hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/JeKuOrdina doesn't exist
        at org.apache.hadoop.tools.GlobbedCopyListing.doBuildListing(GlobbedCopyListing.java:84)
        at org.apache.hadoop.tools.CopyListing.buildListing(CopyListing.java:86)
        at org.apache.hadoop.tools.DistCp.createInputFileListing(DistCp.java:377)
        at org.apache.hadoop.tools.DistCp.prepareFileListing(DistCp.java:90)
        at org.apache.hadoop.tools.DistCp.execute(DistCp.java:179)
        at org.apache.hadoop.tools.DistCp.run(DistCp.java:141)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
        at org.apache.hadoop.tools.DistCp.main(DistCp.java:441)
[ec2-user@cdh-agent-0 ~]$ hadoop distcp hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/JenYinOrdina hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/jocv
18/03/13 10:48:31 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/JenYinOrdina], targetPath=hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/jocv, targetPathExists=false, filtersFile='null'}
18/03/13 10:48:31 INFO client.RMProxy: Connecting to ResourceManager at cdh-agent-0.localdomain/172.31.27.86:8032
18/03/13 10:48:31 ERROR tools.DistCp: Invalid input:
org.apache.hadoop.tools.CopyListing$InvalidInputException: hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-users/JenYinOrdina doesn't exist
        at org.apache.hadoop.tools.GlobbedCopyListing.doBuildListing(GlobbedCopyListing.java:84)
        at org.apache.hadoop.tools.CopyListing.buildListing(CopyListing.java:86)
        at org.apache.hadoop.tools.DistCp.createInputFileListing(DistCp.java:377)
        at org.apache.hadoop.tools.DistCp.prepareFileListing(DistCp.java:90)
        at org.apache.hadoop.tools.DistCp.execute(DistCp.java:179)
        at org.apache.hadoop.tools.DistCp.run(DistCp.java:141)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
        at org.apache.hadoop.tools.DistCp.main(DistCp.java:441)
[ec2-user@cdh-agent-0 ~]$ hadoop distcp hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-user/JenYinOrdina hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-user/jocv
18/03/13 10:48:44 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-user/JenYinOrdina], targetPath=hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-user/jocv, targetPathExists=false, filtersFile='null'}
18/03/13 10:48:44 INFO client.RMProxy: Connecting to ResourceManager at cdh-agent-0.localdomain/172.31.27.86:8032
18/03/13 10:48:44 ERROR tools.DistCp: Invalid input:
org.apache.hadoop.tools.CopyListing$InvalidInputException: hdfs://ec2-35-176-150-212.eu-west-2.compute.amazonaws.com:8020/home/ec2-user/JenYinOrdina doesn't exist
        at org.apache.hadoop.tools.GlobbedCopyListing.doBuildListing(GlobbedCopyListing.java:84)
        at org.apache.hadoop.tools.CopyListing.buildListing(CopyListing.java:86)
        at org.apache.hadoop.tools.DistCp.createInputFileListing(DistCp.java:377)
        at org.apache.hadoop.tools.DistCp.prepareFileListing(DistCp.java:90)
        at org.apache.hadoop.tools.DistCp.execute(DistCp.java:179)
        at org.apache.hadoop.tools.DistCp.run(DistCp.java:141)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
        at org.apache.hadoop.tools.DistCp.main(DistCp.java:441)
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
[ec2-user@cdh-agent-0 ~]$ hdfs fsck /user/ec-user/jocv -files -blocks
Connecting to namenode via http://cdh-agent-0.localdomain:50070
FSCK started by ec2-user (auth:SIMPLE) from /172.31.27.86 for path /user/ec-user/jocv at Tue Mar 13 10:53:28 UTC 2018


Path '/user/ec-user/jocv' does not exist
[ec2-user@cdh-agent-0 ~]$
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
[ec2-user@cdh-agent-0 ~]$ useradd JeKuOrdina
-bash: useradd: command not found
[ec2-user@cdh-agent-0 ~]$ sudo adduser JeKuOrdina
[ec2-user@cdh-agent-0 ~]$ hdfs fs -mkdir /user/JeKuOrdina
Error: Could not find or load main class fs
[ec2-user@cdh-agent-0 ~]$ sudo su hdfs -c "hadoop fs -mkdir /user/JeKuOrdina"
[ec2-user@cdh-agent-0 ~]$ sudo su hdfs -c "hadoop fs -chown JeKuOrdina /user/JeKuOrdina"
[ec2-user@cdh-agent-0 ~]$ ^C
[ec2-user@cdh-agent-0 ~]$ time

real    0m0.000s
user    0m0.000s
sys     0m0.000s
[ec2-user@cdh-agent-0 ~]$ time

real    0m0.000s
user    0m0.000s
sys     0m0.000s
[ec2-user@cdh-agent-0 ~]$     time hadoop jar hadoop-*examples*.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
Not a valid JAR: /home/ec2-user/hadoop-*examples*.jar

real    0m0.177s
user    0m0.181s
sys     0m0.058s
[ec2-user@cdh-agent-0 ~]$ su JeKuOrdina
Password:
[ec2-user@cdh-agent-0 ~]$ sduo su JeKuOrdina
-bash: sduo: command not found
[ec2-user@cdh-agent-0 ~]$ sudo su JeKuOrdina
[JeKuOrdina@cdh-agent-0 ec2-user]$     time hadoop jar hadoop-*examples*.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
Not a valid JAR: /tmp/hsperfdata_JeKuOrdina/hadoop-*examples*.jar

real    0m0.183s
user    0m0.196s
sys     0m0.050s
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDHhadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
CDH/                       CDH-5.9.3-1.cdh5.9.3.p0.4/
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDHhadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
CDH/                       CDH-5.9.3-1.cdh5.9.3.p0.4/
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/hadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
bin/     etc/     include/ jars/    lib/     lib64/   libexec/ meta/    share/
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hhadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
hadoop/                hadoop-hdfs/           hadoop-kms/            hadoop-yarn/           hbase-solr/            hive-hcatalog/
hadoop-0.20-mapreduce/ hadoop-httpfs/         hadoop-mapreduce/      hbase/                 hive/                  hue/
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hhadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
hadoop/                hadoop-hdfs/           hadoop-kms/            hadoop-yarn/           hbase-solr/            hive-hcatalog/
hadoop-0.20-mapreduce/ hadoop-httpfs/         hadoop-mapreduce/      hbase/                 hive/                  hue/
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -D dfs.block.size=320000000 100000000 /user/JeKuOrdina/teragen
18/03/13 11:09:08 INFO client.RMProxy: Connecting to ResourceManager at cdh-agent-0.localdomain/172.31.27.86:8032
18/03/13 11:09:08 INFO terasort.TeraSort: Generating 100000000 using 2
18/03/13 11:09:08 INFO mapreduce.JobSubmitter: number of splits:2
18/03/13 11:09:08 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
18/03/13 11:09:08 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1520932758114_0005
18/03/13 11:09:08 INFO impl.YarnClientImpl: Submitted application application_1520932758114_0005
18/03/13 11:09:08 INFO mapreduce.Job: The url to track the job: http://cdh-agent-0.localdomain:8088/proxy/application_1520932758114_0005/
18/03/13 11:09:08 INFO mapreduce.Job: Running job: job_1520932758114_0005
18/03/13 11:09:13 INFO mapreduce.Job: Job job_1520932758114_0005 running in uber mode : false
18/03/13 11:09:13 INFO mapreduce.Job:  map 0% reduce 0%
18/03/13 11:09:24 INFO mapreduce.Job:  map 10% reduce 0%
18/03/13 11:09:27 INFO mapreduce.Job:  map 16% reduce 0%
18/03/13 11:09:30 INFO mapreduce.Job:  map 23% reduce 0%
18/03/13 11:09:33 INFO mapreduce.Job:  map 29% reduce 0%
18/03/13 11:09:36 INFO mapreduce.Job:  map 35% reduce 0%
18/03/13 11:09:39 INFO mapreduce.Job:  map 42% reduce 0%
18/03/13 11:09:42 INFO mapreduce.Job:  map 49% reduce 0%
18/03/13 11:09:45 INFO mapreduce.Job:  map 55% reduce 0%
18/03/13 11:09:48 INFO mapreduce.Job:  map 62% reduce 0%
18/03/13 11:09:51 INFO mapreduce.Job:  map 68% reduce 0%
18/03/13 11:09:54 INFO mapreduce.Job:  map 74% reduce 0%
18/03/13 11:09:57 INFO mapreduce.Job:  map 79% reduce 0%
18/03/13 11:10:00 INFO mapreduce.Job:  map 83% reduce 0%
18/03/13 11:10:03 INFO mapreduce.Job:  map 86% reduce 0%
18/03/13 11:10:06 INFO mapreduce.Job:  map 90% reduce 0%
18/03/13 11:10:09 INFO mapreduce.Job:  map 94% reduce 0%
18/03/13 11:10:12 INFO mapreduce.Job:  map 97% reduce 0%
18/03/13 11:10:14 INFO mapreduce.Job:  map 100% reduce 0%
18/03/13 11:10:15 INFO mapreduce.Job: Job job_1520932758114_0005 completed successfully
18/03/13 11:10:15 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=246452
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=170
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=8
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=4
        Job Counters
                Launched map tasks=2
                Other local map tasks=2
                Total time spent by all maps in occupied slots (ms)=118184
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=118184
                Total vcore-seconds taken by all map tasks=118184
                Total megabyte-seconds taken by all map tasks=121020416
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Input split bytes=170
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=620
                CPU time spent (ms)=109170
                Physical memory (bytes) snapshot=796487680
                Virtual memory (bytes) snapshot=5575663616
                Total committed heap usage (bytes)=738721792
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=214760662691937609
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=10000000000

real    1m9.435s
user    0m5.475s
sys     0m0.278s
[JeKuOrdina@cdh-agent-0 ec2-user]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort /user/JeKuOrdina/teragen /user/JeKuOrdina/teragen_sorted


    18/03/13 11:13:58 INFO mapreduce.Job: Job job_1520932758114_0006 completed successfully
    18/03/13 11:13:59 INFO mapreduce.Job: Counters: 49
            File System Counters
                    FILE: Number of bytes read=8837547686
                    FILE: Number of bytes written=13229941834
                    FILE: Number of read operations=0
                    FILE: Number of large read operations=0
                    FILE: Number of write operations=0
                    HDFS: Number of bytes read=10000004384
                    HDFS: Number of bytes written=10000000000
                    HDFS: Number of read operations=114
                    HDFS: Number of large read operations=0
                    HDFS: Number of write operations=12
            Job Counters
                    Launched map tasks=32
                    Launched reduce tasks=6
                    Data-local map tasks=32
                    Total time spent by all maps in occupied slots (ms)=682506
                    Total time spent by all reduces in occupied slots (ms)=254473
                    Total time spent by all map tasks (ms)=682506
                    Total time spent by all reduce tasks (ms)=254473
                    Total vcore-seconds taken by all map tasks=682506
                    Total vcore-seconds taken by all reduce tasks=254473
                    Total megabyte-seconds taken by all map tasks=698886144
                    Total megabyte-seconds taken by all reduce tasks=260580352
            Map-Reduce Framework
                    Map input records=100000000
                    Map output records=100000000
                    Map output bytes=10200000000
                    Map output materialized bytes=4398590620
                    Input split bytes=4384
                    Combine input records=0
                    Combine output records=0
                    Reduce input groups=100000000
                    Reduce shuffle bytes=4398590620
                    Reduce input records=100000000
                    Reduce output records=100000000
                    Spilled Records=300000000
                    Shuffled Maps =192
                    Failed Shuffles=0
                    Merged Map outputs=192
                    GC time elapsed (ms)=18968
                    CPU time spent (ms)=812090
                    Physical memory (bytes) snapshot=25427283968
                    Virtual memory (bytes) snapshot=106156916736
                    Total committed heap usage (bytes)=25001721856
            Shuffle Errors
                    BAD_ID=0
                    CONNECTION=0
                    IO_ERROR=0
                    WRONG_LENGTH=0
                    WRONG_MAP=0
                    WRONG_REDUCE=0
            File Input Format Counters
                    Bytes Read=10000000000
            File Output Format Counters
                    Bytes Written=10000000000
    18/03/13 11:13:59 INFO terasort.TeraSort: done

    real    2m2.215s
    user    0m7.162s
    sys     0m0.359s


```