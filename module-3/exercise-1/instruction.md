# Module 3 Exercise 1 - Setting up a FHIR inbound endpoint



## Instructions: 

Navigate to your production (HSEDGE, navigate to the EdgeGatewayProduction, click on Interoperability -> Configure -> Production -> Go)

Create a new Service by clicking on the plus `+` next to the **Services** header. This will open a wizard where you will set the Service class to BCBSSC.Inbound.FHIRService and the Service name to BCBSSC.Inbound.FHIRService. Click enable and ok to finish the service. 

Next, we need to create the adaptor class our FHIR endpoint will be using to ingest the data. We will be using the existing FHIR adaptor class as the base for our new adaptor. Locate the HS.FHIRServer.HC.FHIRInteropAdapter class. Copy that class with the new name BCBSSC.FHIR.Inbound.RestHandler. 

Inside of our new class we need to change one thing and that is the ServiceConfigName. This will be set to match your new service you just created, BCBSSC.Inbound.FHIRService.

Now navigate to the Web Applications portal at System Administration > Security > Applications > Web Applications. 

Click the **Create New Web App** button at the top of the screen. Here there are six settings that need to be set correctly before the endpoint is saved.

    1. Name - /api/healthshare-rest/egfhirtraining01/input
    2. Copy from - 
    3. Namespace - EGFHIRTRAINING01
    4. Enable - REST
    5. Dispatch Class - BCBSSC.FHIR.Inbound.RestHandler
    6. Allowed Authentication Methods - Unauthenticated 



### Task 1: