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

## Install & deploy the "Use Lightning Flow in Vlocity OM" tutorial
1. Download or clone the [vlocity-ex-tutorials](https://github.com/Soforce/vlocity-ex-tutorials) GitHub repository into your computer.
2. Open Windows Command Line or Mac OS Terminal and change into the "om-use-flow" sub-folder.
3. Execute the following SFDX command to deploy the tutorial flow into your VDO org.
```
sfdx force:source:deploy -p force-app -u {VDOAlias}
```
4. Execute the following VBT command to deploy vlocity datapacks into your VDO org.
```
vlocity -job project.yaml packDeploy -u {VDOAlias}
```
5. You also can deploy the [tutorial-init](../tutorial-init/datapacks/tutorial-init.json) datapack to install sample product catalogs to help you run the tutorial. You can reference [Deploy "tutorial-init" datapack](https://github.com/Soforce/vlocity-ex-tutorials/tree/master/tutorial-init#deploy-tutorial-init-datapack) for details.

