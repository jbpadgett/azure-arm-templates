# Create Site to Site VPN via Resource Group

This template allows you to build a site-to-site VPN using a resource group, existing VNET and subnets.  
**NOTE:** Deploy into the resource group of the existing VNET.



Deployment Steps
-------------------
1. ```azure config mode arm```
2. ```azure group create -n "MY-VNET-RG1" -l "West US"```
3. Select your deployment approach for template and parameter files:


Local current dir for template & params file:
-----------------------------------------------
```azure group deployment create -g MY-VNET-RG1 -n MY-S2S-VPN-DEPLOYMENT -vv -f \
azuredeploy.json -e \
azuredeploy.parameters.json```  




One click Deploy to Azure:  
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/http%3A%2F%2github.gapinc.dev%2Fraw%2Fje9g28w%2Fazure-vpc%2Fmaster%2Farm-templates%2Farm-vpn-westus-region%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>  

One Click View of template objects:  
<a href="http://armviz.io/#/?load=http%3A%2F%2github.gapinc.dev%2Fraw%2Fje9g28w%2Fazure-vpc%2Fmaster%2Farm-templates%2Farm-vpn-westus-region%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

