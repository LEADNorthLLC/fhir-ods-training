# Module 1 Exercise 1 - Viewing the FHIR bundle


**Task:** 

## Instructions:


For this exercise, we will be using a cURL command to be making our request. 

Run the following command in the terminal:

curl -k -u "chi.nguyen-rettig@bcbsc.com" https://awslscomishs001.aws.bcbssc.com/csp/healthshare/hsods/fhir/r4a/Patient/100419325/$everything

Send the request.

Once the request goes through, you should now be able to view the FHIR bundle. Scrolling through the bundle, you should see all resources associated with this Patient [Claim, ClaimResponse, RelatedPerson, Patient, Organization, Provenance, maybe more associated with the HL7 sent for the same patient]


### Task: 
1. Find Medication using the **FHIR4** dropdown.
2. Find Patient using the **Category** dropdown.
3. Find ObservationGroup using the **HS.SDA3** dropdown. Note the differences and similarities in the three drop downs.



4. Find the mapping from the Medication section of SDA3 to FHIR. Use whatever dropdown you deem appropriate.
5. Find the Quantity.system **SDA3 Target** field using whatever dropdown you deem appropriate.
6. Find SearchParameter:multipleAnd **FHIR4 Data Type** using whatever dropdown you deem appropriate.

