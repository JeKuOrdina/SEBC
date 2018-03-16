
[root@cdh-mgt-1 ~]# kinit anupam
Password for anupam@JEKUORDINA.NL:
[root@cdh-mgt-1 ~]# time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 50 100


Error due to wrong ownership of folder anupam, access=WRITE, inode="/user/anupam":*anunpam*:*anupam*
```

    org.apache.hadoop.security.AccessControlException: Permission denied: user=anupam, access=WRITE, inode="/user/anupam":anunpam:anupam:drwxr-xr-x
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.checkFsPermission(DefaultAuthorizationProvider.java:279)
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.check(DefaultAuthorizationProvider.java:260)
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.check(DefaultAuthorizationProvider.java:240)
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.checkPermission(DefaultAuthorizationProvider.java:162)
            at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkPermission(FSPermissionChecker.java:152)
            at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:3877)
            at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:3860)
            at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkAncestorAccess(FSDirectory.java:3842)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.checkAncestorAccess(FSNamesystem.java:6731)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.mkdirsInternal(FSNamesystem.java:4496)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.mkdirsInt(FSNamesystem.java:4466)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.mkdirs(FSNamesystem.java:4439)
            at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.mkdirs(NameNodeRpcServer.java:876)
            at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.mkdirs(AuthorizationProviderProxyClientProtocol.java:326)
            at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.mkdirs(ClientNamenodeProtocolServerSideTranslatorPB.java:640)
            at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
            at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
            at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
            at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2226)
            at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2222)
            at java.security.AccessController.doPrivileged(Native Method)
            at javax.security.auth.Subject.doAs(Subject.java:422)
            at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1920)
            at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2220)

            at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
            at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
            at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
            at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
            at org.apache.hadoop.ipc.RemoteException.instantiateException(RemoteException.java:106)
            at org.apache.hadoop.ipc.RemoteException.unwrapRemoteException(RemoteException.java:73)
            at org.apache.hadoop.hdfs.DFSClient.primitiveMkdir(DFSClient.java:3134)
            at org.apache.hadoop.hdfs.DFSClient.mkdirs(DFSClient.java:3099)
            at org.apache.hadoop.hdfs.DistributedFileSystem$19.doCall(DistributedFileSystem.java:1004)
            at org.apache.hadoop.hdfs.DistributedFileSystem$19.doCall(DistributedFileSystem.java:1000)
            at org.apache.hadoop.fs.FileSystemLinkResolver.resolve(FileSystemLinkResolver.java:81)
            at org.apache.hadoop.hdfs.DistributedFileSystem.mkdirsInternal(DistributedFileSystem.java:1000)
            at org.apache.hadoop.hdfs.DistributedFileSystem.mkdirs(DistributedFileSystem.java:992)
            at org.apache.hadoop.fs.FileSystem.mkdirs(FileSystem.java:1970)
            at org.apache.hadoop.examples.QuasiMonteCarlo.estimatePi(QuasiMonteCarlo.java:282)
            at org.apache.hadoop.examples.QuasiMonteCarlo.run(QuasiMonteCarlo.java:354)
            at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
            at org.apache.hadoop.examples.QuasiMonteCarlo.main(QuasiMonteCarlo.java:363)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
            at java.lang.reflect.Method.invoke(Method.java:498)
            at org.apache.hadoop.util.ProgramDriver$ProgramDescription.invoke(ProgramDriver.java:71)
            at org.apache.hadoop.util.ProgramDriver.run(ProgramDriver.java:144)
            at org.apache.hadoop.examples.ExampleDriver.main(ExampleDriver.java:74)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
            at java.lang.reflect.Method.invoke(Method.java:498)
            at org.apache.hadoop.util.RunJar.run(RunJar.java:221)
            at org.apache.hadoop.util.RunJar.main(RunJar.java:136)
    Caused by: org.apache.hadoop.ipc.RemoteException(org.apache.hadoop.security.AccessControlException): Permission denied: user=anupam, access=WRITE, inode="/user/anupam":anunpam:anupam:drwxr-xr-x
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.checkFsPermission(DefaultAuthorizationProvider.java:279)
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.check(DefaultAuthorizationProvider.java:260)
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.check(DefaultAuthorizationProvider.java:240)
            at org.apache.hadoop.hdfs.server.namenode.DefaultAuthorizationProvider.checkPermission(DefaultAuthorizationProvider.java:162)
            at org.apache.hadoop.hdfs.server.namenode.FSPermissionChecker.checkPermission(FSPermissionChecker.java:152)
            at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:3877)
            at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkPermission(FSDirectory.java:3860)
            at org.apache.hadoop.hdfs.server.namenode.FSDirectory.checkAncestorAccess(FSDirectory.java:3842)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.checkAncestorAccess(FSNamesystem.java:6731)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.mkdirsInternal(FSNamesystem.java:4496)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.mkdirsInt(FSNamesystem.java:4466)
            at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.mkdirs(FSNamesystem.java:4439)
            at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.mkdirs(NameNodeRpcServer.java:876)
            at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.mkdirs(AuthorizationProviderProxyClientProtocol.java:326)
            at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.mkdirs(ClientNamenodeProtocolServerSideTranslatorPB.java:640)
            at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
            at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:617)
            at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1073)
            at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2226)
            at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2222)
            at java.security.AccessController.doPrivileged(Native Method)
            at javax.security.auth.Subject.doAs(Subject.java:422)
            at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1920)
            at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2220)

            at org.apache.hadoop.ipc.Client.call(Client.java:1504)
            at org.apache.hadoop.ipc.Client.call(Client.java:1441)
            at org.apache.hadoop.ipc.ProtobufRpcEngine$Invoker.invoke(ProtobufRpcEngine.java:230)
            at com.sun.proxy.$Proxy10.mkdirs(Unknown Source)
            at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolTranslatorPB.mkdirs(ClientNamenodeProtocolTranslatorPB.java:573)
            at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
            at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
            at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
            at java.lang.reflect.Method.invoke(Method.java:498)
            at org.apache.hadoop.io.retry.RetryInvocationHandler.invokeMethod(RetryInvocationHandler.java:258)
            at org.apache.hadoop.io.retry.RetryInvocationHandler.invoke(RetryInvocationHandler.java:104)
            at com.sun.proxy.$Proxy11.mkdirs(Unknown Source)
            at org.apache.hadoop.hdfs.DFSClient.primitiveMkdir(DFSClient.java:3132)
            ... 24 more

    real    0m2.240s
    user    0m3.797s
    sys     0m0.227s


```

