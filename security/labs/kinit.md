
```
[ec2-user@cdh-agent-3 ~]$ kinit jovv
```

```
[ec2-user@cdh-agent-3 ~]$ klist -e -f
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: jovv@EXAMPLE.COM

Valid starting       Expires              Service principal
03/14/2018 16:25:37  03/15/2018 16:25:37  krbtgt/EXAMPLE.COM@EXAMPLE.COM
        renew until 03/21/2018 16:25:37, Flags: FRI
        Etype (skey, tkt): arcfour-hmac, aes256-cts-hmac-sha1-96

```