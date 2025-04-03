# Module 4 Exercise 1 - Setting up an HL7 feed in IRIS for Health


**Task:** 

## Instructions:

The first step is connecting to the AWS EC2 instance. Navigate to the following link: http://ec2-18-218-191-197.us-east-2.compute.amazonaws.com/irishealth/csp/sys/UtilHome.csp

Once there you can log in with the following username: _system, and the password: SYS.


On your assigned EGFHIRTRAINGING namespace of your HealthShare instance, navigate to the EdgeGatewayProduction by clicking on Interoperability -> Configure -> Production. 

Create a new Service by clicking on the plus `+` next to the **Services** header. This will open a wizard where you will set the Service class to **EnsLib.HL7.Service.FileService** and the Service name to **EnsLib.HL7.Service.FileService**. Click enable and ok to finish the service. 

Create a new Process by clicking on the plus `+` next to the **Process** header. Here you will set the Service class to **HS.Local.FHIR.HL7toSDAProcess** and the Service name to **FHIR.HL7toSDA**. Click enable and ok to finish the service. 

Create another new Process by clicking on the plus `+` next to the **Process** header. Now set the Service class to **HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process** and the Service name to **HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process**. Click enable and ok to finish the service.

And finally create a new Operation by clicking on the plus `+` next to the **Operations** header. Set the Service class to **HS.FHIRServer.Interop.Operation** and the Service name to **HS.FHIRServer.Interop.Operation**. Click enable and ok to finish the service. 


Once we have all of your components created you need to connect them all together. Each component, besides HS.FHIRServer.Interop.Operation, will need to set it's TargetConfigNames to the next component in the chain.

    EnsLib.HL7.Service.FileService - FHIR.HL7toSDA
    FHIR.HL7toSDA - HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process
    HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process - HS.FHIRServer.Interop.Operation


Once your pipeline is configured we will be ready to send a message through.

