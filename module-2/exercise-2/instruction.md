# Module 2 Exercise 2 - Running an update to the previous patient and then seeing the update in ODS 


**Task:** 

## Instructions:


In this exercise we will be updating the patient that you created in Module 1 Exercise 2. 

First, on the EGFHIRTRAINING01 namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on **Interoperability -> Configure -> Production**. 

Now, click on the EnsLib.HL7.Service.FileService; this is where we will send our example HL7 file. In the settings tab, under basic settings, find the File Path that is connected to this service.

Navigate to /tmp/hl7/infolder/ and copy the file 0.hl7. Paste the copied file into the in-folder connected to the EnsLib.HL7.Service.FileService. We have provided more messages than just that one that you can run through at the end of the exercise.

Return to the EdgeGatewayProduction, click on the EnsLib.HL7.Service.FileService, and navigate to the messages tab. Click on the header number next to the top message to pull up the message trace. 

In this trace, the HL7 file is being sent to the Inbound Process DTL where it is transformed into SDA3. The information is eventually sent over to update the ODS FHIR server (step 5) and in the AddUpdateHubResponse (step 6) you can see the unique patient MPIID that we will use to retrieve the FHIR bundle.

### Task:

Find the following WITHOUT reading the HL7 message:

1. Patient's new last name
2. Patient's new address
3. Patient's new phone number
4. Patient's MPIID

## Instructions:

For this exercise, we will be using a cURL command to request the FHIR bundle. 

1. Using putty, open up a terminal window.

2. Run the following command on the command line, replacing the values in brackets (Hint: you can copy paste):

curl -k -u "<username@bcbssc.com>" https://awslscomishs001.aws.bcbssc.com/csp/healthshare/hsods/fhir/r4a/Patient/<MPIID>/$everything


Example: curl -k -u "<username@bcbssc.com>" https://awslscomishs001.aws.bcbssc.com/csp/healthshare/hsods/fhir/r4a/Patient/100419325/$everything

Send the request.

Once the request goes through, you should now be able to view the FHIR bundle. Scrolling through the bundle, you should see all resources associated with this Patient [Claim, ClaimResponse, RelatedPerson, Patient, Organization, Provenance, along with clinical data resources from the HL7 sent for the same patient]




### Task 2: Reviewing Postman OperationalOutcomes, and walking through what caused them. 

Step 1: In the FHIR bundle, you will notice that one resource is an OperationalOutcome that indicates there is a resource that failed to load because it is missing data and did not pass validation. What resource failed to load in this way?

Step 2: Back in the Management Portal of the HSODS namespace, navigate to Interoperability -> View -> Event Log . Scrolling through the logs, you should see some Warnings. Read through the warnings until you find one warning about missing required properties for the Claim resource. What required properties are missing from the Claim and the ClaimResponse? 

Step 3: Open the management portal in a new tab, leaving the warnings in their own tab. In the HSODS namespace, navigate to HealthShare -> Schema Documentation -> FHIR Annotations . You will see three drop-down menus at the top of the screen; using the HS.SDA3 drop down, find and select MedicalClaim. This will display a table showing where information is pulled from SDA3 to populate FHIR properties. Looking at the FHIR4 Target column, scroll through and find the entries for the missing properties in the warning we previously looked at. What fields in the SDA3 did the missing properties map from? We can use these SDA fields to back track in the data transformations and find which X12 fields were used to populate these SDA3 ones. 

Bonus step: If you want to look at the DTLs for yourself, you would go to **Interoperability -> Build -> Data Transformations**. 

Once in the editor, click **Open** and pull up the **HS.Gateway.X12.SDA3.From837Iv5010.MedicalClaim** transformation. This is the one that our production used to transform the X12 file. Scrolling through it, you will see that some fields required in FHIR weren’t required in the SDA3, which led to the Operational Outcome for Claim. We have already created another DTL that maps our X12 document to SDA3 while including the remaining fields that are needed in FHIR. Let’s go ahead and test out another file configured to use our edited DTL. 

