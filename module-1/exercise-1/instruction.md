# Module 1: Exercise 1


# Learning about SDA

**Objective:** The goal of this exercise is to learn about the InterSystems SDA model.

First, navigate to the XML Schemas screen of your HealthShare instance by clicking on **Interoperability -> Interoperate -> XML -> XML Schema Structures.** 

If you do not see the schema, you can import it. Click on the **Import** button and select the **HS.SDA3.xsd** file located under the **sample-files** folder. If you don't see the file, ensure that your "File of Type" dropdown is set to see XSD files. Complete the import.

Now you should see all of the sections/structures contained within the SDA XML format. Any documentation you may run across that relates to "Viewer cache or VIEWERLIB" can generally be ignored as this relates to Clinical Viewer in a HealthShare UCR environment only.

**Tasks:**
1. Search for and open the link for Container. Describe the Container definition. What do you think is the purpose of the Container?


2. Click on the **Patient** definition. Find the **PatientNumbers** field. Why is PatientNumbers of type **PatientNumber()** instead of string? What are components of a **PatientNumber** in HealthShare?    

3. Go back to **Container**. Click on the **Procedures()** on Row 15.  Review the details for ProcedureTime and indicate below what HL7 field this data comes from.


4. Scroll to the **EncounterNumber** field on Row 4.  What happens when the HL7 field, PV1-19.1 is null?

   
5. Find the **HS.SDA3.MedicalClaim**. Where should diagnosis information from a claim be stored? 

   
7. Go another level up to the main SDA schema page and dig into three more SDA structures. Scan the documentation to get a feel for some of the constraints, data types and other details that involve mapping data into SDA3.

8. SDAs are automatically matched and deduplicated whenever they are updated. Each streamlet has different matching conditions. To view the Streamlet Matching Documentation, go back to the Management Portal. With EGFHIRTRAINING01 selected, go to **HEALTHSHARE -> Streamlet Matching Documentation**. 

a. What is are the matching requirements for Medications? 

b. What is the matching requirement for MedicalClaims? 