# Resource Group with VNET, Subnets, DNS, ExpressRoute, and Failover VPN

This template allows you to create a VNET with subnets to an existing Azure resource group. **NOTE:** Resource group must be created first.

This allows the complete fresh or incremental creation of a VNET with subnets in a single region as part of a resource group.

Steps
####
This template allows you to create an Azure VNET with multiple subnets, private (non-Azure) DNS, and a site-to-site VPN tunnel with multiple local address prefixes to an existing Azure resource group in a single Azure region.   
This effectively can be an "Azure private VPC data center in a box" automation.  It is incredibly powerful.

**NOTES:** 
* Resource group must be created first.  This example/template uses West US, but you can change any parameter to meet your requirements.  
* The creation from scratch (first time execution) of this template can take up to 35-40 minutes or longer to run.  
* The service provider circuit side of the connection must be prepared first.  If not, the template will complete, but with a deployment error.  
* Azure has a deployment dependency when using Expressroute + an IPSec VPN.  This dependency looks as follows:  
   a. Expressroute gateway must be created FIRST.
     - If a VPN gateway already exists, it will need to be deleted and then recreated as part of this template.
   b. The IPSec VPN tunnel can only function in an active/standby deployment model.  
     - In other words, when using Expressroute, the Expressroute circuit is always taken, and the VPN is only used if the express route is down.
* The default mode of creation using the Azure cross platform CLI is assumed and that the arm mode is incremental.  



**Steps** 
1. ```azure config mode arm```  
2. ```azure group create -n "MY-VNET-RG1" -l "West US"```  
3. Select your deployment approach for template and parameter files:  

**Local current directory for template & params file:**
```
azure group deployment create -g MY-VNET-RG1 -n MY-VNET-DEPLOYMENT -vv -f \
azuredeploy.json -e \
azuredeploy.parameters.json
```  


Troubleshoot a deployment:
----------------------------
```
azure group log show MY-VNET-RG1 --last-deployment
```  

```
azure group log show MY-VNET-RG1 --json | jq -r ".[] | select(.status.value == \"Failed\") | .properties.statusMessage"
```  

```
azure group log show MY-VNET-RG1 --json | jq '.[] | select(.status.value == "Failed")'
```  

```
azure group deployment show --resource-group MY-VNET-RG1 --name MY-VNET-DEPLOYMENT
```  




