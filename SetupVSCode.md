# Setting up VSCode for IRIS Development

You will first need to install the **InterSystems Language Server** and **InterSystems ObjectScript** Extensions from the VSCode Extensions Marketplace.

If you are connecting to an IRIS instance in a container, make sure the container is runnning and the instance has been started. i.e. if you can connect to the Management Portal of the instance, you can connect in VSCode. 

1. Click on the **InterSystems** icon on the left-side panel of the VSCode editor. 

![InterSystems VSCode Extension](../images/module5-vscode-intersystems.png)

2. Expand the **SERVERS** section
* Click on the `+` sign next to **All Servers**
* Name of the new server defition: **fhir-training**
* Optional description: **Docker instance of iris for health**
* Hostname or IP address of web server: **ec2-18-219-162-44.us-east-2.compute.amazonaws.com**
* Port of Webserver: **80**
* Optional path prefix: *Press Enter*
* Username: **_system**
* Connection type: **http**

3. Expand **All Servers**. You should see the **fhir-training** configuration. Expand that server name. You should be prompted at the top of the screen for a password. Enter: **SYS**

4. Once logged in, you will see the available **Namespaces**

![InterSystems VSCode Extension](../images/module5-vscode-fhir-training.png)

* Hover over your assigned **FHIRTRAIN#** Namespace and select the pen icon to `Edit code in workspace`. 
* The workspace is added at the bottom and labeled **fhir-training:FHIRTRAIN#**.

