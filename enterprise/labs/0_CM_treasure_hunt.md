## CM Monitoring Lab
### What is ubertask optimization?

Optimisation for map-reduce jobs.

From the yarn documentations: Search > ubertask

> Whether to enable ubertask optimization, which runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the 
> mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.

### Where in CM is the Kerberos Security Realm value displayed?

Search > Kerberos Security Realm: From Administration > Kerberos > Kerberos Security Realm

> HADOOP.COM

### Which CDH service(s) host a property for enabling Kerberos authentication?

Search > "Kerberos enable"

Yarn, HDFS, Oozie, Hue, Zookeeper, Hive

### How do you upgrade the CM agents?

All Hosts > Rerun upgrade wizard

### Give the tsquery statement used to chart Hue's CPU utilization?

Query:

    `SELECT * WHERE entityName = "hue-HUE_SERVER-31f6f633a7bf9bdb274625f349a22ec3" AND category = ROLE`

Search for cpu related info: (Same chart as in chartbuilder)

    `SELECT cpu_system_rate + cpu_user_rate WHERE entityName = "hue-HUE_SERVER-31f6f633a7bf9bdb274625f349a22ec3" AND category = ROLE`

### Name all the roles that make up the Hive service?


- Gateway 	
- Hive Metastore Server 
- HiveServer2 	


### What steps must be completed before integrating Cloudera Manager with Kerberos?



- Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.
- The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.
- OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.
- Cloudera Manager needs an account that has permissions to create other accounts in the KDC.

    