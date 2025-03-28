///Hello Team! Note from Elise (I'll take this out later), all the exercises I am working on can also be found through this google doc link: https://docs.google.com/document/d/14WjDPaDpcYLcZxt6JDxF9cYxhvi-9wVloN-mamQ_XtE/edit?usp=sharing

# Module 1: Exercise 2

# Running a Demo X12 837I into SDA in EDGE Gateway + Walking through the Message Trace

**Objective:** The goal of this exercise is to [GOAL TO BE DETERMINED]

First, on the HSEDGE namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on Interoperability -> Configure -> Production -> Go. 

Now, click on the EnsLib.EDI.X12.Service.FileService; this is where we will send our example X12 file. In the settings tab, under basic settings, find the File Path that is connected to this service [OR WE CAN PROVIDE THEM WITH THE NAME OF THE FILE PATH, EITHER OR]

Navigate to [FILE LOCATION TO BE DETERMINED] and copy the file 837Ix12example01.txt [NAME SUBJECT TO CHANGE]. Paste the copied file into the in-folder connected to the EnsLib.EDI.X12.Service.FileService (the folder we located in the previous step)

Return to the EdgeGatewayProduction, click on the EnsLib.EDI.X12.Service.FileService, and navigate to the messages tab. Click on the header number next to the top message to pull up the message trace. Refer to images/x12messageTrace.png as an example of what it should look like.

In this trace, the X12 file is being sent to the Inbound Process DTL where it is transformed into SDA3. The information is eventually sent over to update the ODS FHIR server (step 5) and in the AddUpdateHubResponse (step 6) you can see the unique patient MPIID that we will use to retrieve the FHIR bundle.