---
title: FHIR Resource Profile Overrides
sidebar: overview_sidebar
keywords: specification, fhir
permalink: fs_fhir_overrides.html
toc: false
folder: functional_spec
---
## Rationale 
The Booking Standard attempts to align with unmodified versions of the <a href="https://fhir.hl7.org.uk/StructureDefinition" target="_blank">CareConnect FHIR Profiles</a> to increase familiarity and ensure validation works without an excessive number of exceptions to maintain. On occassions though it is necesary for the Booking Standard to deviate from the defaults and below is a list of the affected profiles and related overrides. 

The main reason for the overriding the profiles is because there is a reilance on data that, as default, is not mandatory. For example, the Booking Standard stipulates a requirement for start and end, within Appointment, to be populated, ensuring a time period is allocated and agreed between the Provider and Consumer and something tangiable can be given to the patient. Furthermore, the decision to utilise contained resources was an attempt to simplify the inital implementations, rather than adopt standard FHIR bundles. 

## Overrides 
### <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Appointment-1" target="_blank">Appointment</a>

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|contained resources|-|1..1|
|contained[0] (DocumentReference)|-|1..1|
|contained[1] (Patient)|-|1..1|
|contained[2] (Slot)|-|1..1|
|start|0..1|1..1|
|end|0..1|1..1|
|created|0..1|1..1|
|description|0..1|1..1|
|supportingInformation|0..\*|1..1|
|incomingReferral|0..\*|0..1|
|participant|1..\*|1..1|

### <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1" target="_blank">HealthcareService</a>

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|id (Booking) identifier (Base)|0..\*|1..1|
|location|0..\*|0..1|

### <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1" target="_blank">Patient</a>

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|id (unique in contained Appointment Resource)|-|1..1|
|identifier|0..\*|0..1|
|identifier (nhsNumber)|0..\*|0..1|
|identifier (nhsNumber).extension|0..\*|1..1|
|identifier (nhsNumber).use|0..\*|0..1|
|identifier (nhsNumber).system|0..\*|1..1|
|identifier (nhsNumber).value|0..\*|1..1|
|name|0..\*|1..1|
|gender|0..1|1..1|
|birthdate|0..1|1..1|
|address|0..\*|1..1|
|telecom.rank (if telecom is populated)|0..1|1..1|
|contact.telecom.rank (if telecom is populated)|0..1|1..1|


### <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Schedule-1" target="_blank">Schedule</a>

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|id (Booking) identifier (Base)|0..\*|1..1|
|actor|1..\*|1..3|
|actor(HealthcareService)|1..\*|1..1|
|actor(Practitioner)|1..\*|0..1|
|actor(PractitionerRole)|1..\*|0..1|


### <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Slot-1" target="_blank">Slot</a>

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|identifier|0..\*|1..1|
