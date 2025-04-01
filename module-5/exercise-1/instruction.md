# Module 5 Exercise 1 - Pre-FHIR Transform Mapping

**Learning Objectives:** 
* Reference FHIR R4 Implementation Guide and ISC FHIR Annotations to determine required mapping logic
* Modify an inbound X12 to SDA transformation
* Create a reference between a MedicalClaim (SDA) and a MemberEnrollment (SDA)

**Task:** 

## Instructions:
In the previous module, you loaded Patient, Member Enrollment, Condition, and Claim/ExplanationOfBenefit resources. 

In this exercise, you will be modifying the X12 to SDA Transformation on the Claim/EOB in order to add insurance information. In order to figure out what is required for the FHIR standard and how to accomplish it with the SDA streamlets, you will need to refer to the CarinBB IG as well as the FHIR Annotations in IRIS.  

### Task 1: Mapping Requirement - Documentation Review
1. Look up the requirements for Claim resources in FHIR. FHIR IGs are stacked, with the lowest, most detailed level taking precedence. Search for the Claim profile in this order:
Carin for BB: 
USCDI v1:
FHIR R4: 

Where did you first find a Claim resource profile? This will be your reference. 

2. What is the data type for the Claim.insurance element? What other resource type is it pointing to? 

3. Now you need to find how to map to the Claim.insurance element from IRIS/HealthShare. Go to the FHIR Annotations. 
In I4H: Health -> <Namespace> -> Interoperability -> Interoperate -> FHIR Annotations
In HealthShare/UCR: HealthShare -> <Edge Namespace>

In the R4 pulldown, select the **Claim** resource. You can see that it maps to the **Medical Claim** Streamlet. On the HS.SDA3 pulldown, select **MedicalClaim**. What element name maps to the FHIR Claim.insurance?

4. Using the FHIR Annotations, search out what SDA Streamlet maps to the **Coverage** resource. 

5. In order to map the reference correctly, you will need to put the correct Member Enrollment identifier in the <element name> location. 

### Task 2: Modifying an Inbound Transformation

1. Open the <DTL name>. Locate the MedicalClaim.<elementName> on the target side. 
2. Add a **SET** statement to set the value of the element to the MemberEnrollment identifier. 
3. Save, compile, and re-run the message. 
4. Review the FHIR output in the message trace for the Claim. 
5. Search the FHIR server to see the output of the FHIR bundle. 

### Check-In:### 
In this example, we shortcutted the process by hardcoding a matching value to the MemberEnrollment. In real life, you may need to do a lookup or apply organiztional business logic in order to determine the correct MemberEnrollment/Coverage entry. What logic would be used to determine Coverage at your organization?    