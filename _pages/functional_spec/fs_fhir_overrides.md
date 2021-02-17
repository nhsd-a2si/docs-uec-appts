---
title: FHIR Resource Profile Overrides
sidebar: overview_sidebar
keywords: specification, fhir
permalink: fs_fhir_overrides.html
toc: false
folder: functional_spec
---
## Rationale 

## Overrides 
### Appointment 

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
|supportingInformation|0..*|1..1|
|incomingReferral|0..*|0..1|
|participant|1..*|1..1|

### HealthcareService

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|id (Booking) identifier (Base)|0..*|1..1|
|location|0..*|0..1|

### Patient 

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|id (unique in contained Appointment Resource)|-|1..1|
|identifier|0..*|0..1|
|identifier (nhsNumber)|0..*|0..1|
|identifier (nhsNumber).extension|0..*|1..1|
|identifier (nhsNumber).use|0..*|0..1|
|identifier (nhsNumber).system|0..*|1..1|
|identifier (nhsNumber).value|0..*|1..1|
|name|0..*|1..1|
|telecom|0..*|1..1|
|gender|0..1|1..1|
|birthdate|0..1|1..1|
|address|0..*|1..1|


### Schedule 

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|id (Booking) identifier (Base)|0..*|1..1|
|actor|1..*|1..3|
|actor(HealthcareService)|1..*|1..1|
|actor(Practitioner)|1..*|0..1|
|actor(PractitionerRole)|1..*|0..1|


### Slot 

|Field|Base Profile|Booking Override|
|-----|----|----------------|
|identifier|0..*|1..1|
