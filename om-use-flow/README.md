# Use Lightning Flow in Vlocity OM
## Overview
---

## Prerequisite
You need a VDO (Vlocity Demo Org) org to work on this tutorial. You also need to install SFDX and Vlocity Build Tool on your computer.
1. Sign up a VDO (Vlocity Demo Org) org for your exercise if you don't have one. You can open "https://vdo.force.com" to apply a VDO org for yourself. Please select "Commmunications" in the "Industry" field.
2. Install [Salesforce CLI Command](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference.htm). You can follow the [Install the Salesforce CLI](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_install_cli.htm) to complete the installation.
3. Install [Vlocity Build Tool](https://github.com/vlocityinc/vlocity_build#vlocity-build). You can follow the [Installation and Update Instructions](https://github.com/vlocityinc/vlocity_build#installation-and-update-instructions) to complete the installation.

## Install and Configure [Vlocity Extension (Vlocity-ex)](https://github.com/Soforce/vlocity-ex#vlocity-extension-vlocity-ex-package) Package
You need to install and configure the vlocity-ex package into your VDO org to complete this tutorial if you have not. You can follow [Install & Configure Vlocity-ex Package](https://github.com/Soforce/vlocity-ex#install--configure-vlocity-ex-package) to complete the installation and configuration.

## 

In order to complete this tutorial, you need a VDO (Vlocity demo org) org
install & configure [vlocity-ex](https://github.com/Soforce/vlocity-ex) package into the org.

2. Install Vlocity-ex (Vlocity Extension) package. You can reference "[Install Vlocity-ex package](https://github.com/Soforce/vlocity-ex/blob/master/README.md#install-vlocity-ex-package)" page for detail.
3. Configure Vlocity-ex package after the installation. Youm can reference "[Configure Vlocity-ex package](https://github.com/Soforce/vlocity-ex/blob/master/README.md#-configure-vlocity-ex-package)" page for detail.

## Install & deploy "Use Lightning Flow in Vlocity OM"
1. Download or clone the [vlocity-ex-tutorials](https://github.com/Soforce/vlocity-ex-tutorials) GitHub repository into your computer.   

4. Deploy Vlocity-ex sample data to be used by this trailhead.

## Create Lightning Flow
### Add input variables to be used by the flow
1. From Setup, enter Flow in the Quick Find box, then select Flows.
2. Click New Flow, select Screen Flow, and click Create.
3. Click Manager tab in the Toolbox panel, click New Resource to open the New Resource Dialog.
4. For Resource Type, select Variable.
5. For API Name, enter itemId.
6. For Data Type, select Text.
7. Check Available for input checkbox
8. Repeat 3-7 to create three more text variables: planId, orderId, fulfilmentRequestLineId.
9. Click Save to save your flow.
  * For Flow Label, enter ve-sample: Use Flow in OM. 
  * For Flow API Name, use ve_sample_Use_Flow_in_OM.



You should see the following four variables created in your Lightning Flow after you complete the above steps.


## Create Orchestration Plan 

## Test 

## 
