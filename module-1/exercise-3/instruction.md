///Hello Team! Note from Elise (I'll take this out later), all the exercises I am working on can also be found through this google doc link: https://docs.google.com/document/d/14WjDPaDpcYLcZxt6JDxF9cYxhvi-9wVloN-mamQ_XtE/edit?usp=sharing

# Module 1: Exercise 3

# Viewing the FHIR bundle through Postman

***To start this exercise you must first complete Module 1 Exercise 1 and 2.***

**Objective:** The goal of this exercise is to learn how to query for a patient through the API

First, open up Postman. If you already have an acoount, go ahead and sign in, if not, start by signing up. 

Now, click the New Request button. This will open up a workspace where we can test the FHIR APIs.

Verify that the request is set to GET.

In the URL text box, enter this URL: http://localhost:52773/csp/healthshare/hsods/fhir/r4a/Patient/000/$everything Replace 000 with the MPIID returned in the visual trace from exercise 2. 
**[QUESTIONS: WILL THE MPIID RETURNED FROM EXERCISE 1 (HL7) AND EXERCISE 2 (X12) BE THE SAME? THEY SHOULD BE AS LONG AS NATHAN AND I MAKE SURE THAT THE EXAMPLE FILES ARE THE SAME PATIENT. ALSO THE URL WILL PROBABLY BE SOMETHING ELSE, BUT FOR NOW THIS IS WHAT I HAVE LOCALLY]**

Navigate to the Authorization tab and change the Auth type to Basic Auth. Enter in the username and password connected to the HealthShare instance. **[IS AUTH SOMETHING WE SHOULD STILL TURN OFF? I AM LEAVING IT IN FOR NOW]**

Send the request.

Once the request goes through, you should now be able to view the FHIR bundle. Scrolling through the bundle, you should see all resources associated with this Patient [Claim, ClaimResponse, RelatedPerson, Patient, Organization, Provenance, maybe more associated with the HL7 sent for the same patient]

**I HAVE NOT CHANGED TASKS YET, BUT I WANT THIS TO BE TASKS LIKE FINDING VALUES THAT WERE RETURNED IN THE FHIR BUNDLE, BOTH FROM THE HL7 AND X12 THAT UPDATED THE PATIENT. QUESTIONS LIKE: REFEREING BACK TO EXERCISES 1 AND 2, WHICH FILE LOADED THE CLAIM FOR THIS PATIENT? THOUGHTS?**

**Tasks:**
1. Find Medication using the **FHIR4** dropdown.
2. Find Patient using the **Category** dropdown.
3. Find ObservationGroup using the **HS.SDA3** dropdown. Note the differences and similarities in the three drop downs.



4. Find the mapping from the Medication section of SDA3 to FHIR. Use whatever dropdown you deem appropriate.
5. Find the Quantity.system **SDA3 Target** field using whatever dropdown you deem appropriate.
6. Find SearchParameter:multipleAnd **FHIR4 Data Type** using whatever dropdown you deem appropriate.

