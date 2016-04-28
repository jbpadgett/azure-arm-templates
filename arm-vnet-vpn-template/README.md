# Resource Group with VNET, Subnets, DNS, and VPN

This template allows you to create an Azure VNET with multiple subnets, private (non-Azure) DNS, and a site-to-site VPN tunnel with multiple local address prefixes to an existing Azure resource group in a single Azure region.   
This effectively can be an "Azure private VPC data center in a box" automation.  It is incredibly powerful.

**NOTES:** 
* Resource group must be created first.  
* The creation from scratch (first time execution) of this template can take up to 35-40 minutes.  
* The default mode of creation using the Azure cross platform CLI is assumed and that the arm mode is incremental.  



**Steps**
1. ```azure config mode arm```
2. ```azure group create -n "MY-VNET-RG1" -l "West US"```
3. Select your deployment approach for template and parameter files:

**Local current dir for template & params file:**
```
azure group deployment create -g MY-VNET-RG1 -n MY-VNET-DEPLOYMENT -vv -f \
azuredeploy.json -e \
azuredeploy.parameters.json
```  



One click Deploy to Azure:  
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/http%3A%2F%2github.com%2Fraw%2Fjbpadgett%2FFmaster%2Fazure-arm-templates%2Farm-vnet-vpn-template%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>  

One Click View of template objects:  
<a href="http://armviz.io/#/?load=http%3A%2F%2github.com%2Fraw%2Fjbpadgett%2FFmaster%2Fazure-arm-templates%2Farm-vnet-vpn-template%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>




