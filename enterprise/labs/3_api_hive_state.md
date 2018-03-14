
`
curl -X GET -u JeKuOrdina:cloudera 'http://ec2-35-177-155-59.eu-west-2.compute.amazonaws.com:7180/api/v14/clusters/JenYinOrdina/services/hive/'
`

```
	
    name	"hive"
    type	"HIVE"
    clusterRef	
    clusterName	"cluster"
    serviceUrl	"http://cdh-server-0.localdomain:7180/cmf/serviceRedirect/hive"
    roleInstancesUrl	"http://cdh-server-0.localdomain:7180/cmf/serviceRedirect/hive/instances"
    serviceState	"STARTED"
    healthSummary	"GOOD"
    healthChecks	
    0	
    name	"HIVE_HIVEMETASTORES_HEALTHY"
    summary	"GOOD"
    suppressed	false
    1	
    name	"HIVE_HIVESERVER2S_HEALTHY"
    summary	"GOOD"
    suppressed	false
    configStalenessStatus	"FRESH"
    clientConfigStalenessStatus	"FRESH"
    maintenanceMode	false
    maintenanceOwners	[]
    displayName	"Hive"
    entityStatus	"GOOD_HEALTH"

```