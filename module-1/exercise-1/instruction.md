# Module 1 Exercise 1 - Running a Demo HL7 into SDA in Edge Gateway

**Learning Objectives:** 
* 

**Task:** 

## Instructions:

### Task 1: 

First, on the HSEDGE namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on Interoperability -> Configure -> Production -> Go. 

Now, click on the EnsLib.EDI.HL7.Service.FileService; this is where we will send our example HL7 file. In the settings tab, under basic settings, find the File Path that is connected to this service [OR WE CAN PROVIDE THEM WITH THE NAME OF THE FILE PATH, EITHER OR]

Navigate to [FILE LOCATION TO BE DETERMINED] and copy the file 837IHL7example01.txt [NAME SUBJECT TO CHANGE]. Paste the copied file into the in-folder connected to the EnsLib.EDI.HL7.Service.FileService (the folder we located in the previous step)

Return to the EdgeGatewayProduction, click on the EnsLib.EDI.HL7.Service.FileService, and navigate to the messages tab. Click on the header number next to the top message to pull up the message trace. Refer to images/HL7messageTrace.png as an example of what it should look like.

In this trace, the HL7 file is being sent to the Inbound Process DTL where it is transformed into SDA3. The information is eventually sent over to update the ODS FHIR server (step 5) and in the AddUpdateHubResponse (step 6) you can see the unique patient MPIID that we will use to retrieve the FHIR bundle.