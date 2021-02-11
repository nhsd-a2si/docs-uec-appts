---
title: How to store patient contact details
sidebar: overview_sidebar
keywords: specification
permalink: fs_patientcontact.html
toc: false
folder: functional_spec
---

When storing patient contact details against the {%include FHIRSpecificationLink.html page="patient.html" text="Patient Resource" %} there are some specific business rules that need to be followed.

In the Patient profile there are three ways to store contact details. Each one has a specific use. 

* ```Patient.telecom``` 
  - Should be used as the place to store primary contact information that has a direct relationship to the Patient
* ```Patient.contact``` 
  - Should be used to store contact details for third parties whose details can be used to contact the patient (e.g. a Parent)
* ```Patient.link(RelatedPerson)``` 
  - Should be used to store a relationship to another individual who meets **all* of the following requirements: 
    - has a personal or non-healthcare-specific professional relationship to the patient
    - who is **not** associated with the care delivery organization
    - who is allocated tasks specifically for the care of the Patient

Therefore a supplier system **must** also identify the relationship of the contact details to the patient. Then depending on that relationship those contact details **must** be recorded into the correct location according to the rational above.

### Requirements for the Consumer, collecting and recording the contact details:
* At *least* **ONE** set of contact details 


### Requirements for the Provider, consuming the Patient resource and storing the contact details:





Patient.address | 1..*
At least one address should be populated. you MUST also populate the Patient.Address.Use

Patient.telecom | 1..* OR Patient.contact.telecom | 1..*
At least one telecom MUST be populated, either Patient.telecom OR Patient.contact.telecom. You MUST also populate the Patient.telecom.rank OR Patient.contact.telecom.rank and there must be a clear indication or priority by ONLY ONE element with Patient.telecom.rank = 1 OR Patient.contact.rank = 1.
