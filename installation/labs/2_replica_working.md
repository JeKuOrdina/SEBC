### Mysql replication

```

    MariaDB [(none)]> SHOW SLAVE STATUS \G
    *************************** 1. row ***************************
                Slave_IO_State: Waiting for master to send event
                    Master_Host: cdh-server-0
                    Master_User: root
                    Master_Port: 3306
                    Connect_Retry: 10
                Master_Log_File: master1-bin.000003
            Read_Master_Log_Pos: 38679474
                Relay_Log_File: mariadb-relay-bin.000002
                    Relay_Log_Pos: 26875
            Relay_Master_Log_File: master1-bin.000001
                Slave_IO_Running: Yes
                Slave_SQL_Running: No
                Replicate_Do_DB:
            Replicate_Ignore_DB:
            Replicate_Do_Table:
        Replicate_Ignore_Table:
        Replicate_Wild_Do_Table:
    Replicate_Wild_Ignore_Table:
                    Last_Errno: 1062
                    Last_Error: Could not execute Write_rows event on table mysql.user; Duplicate entry 'localhost-root' for key 'PRIMARY', Error_code: 1062; handler error HA_ERR_FOUND_DUPP_KEY; the event's master log master1-bin.000001, end_log_pos 27368
                    Skip_Counter: 0
            Exec_Master_Log_Pos: 26589
                Relay_Log_Space: 39748008
                Until_Condition: None
                Until_Log_File:
                    Until_Log_Pos: 0
            Master_SSL_Allowed: No
            Master_SSL_CA_File:
            Master_SSL_CA_Path:
                Master_SSL_Cert:
                Master_SSL_Cipher:
                Master_SSL_Key:
            Seconds_Behind_Master: NULL
    Master_SSL_Verify_Server_Cert: No
                    Last_IO_Errno: 0
                    Last_IO_Error:
                Last_SQL_Errno: 1062
                Last_SQL_Error: Could not execute Write_rows event on table mysql.user; Duplicate entry 'localhost-root' for key 'PRIMARY', Error_code: 1062; handler error HA_ERR_FOUND_DUPP_KEY; the event's master log master1-bin.000001, end_log_pos 27368
    Replicate_Ignore_Server_Ids:
                Master_Server_Id: 1

```