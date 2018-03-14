{
  "timestamp" : "2018-03-14T09:20:25.439Z",
  "clusters" : [ {
    "name" : "JenYinOrdina",
    "version" : "CDH5",
    "services" : [ {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "676331520"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cw4pu79quw18r4357tjqxuo8f"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-392acebf82f710189d2ada116fef0096",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "b203455e-a76b-4390-89e6-656299c7d6b3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "c1bo1oqvax3i8h0kuemeldt4j"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "zi72jrbd5zjpn531ifdi3e2x"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "cdh-server-0.localdomain"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie_password"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "676331520"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e5s8ianv2tweicj7zpz483euo"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "cdh-server-0.localdomain"
        }, {
          "name" : "database_password",
          "value" : "hue_password"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-31f6f633a7bf9bdb274625f349a22ec3"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2r0itpijfupf3ixepmfg3gvjk"
          }, {
            "name" : "secret_key",
            "value" : "vkYPYVxiENPdOWgdAuZdZVe70IIppp"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "676331520"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "5367448780"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "400"
          }, {
            "name" : "rm_io_weight",
            "value" : "200"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "676331520"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "676331520"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "qqiqT0ZJ9xwv0rJ88LFAuZ8EHNhnmU"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "5b8UP4uKrqugMytw8XPqAJNxHJwa12"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "kOFGaT3lo0yGfRnrBRXnr5UOsI0bpe"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "20"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-392acebf82f710189d2ada116fef0096",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "b203455e-a76b-4390-89e6-656299c7d6b3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8p75m8blfvd6hsioko0trm1gd"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-3b7e392877bf7e3a2ac7ae18e423017a",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "47f88726-e3e4-4919-bc26-f2ef2d72b32a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dc06kna8yym25ivce4ndjif99"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cxcx3xmo0jwcpedpirnm2nrn5"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bdqz9bo8db82ct8urcdxwhr25"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4j9w02bxjzqf8ubdx063mm9w7"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6axumpw7hvdda8kyhzbztob2"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-392acebf82f710189d2ada116fef0096",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "b203455e-a76b-4390-89e6-656299c7d6b3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ardh1bl11kso1gwd9twv71jh2"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-3b7e392877bf7e3a2ac7ae18e423017a",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "47f88726-e3e4-4919-bc26-f2ef2d72b32a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "832j16nkmd1oefk650df0i5at"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e71qp54aqid1737jkilcb3j5l"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "40"
          }, {
            "name" : "role_jceks_password",
            "value" : "b11b3xi5slwwsxrm5r5u99r56"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "54"
          }, {
            "name" : "role_jceks_password",
            "value" : "4bgiexvrxs1md4xod2xl6uang"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "676331520"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1600"
          }, {
            "name" : "rm_io_weight",
            "value" : "800"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "2904"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "676331520"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4913"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "80"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "ftP6Gjheb7IGYUlBIrtqSvu8JDP0zW"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "707mq4etn8079rcby6jhpyk1"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-392acebf82f710189d2ada116fef0096",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "b203455e-a76b-4390-89e6-656299c7d6b3"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5k7fam2sd2eh0jqaggmzjk4ge"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-3b7e392877bf7e3a2ac7ae18e423017a",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "47f88726-e3e4-4919-bc26-f2ef2d72b32a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bm63plrbitbxcqbhkptutj665"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dqkh1z7p5stmf75l7wctizf3p"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "46"
          }, {
            "name" : "role_jceks_password",
            "value" : "aao849oh7tabtgxn60o45zorw"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "676331520"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "676331520"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3786198220"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "637"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "cdh-server-0.localdomain"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive_password"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-392acebf82f710189d2ada116fef0096",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "b203455e-a76b-4390-89e6-656299c7d6b3"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-3b7e392877bf7e3a2ac7ae18e423017a",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "47f88726-e3e4-4919-bc26-f2ef2d72b32a"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-b83ba01d7a5c3cad50704422b24ec7c4",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1cbnn2d9buexy11xnmzcbr847"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-31f6f633a7bf9bdb274625f349a22ec3",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "178ixcd7902wrhbs4vykf66cw"
          } ]
        }
      } ],
      "displayName" : "Hive"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322",
    "ipAddress" : "172.31.27.86",
    "hostname" : "cdh-agent-0.localdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "00c9e0d2-9c78-447b-9056-54968269f4ac",
    "ipAddress" : "172.31.24.1",
    "hostname" : "cdh-agent-1.localdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "b203455e-a76b-4390-89e6-656299c7d6b3",
    "ipAddress" : "172.31.20.84",
    "hostname" : "cdh-agent-2.localdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "47f88726-e3e4-4919-bc26-f2ef2d72b32a",
    "ipAddress" : "172.31.23.67",
    "hostname" : "cdh-agent-3.localdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "JeKuOrdina",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "32785f69570e5756568d90df68aa61a93d6e8932b28fbe38676f1a0c505561cd",
    "pwSalt" : -3802078735754713524,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-31f6f633a7bf9bdb274625f349a22ec3",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "36faed07e40f1193eea6dd8955d0c7a35520c5498efe5ec68db3b7803ee473f3",
    "pwSalt" : 4481731829198754390,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-31f6f633a7bf9bdb274625f349a22ec3",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "2721300ff1680e8648fc1384d5ed8f48a1e36654cc6e34c6293cf5ba67bcaa05",
    "pwSalt" : 6025254589396673677,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-31f6f633a7bf9bdb274625f349a22ec3",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "8475afd95a7ecb22dbdd1366b9a7797dcbaba5d4826e1e0eeafc951403a58427",
    "pwSalt" : 3147988467814618313,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-31f6f633a7bf9bdb274625f349a22ec3",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "77723023ae0189147e7ba14229c72568d686167bb7bfff911d2659ee6cc73dad",
    "pwSalt" : -8840804836785493012,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "ee50bb853c46ac0dbdc590cbe9a528b15a23da21c6de90116a7277f2040035b6",
    "pwSalt" : -7441200684496724258,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "17e8159ced0755c6b9b98fb15564a21741a43acfd1b6efa20c39582f5907528f",
    "pwSalt" : 1509109975249391918,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.9.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170627-1506",
    "gitHash" : "23506bb4e114dd460bdac64c57a672e6be631907",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "676331520"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "676331520"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "879755264"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "cdh-server-0.localdomain"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman_password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "676331520"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "879755264"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-31f6f633a7bf9bdb274625f349a22ec3",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "b06vriowx1mkg2w8b2xcojiog"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-31f6f633a7bf9bdb274625f349a22ec3",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "2flkha9bdfn50kqsqlsnxiiit"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-31f6f633a7bf9bdb274625f349a22ec3",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "85cl314ze3wcdiyc3z2xumfmm"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-31f6f633a7bf9bdb274625f349a22ec3",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "eboi5015d0ohy47swu24qkdyy"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-31f6f633a7bf9bdb274625f349a22ec3",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "b482f493-1d5a-4e3b-bcb4-4f51c4bb4322"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "c2c8dfwd7rdi9jonr783qvc22"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/22/2012 23:30"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}