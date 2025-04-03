# Module 1 Exercise 2 - Running a Demo HL7 into SDA in Edge Gateway


**Task:** 

## Instructions:


First, on the HSEDGE namespace of your HealthShare instance, navigate to the EdgeGatewayProduction  by clicking on Interoperability -> Configure -> Production -> Go. 

Now, click on the EnsLib.HL7.Service.FileService; this is where we will send our example HL7 file. In the settings tab, under basic settings, find the File Path that is connected to this service.

Navigate to /tmp/hl7/infolder/ and copy the file 0.hl7. Paste the copied file into the in-folder connected to the EnsLib.HL7.Service.FileService. We have provided more messages than just that one that you can run through at the end of the exercise.

Return to the EdgeGatewayProduction, click on the EnsLib.HL7.Service.FileService, and navigate to the messages tab. Click on the header number next to the top message to pull up the message trace. 

In this trace, the HL7 file is being sent to the Inbound Process DTL where it is transformed into SDA3. The information is eventually sent over to update the ODS FHIR server (step 5) and in the AddUpdateHubResponse (step 6) you can see the unique patient MPIID that we will use to retrieve the FHIR bundle.

### Task:

1. Find the following in step 6 of the message trace:

* Patient Last name
* MRN (Medical Record Number)
* Other Identifiers

2. Look at the SDA Streamlet Database via SQL. Go to **Home -> System Explorer -> SQL**. 

* Make sure that **EGFHIRTRAINING01** is the current schema. The streamlet databases are organized within each EDGE Gateway. 

* Type '*Streamlet*' in the Filter box. Then expand the **Tables** section to see all the Streamlet tables. **Find HS.SDA3.Streamlet.Patient**

* Drag the name into the query box or you can also type the following query directly: 

> SELECT * FROM HS_SDA3_STREAMLET.PATIENT

* Click **Execute Query** and view the results. The streamlet data is contained in the **SDAString** field. A quick and dirty way to search for a specific record is by using the contains operator, which is a left square bracket '['. 

> SELECT * FROM HS_SDA3_STREAMLET.PATIENT WHERE SDASTRING [ 'Smith'

You can also search using identifiers like the MRN. 

3. To find all the Streamlets for a Patient, first find the **AggregationKey** value from the Patient streamlet. 

Then use this query against the HS_SDA3_Streamlet.Abstract table to display all the streamlets for the patient: 

> SELECT * from HS_SDA3_Streamlet.Abstract where AggregationKey = 4

    