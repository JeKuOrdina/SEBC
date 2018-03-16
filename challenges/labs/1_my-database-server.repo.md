### Install MariaDB

`sudo yum repolist enabled`

```
    Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
    repo id                                                                          repo name                                                                                       status
    rhui-REGION-client-config-server-7/x86_64                                       Red Hat Update Infrastructure 2.0 Client Configuration Server 7                                      2
    rhui-REGION-rhel-server-releases/7Server/x86_64                                 Red Hat Enterprise Linux Server 7 (RPMs)                                                        18,257
    rhui-REGION-rhel-server-rh-common/7Server/x86_64                                Red Hat Enterprise Linux Server 7 RH Common (RPMs)                                                 231
```


On cdh-mgt-0 execute:

```

    sudo yum install -y mariadb-server
    sudo systemctl enable mariadb
    sudo service mariadb start

```

### Create databases:

In Mysql create the following databases

```

    create database scm default character set utf8 default collate utf8_general_ci;
    grant all on scm.* to 'scm'@'%' identified by 'scm_password';

    create database rman DEFAULT CHARACTER SET utf8;
    grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman_password';

    create database metastore DEFAULT CHARACTER SET utf8;
    grant all on metastore.* TO 'hive'@'%' IDENTIFIED BY 'hive_password';

    create database hue default character set utf8 default collate utf8_general_ci;
    grant all on hue.* to 'hue'@'%' identified by 'hue_password';

    create database oozie default character set utf8;
    grant all privileges on oozie.* to 'oozie'@'localhost' identified by 'oozie';
    grant all privileges on oozie.* to 'oozie'@'%' identified by 'oozie_password';

```

### DB setup

`hostname` : cdh-mgt-0.localdomain
`mysql --version` mysql  Ver 15.1 Distrib 5.5.56-MariaDB, for Linux (x86_64) using readline 5.1
`mysql -uroot -proot
`
```
    MariaDB [(none)]> show databases;

    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | hue                |
    | metastore          |
    | mysql              |
    | oozie              |
    | performance_schema |
    | rman               |
    | scm                |
    +--------------------+
    8 rows in set (0.00 sec)
```