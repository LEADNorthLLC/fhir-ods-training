# Module 2 Exercise 1 - Navigating to ODS Server and inspecting ODS settings and tables


## Instructions:

### Task 1: 

One: From the management portal, verify that you are in the HSODS namespace

Two: Navigate to Healthshare -> ODS Configuration -> FHIR -> Go

Three: Select Package Configuration. From here you can view and manage all the FHIR packages on this instance. Select the hl7.fhir.us.carin-bb 1.0.0 package. What dependencies does it rely on? 
Deeper Dive : Most FHIR packages are not available by default, and must be imported if you intend for your FHIR endpoint to support an implementation guide. You can easily do this by finding the desired FHIR specifications and downloading their packages. In this case, we downloaded these two guides: https://hl7.org/fhir/us/core/STU3.1.1/downloads.html and https://hl7.org/fhir/us/carin-bb/STU1/downloads.html 

Once the guides are downloaded, return to the HSODS namespace and navigate to HealthShare -> ODS Configuration -> FHIR -> Go. Return to the Package configuration and click Import Package. Select the package directory from your files and import. (make sure to first import any dependencies). Repeat import steps until all desired packages have been imported. Now these packages will be available to use for FHIR endpoints.

Four: From the side menu, select server configuration (its icon looks like a gear). You can now see all the endpoints currently set up. Select the drop down arrow for the /csp/healthshare/hsods/fhir/r4a endpoint. Find the additional packages. You will see that this endpoint is configured to use the hl7.fhir.us.carin-bb 1.0.0 package and its dependencies.Feel free to review any other settings in this endpoint.

Five: Now we are going to view the ODS tables where FHIR is stored. From the management portal, verify that the HSODS namespace is selected. Navigate to System Explorer -> SQL -> Go.
Step 6: In the filter, type *FHIR* and search. Select the tables dropdown. The top table should be HSFHIR_X0001_R.Rsrc. Click and drag that table into the Execute Query text box. Run the query by hitting Execute.



