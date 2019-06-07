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
* If an endpoint exists in the metadata for appointments, the 111 IT System will display to the user that appointments are bookable at this service, and so the user can choose to book the patient in
* The 111 IT System will use the endpoint information to retrieve the booking API endpoint from SDS - **SDS Endpoint Search**
* A request will be made for appointment slots from the 111 IT System to the chosen Service Provider IT system, using the retrieved API endpoint to retrieve all available and appropriate slots from the appointment schedules at the chosen service - **GP Connect or CareConnect Appointment Slot Search**
* The Service Provider IT system will return available slots and the user will choose one and then follow the process to book in (*note: this is not in these notes as that is detailed in the appropriate API specification*)

This guidance shows how areas highlighted in bold above are used in combination to return the appointment capability for services.

The methods used for GP Connect appointment booking are different from CareConnect in terms of the SDS Endpoint Search and the appointment FHIR APIs. The guidance will discuss those differences in the context of why this means DOS services for each type will be configured differently.  Also the behaviour of GP Connect provider systems slot return will need some consideration for the consuming 111 IT System functionality.

## Example services used in the guidance below

This guidance uses example services to illustrate how they are configured in DoS and in local provider systems in order to show the flow of 111 search for services in DoS and the use of the two different appointment standards.

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom layers lightbox&quot;,&quot;xml&quot;:&quot;&lt;mxfile modified=\&quot;2019-03-20T12:13:33.456Z\&quot; host=\&quot;www.draw.io\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; etag=\&quot;iAuZzs-lfe-xT1Sf9P38\&quot; version=\&quot;10.5.2\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;pCvT3Y6hV7biSGgpgEUX\&quot; name=\&quot;Page-1\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
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
