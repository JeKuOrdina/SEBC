### Unauthorized user

```

    beeline> !connect "jdbc:hive2://cdh-agent-0:10000/default;principal=hive/cdh-agent-0.localdomain@EXAMPLE.COM"
    scan complete in 2ms
    Connecting to jdbc:hive2://cdh-agent-0:10000/default;principal=hive/cdh-agent-0.localdomain@EXAMPLE.COM
    18/03/15 08:45:51 [main]: ERROR transport.TSaslTransport: SASL negotiation failure
    javax.security.sasl.SaslException: GSS initiate failed [Caused by GSSException: No valid credentials provided (Mechanism level: Failed to find any Kerberos tgt)]


```

### Authorised user


```

    beeline> !connect "jdbc:hive2://cdh-agent-0:10000/default;principal=hive/cdh-agent-0.localdomain@EXAMPLE.COM"
    scan complete in 2ms
    Connecting to jdbc:hive2://cdh-agent-0:10000/default;principal=hive/cdh-agent-0.localdomain@EXAMPLE.COM
    Connected to: Apache Hive (version 1.1.0-cdh5.9.3)
    Driver: Hive JDBC (version 1.1.0-cdh5.9.3)
    Transaction isolation: TRANSACTION_REPEATABLE_READ
    0: jdbc:hive2://cdh-agent-0:10000/default> SHOW TABLES;
    INFO  : OK
    +-----------+--+
    | tab_name  |
    +-----------+--+
    +-----------+--+
    No rows selected (2.228 seconds)

```

### Role and Rights

```

    CREATE ROLE reads;
    CREATE ROLE writes;


    GRANT SELECT ON DATABASE default TO ROLE reads;
    GRANT ROLE reads TO GROUP selector;

    REVOKE ALL ON DATABASE default FROM ROLE writes;
    GRANT INSERT ON default.sample_07 TO ROLE writes;
    GRANT ROLE writes TO GROUP inserters;


```

```

    0: jdbc:hive2://cdh-agent-0:10000/default> CREATE ROLE sentry_admin;
    INFO  : OK
    No rows affected (0.499 seconds)
    0: jdbc:hive2://cdh-agent-0:10000/default> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
    INFO  : OK
    No rows affected (0.173 seconds)
    0: jdbc:hive2://cdh-agent-0:10000/default> GRANT ROLE sentry_admin TO GROUP jovv;
    INFO  : OK
    0: jdbc:hive2://cdh-agent-0:10000/default> SHOW TABLES;
    INFO  : OK
    +------------+--+
    |  tab_name  |
    +------------+--+
    | customers  |
    | sample_07  |
    | sample_08  |
    | web_logs   |
    +------------+--+
    4 rows selected (0.285 seconds)

```

### User creation and roles

#### george
```

0: jdbc:hive2://cdh-agent-0:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20180315085858_f15d3bc7-07fa-4fb7-9c0a-d3e030c69870): show tables
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.234 seconds)

```

#### ferdinand

```

    0: jdbc:hive2://cdh-agent-0:10000/default> show tables
    INFO  : OK
    +------------+--+
    |  tab_name  |
    +------------+--+
    | sample_07  |
    +------------+--+


```