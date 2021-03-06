# Azure ARM Templates for Deploying a VNET, subnets, DNS, Expressroute, and VPN
Azure resource manager templates for deployments to the Azure cloud.
There are 3 templates available.
Each Template does differnet networking models, but do the following commmon tasks:
* Create VNET
* Create subnets inside the VNET
* Setup private DNS servers for the VNET subnets

There are then 3 differnet networking options:
* IPSec VPN only from VNET to your private data center/campus
* Expressroute only from VNET to your private data center/campus
* Expressroute + IPSec VPN from VNET to your private data center/campus


This template allows you to create a VNET with subnets, custom DNS, and ipsec VPN to an existing Azure resource group. 
**NOTE:** Resource group must be created first.

This allows the complete fresh or incremental creation of a VNET with subnets in a single region as part of a resource group.

Steps
####
1. ```azure config mode arm```
2. ```azure group create -n "MY-VNET-RG" -l "West US"```
3. Select your deployment approach for template and parameter files:

Http URI + local current dir for params file:
------------------------------------------------
```azure group deployment create --template-uri \
http://github.com/raw/path/to/template/azuredeploy.json -e \
azuredeploy.parameters.json \
-g MY-VNET-RG -n MY-VNET-DEPLOYMENT -vv```


Local current dir for template & params file:
-----------------------------------------------
```azure group deployment create -g MY-VNET-RG1 -n MY-VNET-DEPLOYMENT -vv -f \
azuredeploy.json -e \
azuredeploy.parameters.json```  



Troubleshoot a deployment:
----------------------------
```
azure group log show MY-VNET-RG --last-deployment
```  

```
azure group log show MY-VNET-RG --json | jq -r ".[] | select(.status.value == \"Failed\") | .properties.statusMessage"
```  

```
azure group log show MY-VNET-RG --json | jq '.[] | select(.status.value == "Failed")'
```  

```
azure group deployment show --resource-group MY-VNET-RG --name MY-VNET-DEPLOYMENT
```  
