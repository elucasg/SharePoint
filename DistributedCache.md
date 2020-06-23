Get the list of Distributed Cache Service instances:

`Get-SPServiceInstance | Where {$_.Typename -like “Distributed Cache”} | Select TypeName, Status, ID, Server | Format-List`

Remove a Distributed Cache instance (run from the server running the instance):

```
$SPFarm = Get-SPFarm
$cacheClusterName = "SPDistributedCacheCluster_" + $SPFarm.Id.ToString() 
$cacheClusterManager = [Microsoft.SharePoint.DistributedCaching.Utilities.SPDistributedCacheClusterInfoManager]::Local 
$cacheClusterInfo = $cacheClusterManager.GetSPDistributedCacheClusterInfo($cacheClusterName);
$instanceName ="SPDistributedCacheService Name=AppFabricCachingService"
$serviceInstance = Get-SPServiceInstance | ? {($_.Service.Tostring()) -eq $instanceName -and ($_.Server.Name) -eq $env:computername}  
$serviceInstance.Delete()
```
