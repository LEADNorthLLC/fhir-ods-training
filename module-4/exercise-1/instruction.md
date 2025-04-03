# Module 4 Exercise 1 - Setting up an HL7 feed in IRIS for Health


**Task:** 

## Instructions:

The first step is connecting to the AWS EC2 instance. Navigate to the following link: http://ec2-18-219-162-44.us-east-2.compute.amazonaws.com/irishealth/csp/sys/UtilHome.csp


You will be assigned a username and password to use in the format of: train# with the same password, train#
i.e. train1/train1


On your assigned EGFHIRTRAINING namespace of your HealthShare instance, navigate to the EdgeGatewayProduction by clicking on Interoperability -> Configure -> Production. 

Create a new Service by clicking on the plus `+` next to the **Services** header. This will open a wizard where you will set the Service class to **EnsLib.HL7.Service.FileService** and the Service name to **EnsLib.HL7.Service.FileService**. Click enable and ok to finish the service. 

Create a new Process by clicking on the plus `+` next to the **Process** header. Here you will set the Service class to **HS.Local.FHIR.HL7toSDAProcess** and the Service name to **FHIR.HL7toSDA**. Click enable and ok to finish the service. 

Create another new Process by clicking on the plus `+` next to the **Process** header. Now set the Service class to **HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process** and the Service name to **HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process**. Click enable and ok to finish the service.

And finally create a new Operation by clicking on the plus `+` next to the **Operations** header. Set the Service class to **HS.FHIRServer.Interop.Operation** and the Service name to **HS.FHIRServer.Interop.Operation**. Click enable and ok to finish the service. 


Once we have all of your components created you need to connect them all together. Each component, besides HS.FHIRServer.Interop.Operation, will need to set it's TargetConfigNames to the next component in the chain.

    EnsLib.HL7.Service.FileService - FHIR.HL7toSDA
    FHIR.HL7toSDA - HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process
    HS.FHIR.DTL.Util.HC.SDA3.FHIR.Process - HS.FHIRServer.Interop.Operation


Set the inbound file to the following, except replacing 00 with the number of your instance:
/tmp/fhir-training00/hl7


This should automatically send a message through your pipeline and we can view it in the message trace.



