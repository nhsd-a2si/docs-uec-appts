---
title: GP Connect - Workflow Example
sidebar: dos_sidebar
keywords: specification
permalink: gpc_wfexample.html
toc: false
folder: functional_spec
---


{% include note-notpublished.html %}


## Overview

This guidance is to detail how the DoS is used in combination with a 111 IT system and service provider systems to join up finding a service for a patient and booking an appointment directly for them into the service provider system.

**The scenario is as follows:**

* DOS Leads will set-up services in the DoS that match specific patient needs returned from an NHS Pathways assessment - **DOS Service Configuration**
* Administrators of the local Service Provider IT Systems will configure the schedules / rotas to open up appointments to the GP Connect or Care Connect APIs - **Service Provider IT System Configuration**
* A patient calls 111 on their phone and gets through to a 111 service health advisor
* The health advisor takes them through an NHS Pathways assessment using their 111 IT System and determines what the patient need is, for example an urgent appointment with a GP
* The 111 IT System searches the DoS with the details of the patient and the assessment outcome - **DoS Service Search**
* The DoS returns a ranked list of services that includes the metadata about those services, information on the referral and booking endpoints is also returned including the type of end point for appointment booking - **DoS Service Search Results**
* The 111 IT System displays the returned services to the user, who selects one (*note: the logic for display and user interaction is not discussed here*)
* The consuming system will check the endpoint metadata for appointments information:
  * If an endpoint exists in the metadata for appointments, the 111 IT System will display to the user that appointments are bookable at this service, and so the user can choose to book the patient in
  * If an endpoint **does not** exist then the 111 IT system will compare the chosen DoS service's ODS code to the ODS code obtained from the PDS trace for the patient. This will determine if the returned service is their regostered practice. 
    * If there is a match, then this ODS code can be used to query SDS.
    * If there is no match then booking is not possible
* The 111 IT System will use the endpoint information to retrieve the booking API endpoint from SDS - **SDS Endpoint Search**
* A request will be made for appointment slots from the 111 IT System to the chosen Service Provider IT system, using the retrieved API endpoint to retrieve all available and appropriate slots from the appointment schedules at the chosen service - **GP Connect or CareConnect Appointment Slot Search**
* The Service Provider IT system will return available slots and the user will choose one and then follow the process to book in (*note: this is not in these notes as that is detailed in the appropriate API specification*)
* For GP Connect booking if the patient is not registered (or has an inactive registration) the <a href="https://nhsconnect.github.io/gpconnect/foundations_use_case_register_a_patient.html" target="_blank">Register a Patient</a> capability MUST be used

This guidance shows how areas highlighted in bold above are used in combination to return the appointment capability for services.

The methods used for GP Connect appointment booking are different from CareConnect in terms of the SDS Endpoint Search and the appointment FHIR APIs. The guidance will discuss those differences in the context of why this means DOS services for each type will be configured differently.  Also the behaviour of GP Connect provider systems slot return will need some consideration for the consuming 111 IT System functionality.

## Example services used in the guidance below

This guidance uses example services to illustrate how they are configured in DoS and in local provider systems in order to show the flow of 111 search for services in DoS and the use of the two different appointment standards. 

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile modified=\&quot;2019-06-24T14:32:23.168Z\&quot; host=\&quot;www.draw.io\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; etag=\&quot;8Yz4cEW_hKZ-tFZbJc2u\&quot; version=\&quot;10.8.0\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;pCvT3Y6hV7biSGgpgEUX\&quot; name=\&quot;Page-1\&quot;&gt;7VxRl5o4FP41PtYDJCA8qjO2u9tuPceebfepJ0JG6SBxMc5of/0GSICQqDjrIOvUF81NCOF+93733pCZHhivdu8TtF5+IgGOepYR7HrgrmdZJhw47CuV7LnENmAuWSRhwGWlYBb+xFxocOk2DPBGGkgJiWi4loU+iWPsU0mGkoQ8y8MeSCTfdY0WWBHMfBSp0q9hQJe5FADDKDs+4HCx5LdmXV7es0JiNB+6WaKAPFdE4L4HxgkhNP+12o1xlKpPKCa/bnKgt1hZgmPa5IK5NX/6loDAni2Gj/FuEH0PrHd8licUbfkTTxEN0xnzNdO90ARb/jr9udotUqz7m3ARb/pLjCK69Nki+mRLv6/5xWC0pKuIjTbZz4cwisYkIkk2EVNd+mHyDU3IIxY9MYnZ9KMnnNCQ6f8jmuNoSjYhDUnMuueEUrKqDBhGbAGsg5I1kyLe8tndcZLelMSUm5Pp8vYErcIotcQxWYU+e7wZijfs69OMDVDVKXTDboh3FRFX73tMVpgmezaksHcOtbB2YSXPpenY3COWFaPxuMkgbqyLYuYSTvaDI3oGupaCrgIrjoNh6iclAhXk/ExP4K5ESzgB08KIXToJ0wVl/Uxtyf5btfF32ujbonm3q3be7UVrF9Lssr4LAG/nVzoOb5ZXpo3qhVOchExVKeKZ7CCIG7JNfHzaEShKFpgeGQfycTiQeEM1iSrkhgq5kCU4Yi7zJLONzg74HaYkTH1TWFxBLsLiHEOeIn9uflWVHGoTwfpEbm2iXDHKRJlZFo/9cksFiqWappl6KE6eQgZc3WyflyHFszXKMH1mhCQbLtqs82jwEO5wcCU6gBDIOrVshQ5cjW3UVX8xOoCKku/I7CDR+/sojIOMTE9oe062bGDwcV4IkP+4SFLp5y1ls2ARCc5FIUqjwKiYrRJFHrLPZYAaQFgDylGAMs02kXLOIu55RPxHGRIdW7+Mn39sV+sZvy2PENWwUA8CIoczzQq3mxKv20dp/eUUDhpSOOwUhduuzLxF6nsuhZtebaKWKdxTbHaCGX2gLIGzDIFihWiew1WEMotSiEFOGTHwXU3KyHpGhmdnPekMOnqo2mqS8xQ3yAsQhy1rHDpqvgd1DA/rGL+EONbBhy9PA/jz3fDPufvz6+b3Mf6rUcbH7F44NEnokixIjKL7UlrRk1HTYDn+I0nz7kyRPzCle44e2lIiM5Gq5mPWczpPM1Qv12rCbOjljd33PxG6WHYFmPfTHhgy0VBBSLbTE8G3Cs8JNzKMyUTvRq41B1m6fR5azT1F2OFedpxqgDUs1VGKCurijqIWvqMExf6SY6Ky1e2DwtZybVTsG6Iv7QNqchTtuKY5ysXZS7uawS9Y8nFOp2BRi2YRU0at0VeAsPvg6+jL8V0811doF6KvgS3xlyb7apm+1LKtGlRGqtfcICrAMbsWVdR9DwmW9mL9FWExvc4Fe1eBRSoYVW9pXjA+uD72tYqeuza06wHo4oWhY8o7Sh2oDNXyvHsx/JiZnIzhzSvDq5WGR9d91dLwRcx01KubBwy7a2HcVIvDN42IBa8PiRrD2891AZhMsneU7UNiGl7XnESt1d8WIl7NSa6fUJlqQXhrMR42jfF2t2K8Whm+KWcRL1Q75CvWL1+pGWdXfEWtC3uWE1Fu4L30sJ+wXOefbXp8bsTf+DlOVeQs0u8P23lmh3wKtqR8lry3NeebTFzdqbfjznf+C8m6o3nXdzRd4fm/h9NxDGM8fm04LWh1DU5LrVZvAM40MHrea8Pp1pL4DsAJdWRbU3p69mrd/PGLw9hoLmYwjqrF80AfepWPpCTTUE/NeWbfqHxEvV5V2UXOZuk9QC1FhfluS8OVXKJUprD/tOPdJjPINAlkt9qpzvEH3h90jEK8PegsDJbaSWztieuqK3CRcpq6fuh6FQZBlgDpXPBwUqQ7/ycSLM159uMW25xF7b4tWQtUDApqtmKt1zIg0OAt9wGfO08jZ3ui2TeB4zouGAws0zEdA+CiqCx2sjXeqCoPvpr3qXtzrUWJw0c1zi2gChM4bcQnrPT1FK1uJtx/+k09LnybLHMGQCL1ll97mmpob5dkGhwhzklGi40Ww/b4iCvRG1yXbECDgy/t7/8Xf0DV1JadA3h0h2yAmoZ+mU6ZYKa+nL9RwmkOUkcJp8EL5pazGqEZeLKCEIVZK8YOdSV0l/ctjuPdXVaBaq44DBB7cvRWSOXsY0K2J/uFK7/kujbJiP2wDpFM89KpOIJ1rXQGNng/2Kn97+M20GHiUbeIhv6W4l52gGR0/0bo5wykupnTwO7t1Bw5ktMulzSoLzu1W38c4A5ziVqDfqZL5upvhEO6uxHDmuV/b8n/irb8Lzjg/l8=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

* **Federation 1** - GP Practice A is in a federation with GP Practice B
  * **GP Practice A**:
    * Has GP Connect enabled.
    * It has two locations - GP-A (main location) and GP-A1 (branch location).
    * GP Practice A is only open to its own registered patients.  
  * **GP Practice B**
    * Has GP Connect enabled.
    * Has three locations - GP-B (main location) and GP-B1 (branch) and GP-B2 (branch)
    * Offers appointments to its own registered patients at any time. 
    * In addition GP-B provides an extended hours service from 6pm-8pm Monday-Friday to patients from GP Practice A and GP Practice B. 
* **Federation 2** - GP Practice M is in a federation with GP Practice N
* In addition, all these GP Practices are in one CCG - called CCG1
  * And this CCG has commissioned an extended hours service from Hub X for all their registered patients open on Saturday mornings 9-12am. 
  * Hub X also operates a wider OOHs service for the CCG that supports telephone appointments and home visits. 
  * This service uses an IT system that is CareConnect enabled. 
* A UTC service called **Hub Y** using a system that has CareConnect messaging enabled which is open to any patients
* An ED service called **Hub Z** using a system that has CareConnect messaging enabled which is open to any patients
* A UTC and OOH service called **Hub G** using a system that has GP Connect messaging:
  * And extended hours clinic open to Fed 2 patients only
  * A UTC open to all

Services on the DoS are profiled with a range of metadata that is used to determine the ranking for services. 

Examples of these data items are as follows  - full list of items are included here:

* Geographical information such as address and search etc - used in a DoS search to find services within a specified geographical radius
* Demographic profile of patients the service is available for - used in DoS search to ensure for example paediatric only services are not returned for adults
* The commissioning footprint of the service - used in DoS in combination with the patient's registered GP details
  * GP Practices that patients have to be registered to in order to use the service
* The clinical needs that the service will meet, for example:
  * symptoms
  * timeframes
* Opening hours

## DOS Services - how are they configured?

The DoS has a system limitation preventing duplicate ODS codes in the DoS entries.  This means that DoS Leads follow a procedure for adding the correct ODS code for a main GP Practice and use "dummy" ODS codes for services that may be in the DoS separately from the core practice, even though they are run and managed by that practice. For example, a main GP Practice will be included in the DOS with it's correctly assigned ODS code but may include another entry for a specific extended hours clinic available to a wider set of patients with a dummy ODS code.

**Endpoints hold these details:**

| Field Name       | Type   | Description                                                                  |
|------------------|--------|------------------------------------------------------------------------------|
| address          | string | endpoint address                                                             |
| businessScenario | string | Primary or Copy                                                              |
| comment          | string | notes about the endpoint                                                     |
| compression      | string | Y or N                                                                       |
| format           | string | CDA, HTML, PDF etc.                                                          |
| interaction      | string |                                                                              |
| order            | int    | the order in which the endpoint should be used, if more than one is provided |
| transport        | string | type of address - ITK, email, phone                                          |

For settings for the appointment endpoints:

| Field                  | Description / example                              |
|------------------------|----------------------------------------------------|
| order                  | n/a - there should be only one scheduling endpoint |
| transport              | HTTP                                               |
| format                 | FHIR                                               |
| interaction            | scheduling                                         |
| businessScenario       | Primary                                            |
| Address (GP Connect)   | ODS:[Correct ODS code for the service]             |
| Address (Care Connect) | ASID:[Spine ASID for the service]                  |

Using the above the example, services could be configured in DOS as follows:

| Example service | Service Name                      | ODS Code  | DoS Service ID | Dispositions                    | Opening hours                        | Location | ODS commissioned | Appointment Endpoint address |
|-----------------|-----------------------------------|-----------|----------------|---------------------------------|--------------------------------------|----------|------------------|------------------------------|
| 1               | GP Practice A - Main surgery      | G12345    | 765765765      | Dx code - GP consultations      | 08.30-18:00 Mon-Fri                  | GP-A     | G12345           | ODS:G12345                   |
| 2               | GP Practice A - Branch A1         | 845673474 | 845673474      | Dx code - GP consultations      | 08.30-18:00 Mon-Fri                  | GP-A1    | G12345           | ODS:G12345                   |
| 3               | GP Practice B - Main surgery      | G67576    | 647294726      | Dx code - GP consultations      | 08.30-18:00 Mon-Fri                  | GP-B     | G67576           | ODS:G67576                   |
| 4               | GP Practice B - Branch B1         | 729473627 | 729473627      | Dx code - GP consultations      | 08.30-18:00 Mon-Fri                  | GP-B1    | G67576           | ODS:G67576                   |
| 5               | GP Practice B - Branch B2         | 263849372 | 263849372      | Dx code - GP consultations      | 08.30-18:00 Mon-Fri                  | GP-B2    | G67576           | ODS:G67576                   |
| 6               | GP Practice B - GP Extended hours | 462749382 | 462749382      | Dx code - GP consultations      | 18:00-20:00 Mon-Fri                  | GP-B     | G12345, G67576   | ODS:G67576                   |
| 7               | Hub X - OOH face to face          | G39482    | 574858274      | Dx code - GP consultations      | 20:00-08:30 Mon-Fri, All day Sat-Sun | Hub X    | CCG1, CCG2, CCG3 | ASID:457384758671            |
| 8               | Hub X - GP Extended hours         | 237583737 | 237583737      | Dx code - GP consultations      | 9am-12pm Sat                         | Hub X    | CCG1             | ASID:348583204958            |
| 9               | Hub Y - Urgent Treatment centre   | G57392    | 968472747      | Dx code - GP consultations      | 8am-10pm Every Day                   | Hub Y    | Anyone           | ASID:857372758372            |
| 10              | GP Practice B - Antenatal clinic  | 725472616 | 725472616      | DX CODE - Maternity nurse check | 18:00-20:00 TUE                      | GP-B     | G67576           | ODS:G67576                   |

## Appointment slot configuration in provider systems

Generally slots will be configured for a partiucular "clinic" at a specific location. This will have types associated with the clinician (e.g. GP, Nurse etc..) or the type of service (minor injury or illness etc..).

### DoS Service Search

Services are searched by the 111 System using the DoS Search SOAP API.

### DoS Service Search Results

The response returned from DoS ranks the services in the order in which they should be used for transfers of care.  The details returned include all the information required to support the ongoing transfer of care process including technical integration methods.  

### Scenarios:

* A patient registered at GP-A, with their preferred location branch location: GP-A1
* During the day, an assessment by an urgent care service that determines the patient needs a GP should return services 1, 2 or 9.   
  * This is because the patient is registered with GP Practice A.
  * 1 and 2 give you ODS code and 9 the ASID.  So system knows how to find the service in SDS
  * 1 and 2 will return a GP Connect interaction type and 9 will return a CareConnect interaction type
  * 1 and 2 actually return the same GP Connect endpoint and will return the same slots at both locations 
  
A 111 system has to use the GP Connect specification to check patient registration and preferred location. It will therefore display appointments in order of preference (so for the example patient here, GP-A will be returned first)
Patient registered at GP-A, 9pm Thursday, need GP - should return services 7 and 9

* Service 7 is a CareConnect service (indicated by the ASID: prefix on address).
* Service 9 is a CareConnect service (indicated by the ASID: prefix on address).

* A patient registered at GP-A, presenting at 10am on a Saturday, with a need GP outcome - should return services 8,7 and 9
  * Service 8 is a CareConnect service (indicated by the ASID: prefix on address).
  * Service 7 is a CareConnect service (indicated by the ASID: prefix on address).
  * Service 9 is a CareConnect service (indicated by the ASID: prefix on address).

* A patient registered at GP-A, presenting at 7pm Tues, with a need GP outcome - should return services 6 and 9.  
  (*Note: 10 is NOT returned - as the assessment outcome does not match and nor does the commissioned ODS codes.*)
  * Service 6 is GP Connect service (indicated by the ODS: prefix).
  * Service 9 is a CareConnect service (indicated by the ASID: prefix on address).

* A patient registered at GP-B, presenting at 7pm on a Tuesday, needs a maternity nurse check. 
  * This should return service 10. But when you do the query appts for the extended hours GP slots may be returned
  * Service 10 is a GP Connect service (indicated by the ODS: prefix on address).
