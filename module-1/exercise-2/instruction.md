# Module 1 Exercise 1 -  Running a Demo X12 837I into SDA in EDGE Gateway + Walking through the Message Trace

**Learning Objectives:** 
The goal of this exercise is to [GOAL TO BE DETERMINED]
* 

**Task:** 

## Instructions:

### Task 1: 

First, on the HSEDGE namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on Interoperability -> Configure -> Production -> Go. 

Now, click on the EnsLib.EDI.X12.Service.FileService; this is where we will send our example X12 file. In the settings tab, under basic settings, find the File Path that is connected to this service [OR WE CAN PROVIDE THEM WITH THE NAME OF THE FILE PATH, EITHER OR]

Navigate to [FILE LOCATION TO BE DETERMINED] and copy the file 837Ix12example01.txt [NAME SUBJECT TO CHANGE]. Paste the copied file into the in-folder connected to the EnsLib.EDI.X12.Service.FileService (the folder we located in the previous step)

Return to the EdgeGatewayProduction, click on the EnsLib.EDI.X12.Service.FileService, and navigate to the messages tab. Click on the header number next to the top message to pull up the message trace. Refer to images/x12messageTrace.png as an example of what it should look like.

In this trace, the X12 file is being sent to the Inbound Process DTL where it is transformed into SDA3. The information is eventually sent over to update the ODS FHIR server (step 5) and in the AddUpdateHubResponse (step 6) you can see the unique patient MPIID that we will use to retrieve the FHIR bundle.



***START OF TANGENT/ TRAINING SIDE QUEST*** 

BONUS Exercise: Context- This will be the ERROR example where they get to Postman and see all of the operational outcomes, and showing how to back-track and fix. Not sure where this one fits in (if we want it can be their first file run-through and view, or we can show them the happy-case before giving them the example that fails in Postman. In my brain, the bad example comes first just because the out-of-the-box code isn’t set up to have all the mappings for the Carin BB standards, so therefore everything you can start out with leads to this, and then after refining you can achieve a happy FHIR).
Reviewing Postman OperationalOutcomes, and walking through what caused them. 

Step 0: (This builds off of all the steps taken with Exercises 1 + 2. Only variation is the name/content of the file sent through. It would have to be a file that would lead to operational outcomes) 

Step 1: In the FHIR bundle, you will notice that one resource is an OperationalOutcome that indicates there is a resource that failed to load because it is missing data and did not pass validation. What resource failed to load in this way? [Claim]

 Step 2: Back in the Management Portal of the HSODS namespace, navigate to Interoperability -> View -> Event Log -> Go. Scrolling through the logs, you should see some Warnings. Read through the warnings until you find one warning about missing required properties for the Claim resource. What required properties are missing from the Claim and the ClaimResponse? 

Step 3: Open the management portal in a new tab, leaving the warnings in their own tab. In the HSODS namespace, navigate to HealthShare -> Schema Documentation -> FHIR Annotations -> Go. You will see three drop-down menus at the top of the screen; using the HS.SDA3 drop down, find and select MedicalClaim. This will display a table showing where information is pulled from SDA3 to populate FHIR properties. Looking at the FHIR4 Target column, scroll through and find the entries for the missing properties in the warning we previously looked at. What fields in the SDA3 did the missing properties map from? We can use these SDA fields to back track in the data transformations and find which X12 fields were used to populate these SDA3 ones. 

Bonus step: If you want to look at the DTLs for yourself, you would go to Interoperability -> Build -> Data Transformations -> Go. Once in the editor, click Open and pull up the HS.Gateway.X12.SDA3.From837Iv5010.MedicalClaim transformation. This is the one that our production used to transform the X12 file. Scrolling through it, you will see that some fields required in FHIR weren’t required in the SDA3, which led to the Operational Outcome for Claim. We have already created another DTL that maps our X12 document to SDA3 while including the remaining fields that are needed in FHIR. Let’s go ahead and test out another file configured to use our edited DTL….. (This will be exercise 1 and 2 again except using a different test file that has been pre set-up to utilize the customized transforms; if all goes well, this one will be the happy case and give them usable FHIR)

***END OF TANGENT/ TRAINING SIDE QUEST ***
