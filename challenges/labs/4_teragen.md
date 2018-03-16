
### TeraGen cmd
time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen \
>     -D dfs.block.size=640000000 \
>     -Dmapreduce.job.maps=16 \
>     -Dmapreduce.map.memory.mb=768 \
>      65536000 /user/hilary/tgen

```
    18/03/16 10:12:13 INFO client.RMProxy: Connecting to ResourceManager at cdh-mgt-0.localdomain/172.31.29.241:8032
    18/03/16 10:12:14 INFO terasort.TeraGen: Generating 65536000 using 16
    18/03/16 10:12:14 INFO mapreduce.JobSubmitter: number of splits:16
    18/03/16 10:12:14 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
    18/03/16 10:12:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1521194200518_0001
    18/03/16 10:12:14 INFO impl.YarnClientImpl: Submitted application application_1521194200518_0001
    18/03/16 10:12:14 INFO mapreduce.Job: The url to track the job: http://cdh-mgt-0.localdomain:8088/proxy/application_1521194200518_0001/
    18/03/16 10:12:14 INFO mapreduce.Job: Running job: job_1521194200518_0001

    18/03/16 10:12:20 INFO mapreduce.Job: Job job_1521194200518_0001 running in uber mode : false
    18/03/16 10:12:20 INFO mapreduce.Job:  map 0% reduce 0%
    18/03/16 10:12:30 INFO mapreduce.Job:  map 6% reduce 0%
    18/03/16 10:12:33 INFO mapreduce.Job:  map 31% reduce 0%
    18/03/16 10:12:35 INFO mapreduce.Job:  map 38% reduce 0%
    18/03/16 10:12:36 INFO mapreduce.Job:  map 44% reduce 0%
    18/03/16 10:12:37 INFO mapreduce.Job:  map 50% reduce 0%
    18/03/16 10:12:46 INFO mapreduce.Job:  map 56% reduce 0%
    18/03/16 10:12:49 INFO mapreduce.Job:  map 65% reduce 0%
    18/03/16 10:12:50 INFO mapreduce.Job:  map 72% reduce 0%
    18/03/16 10:12:51 INFO mapreduce.Job:  map 78% reduce 0%
    18/03/16 10:12:54 INFO mapreduce.Job:  map 82% reduce 0%
    18/03/16 10:12:55 INFO mapreduce.Job:  map 85% reduce 0%
    18/03/16 10:12:56 INFO mapreduce.Job:  map 89% reduce 0%
    18/03/16 10:12:57 INFO mapreduce.Job:  map 92% reduce 0%
    18/03/16 10:13:00 INFO mapreduce.Job:  map 96% reduce 0%
    18/03/16 10:13:01 INFO mapreduce.Job:  map 99% reduce 0%
    18/03/16 10:13:02 INFO mapreduce.Job:  map 100% reduce 0%
    18/03/16 10:13:02 INFO mapreduce.Job: Job job_1521194200518_0001 completed successfully
    18/03/16 10:13:02 INFO mapreduce.Job: Counters: 31
            File System Counters
                    FILE: Number of bytes read=0
                    FILE: Number of bytes written=2361206
                    FILE: Number of read operations=0
                    FILE: Number of large read operations=0
                    FILE: Number of write operations=0
                    HDFS: Number of bytes read=1368
                    HDFS: Number of bytes written=6553600000
                    HDFS: Number of read operations=64
                    HDFS: Number of large read operations=0
                    HDFS: Number of write operations=32
            Job Counters
                    Launched map tasks=16
                    Other local map tasks=16
                    Total time spent by all maps in occupied slots (ms)=266166
                    Total time spent by all reduces in occupied slots (ms)=0
                    Total time spent by all map tasks (ms)=266166
                    Total vcore-milliseconds taken by all map tasks=266166
                    Total megabyte-milliseconds taken by all map tasks=272553984
            Map-Reduce Framework
                    Map input records=65536000
                    Map output records=65536000
                    Input split bytes=1368
                    Spilled Records=0
                    Failed Shuffles=0
                    Merged Map outputs=0
                    GC time elapsed (ms)=1911
                    CPU time spent (ms)=114950
                    Physical memory (bytes) snapshot=5076094976
                    Virtual memory (bytes) snapshot=41088376832
                    Total committed heap usage (bytes)=4825546752
            org.apache.hadoop.examples.terasort.TeraGen$Counters
                    CHECKSUM=140750829423462787
            File Input Format Counters
                    Bytes Read=0
            File Output Format Counters
                    Bytes Written=6553600000

    real    0m51.110s
    user    0m6.217s
    sys     0m0.343s
```

### Folder content

hdfs dfs -ls /user/hilary/tgen

```
    Found 17 items
    -rw-r--r--   3 hilary hilary          0 2018-03-16 10:13 /user/hilary/tgen/_SUCCESS
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00000
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00001
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00002
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00003
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00004
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00005
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00006
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00007
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00008
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00009
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00010
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00011
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00012
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00013
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:12 /user/hilary/tgen/part-m-00014
    -rw-r--r--   3 hilary hilary  409600000 2018-03-16 10:13 /user/hilary/tgen/part-m-00015
```

### Block list

hadoop fsck -blocks /user/hilary

```
    DEPRECATED: Use of this script to execute hdfs command is deprecated.
    Instead use the hdfs command for it.

    Connecting to namenode via http://cdh-mgt-0.localdomain:50070/fsck?ugi=hilary&blocks=1&path=%2Fuser%2Fhilary
    FSCK started by hilary (auth:SIMPLE) from /172.31.23.151 for path /user/hilary at Fri Mar 16 10:15:33 UTC 2018
    .................Status: HEALTHY
    Total size:    6553600000 B
    Total dirs:    3
    Total files:   17
    Total symlinks:                0
    Total blocks (validated):      16 (avg. block size 409600000 B)
    Minimally replicated blocks:   16 (100.0 %)
    Over-replicated blocks:        0 (0.0 %)
    Under-replicated blocks:       0 (0.0 %)
    Mis-replicated blocks:         0 (0.0 %)
    Default replication factor:    3
    Average block replication:     3.0
    Corrupt blocks:                0
    Missing replicas:              0 (0.0 %)
    Number of data-nodes:          4
    Number of racks:               1
    FSCK ended at Fri Mar 16 10:15:33 UTC 2018 in 2 milliseconds


    The filesystem under path '/user/hilary' is HEALTHY
```