# Module 2 Exercise 2 - Running an update to the previous patient and then seeing the update in ODS 


**Task:** 

## Instructions:


In this exercise we will be updating the patient that you created in Module 1 Exercise 1. 

First, on the HSEDGE namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on Interoperability -> Configure -> Production -> Go. 

Now, click on the EnsLib.HL7.Service.FileService; this is where we will send our example HL7 file. In the settings tab, under basic settings, find the File Path that is connected to this service.

Navigate to /tmp/x12/infolder/ and copy the file 0.hl7. Paste the copied file into the in-folder connected to the EnsLib.HL7.Service.FileService. We have provided more messages than just that one that you can run through at the end of the exercise.

Return to the EdgeGatewayProduction, click on the EnsLib.HL7.Service.FileService, and navigate to the messages tab. Click on the header number next to the top message to pull up the message trace. 

In this trace, the HL7 file is being sent to the Inbound Process DTL where it is transformed into SDA3. The information is eventually sent over to update the ODS FHIR server (step 5) and in the AddUpdateHubResponse (step 6) you can see the unique patient MPIID that we will use to retrieve the FHIR bundle.

### Task:

Find the following WITHOUT reading the HL7 message:

1. Patient's new last name
2. Patient's new address
3. Patient's new phone number