## Day 1: Installation Lab

**Notes**

*Packages*
- nscd: Caching (Dns entries, ) 
    - Recommended for larger clusters, performance recommendation
- ntpd: Time syncronisation, consistent time thoughout the cluster.
    - Setup always required (Kudu, Hbase, Kerberos)

*FileSystem*
- File Access Time
    - Linux filesystems keep metadata that record when each file was accessed. This means that even reads result in a write to the disk. To speed up file reads, Cloudera recommends that you disable this option, called atime, using the mount option in /etc/fstab:

        `/dev/sdb1 /data1 ext4 defaults,noatime 0` Apply the change without rebooting: `mount -o remount /data1`

-  Kudu Filesystem Requirements - 
    - Kudu is supported on ext4 and XFS. Kudu requires a kernel version and filesystem that supports hole punching. Hole punching is the use of the fallocate(2) system call with the FALLOC_FL_PUNCH_HOLE option set. For more details, see Kudu troubleshooting

- MariaDB
    - FLUSH TABLES WITH READ LOCK; -> output a current snapshot of database for Replication DB to copy. -> Note: *MASTER_LOG_FILE* and *MASTER_LOG_POS* (Not required on new empty database)

## Instalation Lab

###  System Configuration Checks
#### swapiness
```

    [ec2-user@ip-172-31-28-40 ~]$ cat /etc/sysctl.conf
    vm.swappiness = 1

    [ec2-user@ip-172-31-28-40 ~]$ cat /proc/sys/vm/swappiness
    1

```

#### fstab

```

    [ec2-user@ip-172-31-28-40 ~]$ cat /etc/fstab

    #
    # /etc/fstab
    # Created by anaconda on Wed Jan  3 17:52:46 2018
    #
    # Accessible filesystems, by reference, are maintained under '/dev/disk'
    # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
    #
    UUID=3e11801e-5277-4d87-be4c-0a9a61fbc3da /                       xfs     defaults        0 0


```

#### nscd
```

    Redirecting to /bin/systemctl status nscd.service
    ● nscd.service - Name Service Cache Daemon
    Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
    Active: active (running) since Mon 2018-03-12 16:39:35 UTC; 4s ago
    Process: 12000 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
    Main PID: 12001 (nscd)
    CGroup: /system.slice/nscd.service
            └─12001 /usr/sbin/nscd

    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 monitoring file `/etc/hosts` (4)
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 monitoring directory `/etc` (2)
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 monitoring file `/etc/resolv.conf` (5)
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 monitoring directory `/etc` (2)
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 monitoring file `/etc/services` (6)
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 monitoring directory `/etc` (2)
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 disabled inotify-based monitoring for file `/etc/netgroup': No such file or directory
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 stat failed for file `/etc/netgroup'; will try again later: No such file or directory
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal nscd[12001]: 12001 Access Vector Cache (AVC) started
    Mar 12 16:39:35 ip-172-31-28-40.eu-west-2.compute.internal systemd[1]: Started Name Service Cache Daemon.

```

#### page cache

```

    [ec2-user@ip-172-31-28-40 ~]$     cat /sys/kernel/mm/transparent_hugepage/enabled
    always madvise [never]
    [ec2-user@ip-172-31-28-40 ~]$     cat /sys/kernel/mm/transparent_hugepage/defrag
    always madvise [never]


```

#### network setup

```

    [ec2-user@ip-172-31-28-40 ~]$ sudo ifconfig
    eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 9001
            inet 172.31.28.40  netmask 255.255.240.0  broadcast 172.31.31.255
            inet6 fe80::836:3fff:fec4:2610  prefixlen 64  scopeid 0x20<link>
            ether 0a:36:3f:c4:26:10  txqueuelen 1000  (Ethernet)
            RX packets 1686825  bytes 2448354658 (2.2 GiB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 267549  bytes 1560818957 (1.4 GiB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1  (Local Loopback)
            RX packets 172906  bytes 65790335 (62.7 MiB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 172906  bytes 65790335 (62.7 MiB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

    [ec2-user@ip-172-31-28-40 ~]$ netstat -i
    Kernel Interface table
    Iface      MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
    eth0      9001  1686898      0      0 0        267600      0      0      0 BMRU
    lo       65536   173630      0      0 0        173630      0      0      0 LRU

```

#### nslookup

```

    [ec2-user@ip-172-31-28-40 ~]$ nslookup ec2-35-176-157-36.eu-west-2.compute.amazonaws.com
    Server:         172.31.0.2
    Address:        172.31.0.2#53

    Non-authoritative answer:
    Name:   ec2-35-176-157-36.eu-west-2.compute.amazonaws.com
    Address: 172.31.28.40

    [ec2-user@ip-172-31-28-40 ~]$ nslookup 172.31.28.40
    Server:         172.31.0.2
    Address:        172.31.0.2#53

    Non-authoritative answer:
    40.28.31.172.in-addr.arpa       name = ip-172-31-28-40.eu-west-2.compute.internal.

```

#### ntpd

```

    Redirecting to /bin/systemctl status ntpd.service
    ● ntpd.service - Network Time Service
    Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
    Active: active (running) since Mon 2018-03-12 16:45:46 UTC; 3s ago
    Process: 12052 ExecStart=/usr/sbin/ntpd -u ntp:ntp $OPTIONS (code=exited, status=0/SUCCESS)
    Main PID: 12053 (ntpd)
    CGroup: /system.slice/ntpd.service
            └─12053 /usr/sbin/ntpd -u ntp:ntp -g

    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listen and drop on 1 v6wildcard :: UDP 123
    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listen normally on 2 lo 127.0.0.1 UDP 123
    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listen normally on 3 eth0 172.31.28.40 UDP 123
    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listen normally on 4 lo ::1 UDP 123
    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listen normally on 5 eth0 fe80::836:3fff:fec4:2610 UDP 123
    Mar 12 16:45:46 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: Listening on routing socket on fd #22 for interface updates
    Mar 12 16:45:47 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: 0.0.0.0 c016 06 restart
    Mar 12 16:45:47 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: 0.0.0.0 c012 02 freq_set kernel 0.000 PPM
    Mar 12 16:45:47 ip-172-31-28-40.eu-west-2.compute.internal ntpd[12053]: 0.0.0.0 c011 01 freq_not_set

```

