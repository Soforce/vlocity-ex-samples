# Use Lightning Flow in Vlocity OM
## Overview
This tutorial demonstrates how to use Lighting flow in Vlociyt OM. In the sample Lightning flow, it reads "ReliesOnItemId__c" field from the order item and updates it into the "Relies On" attribute of fulfilment request line decomposed from the given order item.

**Metadata included for this tutorial**  
*  `ve_sample_Use_Flow_in_OM` - Lightning Flow
*  `OrchestrationPlanDefinition/ve-sample-Use-Flow-in-OM` - Vlocity Orchestration Plan Definition
*  `OrchestrationItemDefinition/Test-OM-Flow_ve-sample-Use-Flow-in-OM` - Vlocity Orchestration Item Definition
*  `Product2/26e1ed65-5197-86d1-2eb6-79fe6e2cf569` - EVC CFS Product which contains the plan scenario

## Prerequisite
You need a VDO (Vlocity Demo Org) org to work on this tutorial. You also need to install SFDX and Vlocity Build Tool on your computer.
1. Sign up a VDO (Vlocity Demo Org) org for your exercise if you don't have one. You can open "https://vdo.force.com" to apply a VDO org for yourself. Please select "Commmunications" in the "Industry" field.
2. Install [Salesforce CLI Command](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference.htm). You can follow the [Install the Salesforce CLI](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_install_cli.htm) to complete the installation.
3. Install [Vlocity Build Tool](https://github.com/vlocityinc/vlocity_build#vlocity-build). You can follow the [Installation and Update Instructions](https://github.com/vlocityinc/vlocity_build#installation-and-update-instructions) to complete the installation.
4. Authorize your VDO org by SFDX. `sfdx force:auth:web:login --setalias {VDOAlias}`
5. Configure Vlocity OM on your VDO org if you have not.
*  Open "Vlocity XOM Administration" tab
*  Click "Configure for Order Management Standard"
*  Click "Start" for "APPLY RECORED TYPES AND PAGE LAYOUT ASSIGNMENTS"
*  Select "XOM Admin" for System Administrator and click "Update" button

## Install and Configure [Vlocity Extension (Vlocity-ex)](https://github.com/Soforce/vlocity-ex#vlocity-extension-vlocity-ex-package) Package
You need to install and configure the vlocity-ex package into your VDO org to complete this tutorial if you have not. You can follow [Install & Configure Vlocity-ex Package](https://github.com/Soforce/vlocity-ex#install--configure-vlocity-ex-package) to complete the installation and configuration.

## Install & deploy the "Use Lightning Flow in Vlocity OM" tutorial
1. You also can deploy the [tutorial-init](../tutorial-init/datapacks/tutorial-init.json) datapack to install sample product catalogs to help you run the tutorial. You can reference [Deploy "tutorial-init" datapack](https://github.com/Soforce/vlocity-ex-tutorials/tree/master/tutorial-init#deploy-tutorial-init-datapack) for details.
2. Download or clone the [vlocity-ex-tutorials](https://github.com/Soforce/vlocity-ex-tutorials) GitHub repository into your computer.
3. Open Windows Command Line or Mac OS Terminal into the folder where you download the "vlocity-ex-tutorials" repo.
4. Change directory (`cd tutorial-init`) into the "tutorial-init" sub-folder and execute the following VBT command to deploy the initial datapack to be used by the tutorial. 
```
vlocity -job project.yaml packDeploy -sfdx.username={VDOAlias}
```
5. Change directory (`cd ../om-use-flow`) into the "om-use-flow" folder.
6. Execute the following SFDX command to deploy the tutorial flow into your VDO org.
```
sfdx force:source:deploy -p force-app -u {VDOAlias}
```
7. Execute the following VBT command to deploy vlocity datapacks into your VDO org.
```
vlocity -job project.yaml packDeploy -sfdx.username={VDOAlias}
```

## Run the Tutorial
[![Click to play the video](https://github.com/Soforce/vlocity-ex-tutorials/blob/master/om-use-flow/images/video%20cover.png)](https://www.youtube.com/watch?v=O7AhKvIntew) 

In this sample, you will build an order with two products, one product relies on another by using the Vlocity relies on relatinship. Once the products are decomposed and submitted to OM, the fulfilment task, aka the orchestration item, will copy the relies on item Id from the Order Item into the attribute of the decomposed fulfilment request line record.  
1. Create an Order and add **Ethernet Internet Access** and **User Network Interface** products
2. Set the ReliesOnItemId__c on the **Ethernet Internet Access** to the Id of **User Network Interface** OLI to establish the relies on relationship.
3. Decompose and submit the Order to OM
4. Check the "Relies On" attribute of "EVC CFS" to see if it matches to the "ReliesOnItemId__c" field of the Ethernet Internet Access OLI.


## Explanation of the Tutorial
### Decompostion 
*  `Ethernet Internet Access` is decomposed into `EVC CFS`
*  `User Network Interface` is decomposed into `UNI CFS`
*  `OrderItem.vlocity_cmt_AssetReferenceId__c` field is mapped into `Asset Reference Id` attribute of FRL

### Orchestration Plan
*  `ve-sample: Use Flow in OM` orchestration plan is created with only one `Test OM Flow` orchestration item
*  `Test OM Flow` is an **AutoTask** which executes the Lightning flow with `Execute Autolaunched Flow` item implementation
*  The flow name to be executed is passed in **Auto Task Parameters** parameter.

### "ve-sample: Use Flow in OM" Lightning Flow
#### Input paramters
*  `itemId` - Id of the Orchestration Item record
*  `fulfilmentRequestLineId` - Id of the fulfilment request line record which kicks off the orchestration plan
*  `planId` - Id of the Orchestration Plan record
*  `orderId` - Id of the order 
#### Flow steps
![Image of Flow in OM](https://github.com/Soforce/vlocity-ex-tutorials/blob/master/om-use-flow/images/flow%20diagram.png)

1. `Get AssetReferenceId for the FRL` Apex Action step 
An Apex Action which uses 'Get JSONAttribute' action provided by the **Vlocity Extension** package. It reads the JSON attribute value for the `Asset Reference Id` attribute on the Fulfilment Request Line record.
2. `Find OLI by the AssetReferenceId` Get Records step 
This data action retrieves record by the the asset reference Id returned from step 1.
3. `Populate reliesOnItemAttribute` Assignment step
Populate the name and value for the `Relies On Item` variable
4. `Update Relies On Item Attribute of FRL` Apex Action step
Uses 'Set JSONAttribute' action provided by the **Vlocity Extension** package to update the attribute back into the fulfilment request line record.
