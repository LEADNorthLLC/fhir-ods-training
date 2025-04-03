# Module 4 Exercise 2 - Setting up an X12 feed in IRIS for Health


**Task:** 

## Instructions:

On your assigned EGFHIRTRAINGING namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on Interoperability -> Configure -> Production. 



Create a new Service by clicking on the plus `+` next to the **Services** header. This will open a wizard where you will set the Service class to **EnsLib.EDI.X12.Service.FileService** and the Service name to **EnsLib.EDI.X12.Service.FileService**. Click enable and ok to finish the service. 

Create a new Process by clicking on the plus `+` next to the **Process** header. This will open a wizard where you will set the Service class to **EnsLib.EDI.X12.MsgRouter.RoutingEngine** and the Service name to **FromX12FileService.Router**. Do not check off the Create Routing Rule if it does not exist option. Click enable and ok to finish the service. 


Just like the last exercise, the next step is connecting all of our components. This time we will use both TargetConfigNames and a Routing Rule to accomplish this. 

EnsLib.EDI.X12.Service.FileService will have it's TargetConfigNames set to FromX12FileService.Router

For EnsLib.EDI.X12.MsgRouter.RoutingEngine set the RoutingRule to FromX12FileService.RouterRoutingRule





