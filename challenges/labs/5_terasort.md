
time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort \
     -Dmapreduce.job.maps=16 \
     -Dmapreduce.job.reduces=16 \
     -Dmapreduce.map.memory.mb=768 \
     /user/hilary/tgen /user/hilary/tsort 

```

    18/03/16 10:40:38 INFO terasort.TeraSort: starting
    18/03/16 10:40:39 INFO hdfs.DFSClient: Created token for hilary: HDFS_DELEGATION_TOKEN owner=hilary@JEKUORDINA.NL, renewer=yarn, realUser=, issueDate=1521196839555, maxDate=1521801639555, sequenceNumber=1, masterKeyId=2 on 172.31.29.241:8020
    18/03/16 10:40:39 INFO security.TokenCache: Got dt for hdfs://cdh-mgt-0.localdomain:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.29.241:8020, Ident: (token for hilary: HDFS_DELEGATION_TOKEN owner=hilary@JEKUORDINA.NL, renewer=yarn, realUser=, issueDate=1521196839555, maxDate=1521801639555, sequenceNumber=1, masterKeyId=2)
    18/03/16 10:40:39 INFO input.FileInputFormat: Total input paths to process : 16
    Spent 264ms computing base-splits.
    Spent 2ms computing TeraScheduler splits.
    Computing input splits took 267ms
    Sampling 10 splits of 16
    Making 16 from 100000 sampled records
    Computing parititions took 552ms
    Spent 821ms computing partitions.
    18/03/16 10:40:40 INFO client.RMProxy: Connecting to ResourceManager at cdh-mgt-0.localdomain/172.31.29.241:8032
    18/03/16 10:40:40 INFO mapreduce.JobSubmitter: number of splits:16
    18/03/16 10:40:40 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1521196557010_0001
    18/03/16 10:40:40 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.29.241:8020, Ident: (token for hilary: HDFS_DELEGATION_TOKEN owner=hilary@JEKUORDINA.NL, renewer=yarn, realUser=, issueDate=1521196839555, maxDate=1521801639555, sequenceNumber=1, masterKeyId=2)
    18/03/16 10:40:41 INFO impl.YarnClientImpl: Submitted application application_1521196557010_0001
    18/03/16 10:40:41 INFO mapreduce.Job: The url to track the job: http://cdh-mgt-0.localdomain:8088/proxy/application_1521196557010_0001/
    18/03/16 10:40:41 INFO mapreduce.Job: Running job: job_1521196557010_0001
    18/03/16 10:40:48 INFO mapreduce.Job: Job job_1521196557010_0001 running in uber mode : false
    18/03/16 10:40:48 INFO mapreduce.Job:  map 0% reduce 0%
    18/03/16 10:41:06 INFO mapreduce.Job:  map 8% reduce 0%
    18/03/16 10:41:07 INFO mapreduce.Job:  map 13% reduce 0%
    18/03/16 10:41:08 INFO mapreduce.Job:  map 21% reduce 0%
    18/03/16 10:41:09 INFO mapreduce.Job:  map 27% reduce 0%
    18/03/16 10:41:10 INFO mapreduce.Job:  map 40% reduce 0%
    18/03/16 10:41:12 INFO mapreduce.Job:  map 44% reduce 0%
    18/03/16 10:41:16 INFO mapreduce.Job:  map 49% reduce 0%
    18/03/16 10:41:17 INFO mapreduce.Job:  map 50% reduce 0%
    18/03/16 10:41:24 INFO mapreduce.Job:  map 55% reduce 0%
    18/03/16 10:41:25 INFO mapreduce.Job:  map 63% reduce 0%
    18/03/16 10:41:26 INFO mapreduce.Job:  map 65% reduce 0%
    18/03/16 10:41:28 INFO mapreduce.Job:  map 73% reduce 0%
    18/03/16 10:41:29 INFO mapreduce.Job:  map 77% reduce 0%
    18/03/16 10:41:32 INFO mapreduce.Job:  map 85% reduce 0%
    18/03/16 10:41:33 INFO mapreduce.Job:  map 90% reduce 0%
    18/03/16 10:41:34 INFO mapreduce.Job:  map 94% reduce 0%
    18/03/16 10:41:39 INFO mapreduce.Job:  map 99% reduce 0%
    18/03/16 10:41:40 INFO mapreduce.Job:  map 100% reduce 0%
    18/03/16 10:41:46 INFO mapreduce.Job:  map 100% reduce 6%
    18/03/16 10:41:48 INFO mapreduce.Job:  map 100% reduce 31%
    18/03/16 10:41:57 INFO mapreduce.Job:  map 100% reduce 50%
    18/03/16 10:41:58 INFO mapreduce.Job:  map 100% reduce 56%
    18/03/16 10:42:02 INFO mapreduce.Job:  map 100% reduce 63%
    18/03/16 10:42:03 INFO mapreduce.Job:  map 100% reduce 81%
    18/03/16 10:42:07 INFO mapreduce.Job:  map 100% reduce 88%
    18/03/16 10:42:09 INFO mapreduce.Job:  map 100% reduce 94%
    18/03/16 10:42:10 INFO mapreduce.Job:  map 100% reduce 100%
    18/03/16 10:42:10 INFO mapreduce.Job: Job job_1521196557010_0001 completed successfully
    18/03/16 10:42:10 INFO mapreduce.Job: Counters: 50
            File System Counters
                    FILE: Number of bytes read=5794841708
                    FILE: Number of bytes written=8661961025
                    FILE: Number of read operations=0
                    FILE: Number of large read operations=0
                    FILE: Number of write operations=0
                    HDFS: Number of bytes read=6553602048
                    HDFS: Number of bytes written=6553600000
                    HDFS: Number of read operations=96
                    HDFS: Number of large read operations=0
                    HDFS: Number of write operations=32
            Job Counters
                    Launched map tasks=16
                    Launched reduce tasks=16
                    Data-local map tasks=14
                    Rack-local map tasks=2
                    Total time spent by all maps in occupied slots (ms)=335166
                    Total time spent by all reduces in occupied slots (ms)=201906
                    Total time spent by all map tasks (ms)=335166
                    Total time spent by all reduce tasks (ms)=201906
                    Total vcore-milliseconds taken by all map tasks=335166
                    Total vcore-milliseconds taken by all reduce tasks=201906
                    Total megabyte-milliseconds taken by all map tasks=343209984
                    Total megabyte-milliseconds taken by all reduce tasks=206751744
            Map-Reduce Framework
                    Map input records=65536000
                    Map output records=65536000
                    Map output bytes=6684672000
                    Map output materialized bytes=2885076686
                    Input split bytes=2048
                    Combine input records=0
                    Combine output records=0
                    Reduce input groups=65536000
                    Reduce shuffle bytes=2885076686
                    Reduce input records=65536000
                    Reduce output records=65536000
                    Spilled Records=196608000
                    Shuffled Maps =256
                    Failed Shuffles=0
                    Merged Map outputs=256
                    GC time elapsed (ms)=10726
                    CPU time spent (ms)=531270
                    Physical memory (bytes) snapshot=22086168576
                    Virtual memory (bytes) snapshot=86284464128
                    Total committed heap usage (bytes)=21846556672
            Shuffle Errors
                    BAD_ID=0
                    CONNECTION=0
                    IO_ERROR=0
                    WRONG_LENGTH=0
                    WRONG_MAP=0
                    WRONG_REDUCE=0
            File Input Format Counters
                    Bytes Read=6553600000
            File Output Format Counters
                    Bytes Written=6553600000
    18/03/16 10:42:10 INFO terasort.TeraSort: done

    real    1m32.571s
    user    0m7.758s
    sys     0m0.374s


```

