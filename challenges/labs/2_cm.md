

### List repo

`sudo yum repolist enabled` [Cloudera Director for jdk_8]

```
    Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
    repo id                                                                          repo name                                                                                       status
    cloudera-director                                                               Cloudera Director                                                                                    5
    rhui-REGION-client-config-server-7/x86_64                                       Red Hat Update Infrastructure 2.0 Client Configuration Server 7                                      2
    rhui-REGION-rhel-server-releases/7Server/x86_64                                 Red Hat Enterprise Linux Server 7 (RPMs)                                                        18,257
    rhui-REGION-rhel-server-rh-common/7Server/x86_64                                Red Hat Enterprise Linux Server 7 RH Common (RPMs)                                                 231
```

-------------

### Install scm database

On cdh-mgt-1 execute: `sudo /usr/share/cmf/schema/scm_prepare_database.sh mysql -h ip-172-31-29-241.eu-west-2.compute.internal --scm-host ip-172-31-23-151.eu-west-2.compute.internal scm scm scm_password`

```

    JAVA_HOME=/usr/java/jdk1.8.0_121-cloudera
    Verifying that we can write to /etc/cloudera-scm-server
    Creating SCM configuration file in /etc/cloudera-scm-server
    Executing:  /usr/java/jdk1.8.0_121-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
    [                          main] DbCommandExecutor              INFO  Successfully connected to database.
    All done, your SCM database is configured correctly!

```