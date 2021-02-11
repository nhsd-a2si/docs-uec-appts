---
title: How to store patient contact details
sidebar: overview_sidebar
keywords: specification
permalink: fs_patientcontact.html
toc: false
folder: functional_spec
---




When storing patient contact details against the {%include FHIRSpecificationLink.html page="patient.html" text="Patient Resource" %} there are some specific business rules that need to be followed.

In the Patient profile there are two ways to store contact details. Each one has a specific use. 

* ```Patient.telecom``` 
  - Should be used as the place to store primary contact information that has a direct relationship to the Patient
* ```Patient.contact``` 
  - Should be used to store contact details for third parties whose details can be used to contact the patient (e.g. a Parent)

Additionally there is a third way related contact details collected *might* be stored, however this has a very specific use and should **not** be used as a way to store third party contact details:

* ```Patient.link(RelatedPerson)``` 
  - Should be used to store a relationship to another individual (with their own separate set of contact details) who meets **all** of the following requirements: 
    - has a personal or non-healthcare-specific professional relationship to the patient
    - who is *not* associated with the care delivery organization
    - who is allocated tasks specifically for the care of the Patient

{%include note.html content="It is often the case that a third party individual (such as a parent of a child) might meet the requirements of both third party contact and also being a relevent ```RelatedPerson``` to the patient. In this case the contact details would be stored in both a separate RelatedPerson profile *and* against the patient in ```Patient.contact``` as third party contact details for the patient." %}

Therefore a supplier system **must** also identify the relationship of the contact details to the patient. Then depending on that relationship those contact details **must** be recorded into the correct location according to the rational above.

### Requirements for the Consumer, collecting and recording the contact details:

* At *least* **ONE** set of contact details **must** be recorded against the patient
  * **if** the contact details are *directly* related/owned by the patient then the details **must** be stored as ```Patient.telecom```
  * **if** the contact details belong to a 3rd party, they **must** be stored in the ```Patient.contact``` section
    * 3rd party contact details **must** include: 
      * a relationship
      * a name
  * all contact details **must** record a rank
  * Each rank value **must** be unique and **not** used more than once in a Patient profile.
  * Rank values **must** use the following precedence:
  
* At *least* **ONE** set of address details **must** be recorded against the patient
  * ```Patient.address``` **must** always be populated


### Requirements for the Provider, consuming the Patient resource and storing the contact details:

* When specfic 3rd party contact details are displayed to a user a name and a relationship **must** be displayed



Patient.address | 1..*
At least one address should be populated. you MUST also populate the Patient.Address.Use

Patient.telecom | 1..* OR Patient.contact.telecom | 1..*
At least one telecom MUST be populated, either Patient.telecom OR Patient.contact.telecom. You MUST also populate the Patient.telecom.rank OR Patient.contact.telecom.rank and there must be a clear indication or priority by ONLY ONE element with Patient.telecom.rank = 1 OR Patient.contact.rank = 1.
