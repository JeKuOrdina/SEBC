### Provider

- AWS | m5.xlarge

-----

### IP

| private ip    | private dns                                 | alias
|---------------|:-------------------------------------------:|-----------
| 172.31.29.241 | ip-172-31-29-241.eu-west-2.compute.internal | cdh-mgt-0
| 172.31.23.151 | ip-172-31-23-151.eu-west-2.compute.internal | cdh-mgt-1
| 172.31.16.21  | ip-172-31-16-21.eu-west-2.compute.internal  | cdh-wkt-0
| 172.31.31.101 | ip-172-31-31-101.eu-west-2.compute.internal | cdh-wkt-1
| 172.31.29.238 | ip-172-31-29-238.eu-west-2.compute.internal | cdh-wkt-2

-----

### OS 

`cat /etc/redhat-release`

Red Hat Enterprise Linux Server release 7.4 (Maipo)

--------

### FileSystem Capacity

` lsblk `

```
    NAME        MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
    nvme0n1     259:0    0  50G  0 disk
    ├─nvme0n1p1 259:1    0   1M  0 part
    └─nvme0n1p2 259:2    0  50G  0 part /
```

### RepoList

`sudo yum repolist enabled`

```
    Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
    repo id                                                                          repo name                                                                                       status
    rhui-REGION-client-config-server-7/x86_64                                       Red Hat Update Infrastructure 2.0 Client Configuration Server 7                                      2
    rhui-REGION-rhel-server-releases/7Server/x86_64                                 Red Hat Enterprise Linux Server 7 (RPMs)                                                        18,257
    rhui-REGION-rhel-server-rh-common/7Server/x86_64                                Red Hat Enterprise Linux Server 7 RH Common (RPMs)                                                 231
```

### Adduser and Addgroup

On all nodes execute:

```
sudo groupadd analytics
sudo groupadd datasci
sudo useradd -u 2900 anupam -g analytics
sudo useradd -u 2800 hilary -g datasci
```

Result of `cat /etc/passwd`

```

    anupam:x:2900:1001::/home/anupam:/bin/bash
    hilary:x:2800:1002::/home/hilary:/bin/bash

```

Result of `cat /etc/group`

```

    analytics:x:1001:
    datasci:x:1002:

```

