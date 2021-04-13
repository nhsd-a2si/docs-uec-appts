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

Therefore a supplier system **must** also identify the relationship of the contact details to the patient. Then depending on that relationship those contact details **must** be recorded into the correct location according to the rules above.

### Requirements for the Consumer, collecting and recording the contact details:

* At *least* **one** set of contact details **must** be recorded against the patient
  * **if** the contact details are *directly* related/owned by the patient then the details **must** be stored as ```Patient.telecom```
  * **if** the contact details belong to a 3rd party, they **must** be stored in the ```Patient.contact``` section
    * 3rd party contact details **must** include: 
      * a relationship
      * a name      
  * all contact details **must** record a ```rank```:
    * the ```rank``` element is a positive integer value
    * Contacts are ranked with lower values coming before higher values (e.g. 1=highest)
    * rank does not necessarily follow the order in which the contacts are represented in the instance.
    * the ```rank``` value of ```1``` **must** be unique and **not** used more than once in a Patient profile.
    * ```rank``` values **must** use the following precedence:
      * the *primary* contact details (e.g. those that should be tried first) for the patient **must** always have a rank value of 1
      * if precedence for other contact details can be determined then rank values **must** reflect this
      * if no precedence can be determined then they can all be allocated the same value (e.g. ```2```)
  
* At *least* **one** set of address details **must** be recorded against the patient
  * ```Patient.address``` **must** always be populated
  * third-party address details **must** be stored in the ```Patient.contact``` section with other contact details (e.g. ```telecom```)


### Requirements for the Provider, consuming the Patient resource and storing the contact details:

* Contact details are obtained from: 
  * ```Patient.telecom``` & ```Patient.address``` 
  **and / or** 
  *  ```Patient.contact.telecom``` & ```Patient.contact.address```
* when specfic 3rd party contact details are displayed to a user, a name and a relationship **must** be displayed
* at *least* the primary contact for the patient **must** be displayed to a user (indicated by a ```rank``` value of 1)
* additional contacts **should** be displayed to the user if present with the precedence identified to the user (based on ```rank``` values)

## Examples

The following examples show abridged Patient resources with *only* the pertinent contact elements included for illustration only *(click to expand)*:

<details>
  <summary markdown="span">Patient with no 3rd party contact details</summary>
  {% highlight json %}
  {
    "resourceType": "Patient",
    <-snip->
    "telecom": [
        {
            "system": "phone",
            "value": "01234 567 890",
            "use": "home",
            "rank": 1
        }
    ],
    <-snip->  
    "address": [
        {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
        }
    ],
    <-snip->
  }
  {% endhighlight %}
</details>
      
<details>
  <summary markdown="span">Patient with only 3rd party contact details</summary>
  {% highlight json %}
  {
    "resourceType": "Patient",
    <-snip->
      "address": [
        {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR",           
        }
      ],
      <-snip->
      "contact": [
        {
          "relationship": [
            {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/v2/0131",
                  "code": "N"
                }
              ]
            }
          ],
          "name": {
            "family": "Smith",            
            "given": [
              "Jane"
            ]
          },
          "telecom": [
            {
              "system": "phone",
              "value": "01234 567 890",
              "rank": 1
            }
          ],
          "address": {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
            }
          },
          "gender": "female",          
      }
    ],     
    <-snip->
  }
  {% endhighlight %}
</details>

<details>
  <summary markdown="span">Patient with own and 3rd party contact details</summary>
  {% highlight json %}
  {
    "resourceType": "Patient",
    <-snip->
    "telecom": [
        {
            "system": "phone",
            "value": "01234 567 890",
            "use": "home",
            "rank": 1
        }
     ],
     "address": [
        {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
        }
      ],
      <-snip->
      "contact": [
        {
          "relationship": [
            {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/v2/0131",
                  "code": "N"
                }
              ]
            }
          ],
          "name": {
            "family": "Smith",            
            "given": [
              "Jane"
            ]
          },
          "telecom": [
            {
              "system": "phone",
              "value": "01234 056 789",
              "rank": 2
            }
          ],
          "address": {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
            }
          },
          "gender": "female",          
      }
    ],     
    <-snip->
  }
  {% endhighlight %}
</details>

<details>
  <summary markdown="span">Patient with own and two 3rd party contact details</summary>
  {% highlight json %}
  {
    "resourceType": "Patient",
    <-snip->
    "telecom": [
        {
            "system": "phone",
            "value": "01234 567 890",
            "use": "home",
            "rank": 1
        }
     ],
     "address": [
        {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
        }
      ],
      <-snip->
      "contact": [
        {
          "relationship": [
            {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/v2/0131",
                  "code": "N"
                }
              ]
            }
          ],
          "name": {
            "family": "Smith",            
            "given": [
              "Jane"
            ]
          },
          "telecom": [
            {
              "system": "phone",
              "value": "01234 056 789",
              "rank": 2
            }
          ],
          "address": {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
            }
          },
          "gender": "female",          
      },
      {
          "relationship": [
            {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/v2/0131",
                  "code": "N"
                }
              ]
            }
          ],
          "name": {
            "family": "Smith",            
            "given": [
              "John"
            ]
          },
          "telecom": [
            {
              "system": "phone",
              "value": "01234 905 678",
              "rank": 2
            }
          ],
          "address": {
            "use": "home",
            "text": "123 High Street, Leeds LS1 4HR",
            "line": [
                "123 High Street",
                "Leeds"
            ],
            "city": "Leeds",
            "postalCode": "LS1 4HR"
            }
          },
          "gender": "male",          
      }  
    ],     
    <-snip->
  }
  {% endhighlight %}
</details>
