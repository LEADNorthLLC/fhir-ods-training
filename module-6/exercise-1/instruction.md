# Module 6 Exercise 1 - FHIR Terminology

**Task:** 

## Instructions:


Task 1

Once putty is set up navigate to FHIR Terminology page. The path to do this is by clicking on Health -> Schema Documentation -> FHIR Annotations. 

Once on this page click on the **View Lookups** button. This will open a window that shows you the existing FHIR Terminology transforms that are currently being applied. 

We will be referring back to this page as we move forward with the exercise.



Task 2

Download healthshare-connect.ppk from the exercise-1 folder. 

Inside of Putty navigate to the following location:
    Connections -> SSH -> Auth -> Credentials

Set the Private Key for Authentication the healthshare-connect.ppk you downloaded.
(../images/mod6-ex1.3.png)


Navigate back to Connections.
Set the following:
    Host Name: ec2-18-218-191-197.us-east-2.compute.amazonaws.com
    Port: 22
    Connection Type: SSH

(../images/mod6-ex1.1.png)

ec2-user

(../images/mod6-ex1.4.png)

Username: _system
Password:SYS

(../images/mod6-ex1.5.png)

iris terminal irishealth

ZN "*YOUR-NAMESPACE*"

 do ##class(HS.FHIR.DTL.Util.API.LookupTable).EditLookupTable()

 R4

 SDA3

 (../images/mod6-ex1.6.png)

 17

 +

 paused

 PA

 (../images/mod6-ex1.7.png)

 After the prompts finish Navigate back to FHIR Annotations. 