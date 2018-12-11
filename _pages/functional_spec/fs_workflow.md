---
title: Workflow and Interactions
sidebar: overview_sidebar
keywords: specification
permalink: fs_workflow.html
toc: true
folder: functional_spec
---

{% include note-notpublished.html %}

## Introduction
This section describes the message interactions that happen as part of the main booking workflow. It will define the key parameters and attributes required to progress through the booking flow.

Below is the primary data model that describes the key data items that are required.

### Primary Data Model

<img src="_pages/functional_spec/img/UEC_Appointments_Flow.png">

The sections below will step through the process.

## The Actors

There are a number of different systems involved in the end to end booking process. These fall into the following catagories:

* Consumer System
* National Infrastructure
* Provider System

<img src="_pages/functional_spec/img/Actors.png">

### Consumer Systems

The Consumer System is the IT system that is being used by the service that is searching for an appropriate appointment for the patient. The system will participate in discovery of the appropriate service, discovery of its booking endpoint, searching the providing system for appropriate slots and then booking one of those slots for the patient. 

### National Infrastructure

During the booking process a number of systems that are hosted by NHS Digital as national infrastructure need to be interacted with. These are as follows:

#### Patient Demographic Service (PDS)
The Patient Demographic Service is a Spine service that enables matching captured demographics against a national demographic  repository. PDS verified demographics, in particular NHS number is required by a lot of interoperability in the NHS. **A spine verified NHS number, either by direct verification on PDS or through a Spine Mini Service Provider (SMSP) is required for booking using this standard**.

####  National DoS
The national DoS can be used to discover the most appropriate service for the patient. If that service offers appointments the necessary information required to query SDS for the endpoint will be provided. 

#### Spine Directory Service (SDS)
The SDS performs the role of the booking endpoint directory. Endpoints for the booking API of target provider systems will be registered on the SDS as part of <A href="https://nhsd-a2si.github.io/docs-uec-appts/assurance_supplier.html" target="_blank">assurance</a>.

#### NHS Authentication service
An NHS authentication service will be used to provide a digital identity to ensure that the consuming service has authorisation to make a booking.

For this booking standard, the authentication service validates credentials passed by the consumer system and subject to this check, issue a short lived (1 hour) access token which the consumer system must include in a http Authorization header in all requests to the provider system.

#### Spine Secure Proxy (SSP)
The SSP brokers and routes connections to endpoints. In order to facilitate urgent appointment booking it is important to support the ability to establish connections between systems on-the-fly without prior networking or security configuration between two specific systems. In order to do this all communications between systems are brokered via the SSP. That way systems involved in booking only ever need to establish and accept connections from/to the SSP which can be configured once, as part of <A href="https://nhsd-a2si.github.io/docs-uec-appts/assurance_supplier.html" target="_blank">assurance</a>

### Provider Systems
The provider system is the system that is offering appointments to be booked into. This system will be configured to accept connections from the SSP and will offer the defined capabilities in this standard via its FHIR Interface. There are many different service types that could be a booking provider including UTC's, OOH GP's, Emergency Dental services etc.. 

## Service Discovery

The first step of the booking process involves some form of service discovery. Typically this will use the <a href="https://digital.nhs.uk/services/directory-of-services-dos" target="_blank">Urgent Care Directory of Services (known as the "DoS")</a> to identify the most appropriate service to meet the patients needs. 

In the situation the DoS is being used there will be the initial call to the DoS API to return the ordered list of appropriate services (`CheckCapacitySummary`). 

<img src="_pages/functional_spec/img/ServiceDiscovery1.png">

Once the chosen service has been selected the next call to the DoS API is made (`ServiceDetailsByID`) and this will return the specific details of the selected service including, where the service offers appointment booking, something called an Accredited System Identifier (ASID).

<img src="_pages/functional_spec/img/ServiceDiscovery2.png">

An ASID is used to obtain the endpoint for booking into the Provider system.

## Endpoint Discovery

The consumer system uses SDS to resolve the FHIR Endpoint Server Root URL. SDS is queried using the ASID obtained from the previous step.

This is a two step process:

1. Obtaining the nhsAS object that contains an MHS Party Key.
2. Obtaining the nhsMHS object that contains an nhsMHSEndPoint.

Step 1:

<img src="_pages/functional_spec/img/EndpointDiscovery1.png">

Given an ASID of 123456789012 a query can be made to obtain the nhsMHSPartyKey of the nhsAS object, for example:

```json
ldapsearch -b uniqueIdentifier=123456789012,ou=Services,o=nhs nhsMHSPartyKey
Response:
nhsMHSPartyKey: A12345-1234567
```
The value returned is needed for step 2:
<img src="_pages/functional_spec/img/EndpointDiscovery2.png">

Step 2:
A request for the nhsMHS object can then be made using the interaction and Party Key:

<img src="_pages/functional_spec/img/EndpointDiscovery3.png">
```json
ldapsearch -b ou=Services,o=nhs "(&(nhsMHSPartyKey= A12345-1234567)(urn:nhs:names:services:careconnect:fhir:rest:create:appointment))" nhsMHSEndPoint
Response:
nhsMHSEndPoint: https://server.domain.nhs.uk/fhir_base
```
The value returned is the endpoint required to build an SSP request.

<img src="_pages/functional_spec/img/EndpointDiscovery4.png">

Before making a call to the FHIR endpoint, the consumer system needs to obtain an access token from NHS authentication service. This uses an OAuth Client Credentials grant making a call to the token endpoint of the NHS authentication service, including the following values:
```json
grant_type=client_credentials
client_id=[issued during assurance].
client_secret=[issued during assurance].
scope=[https://host.nhs.uk/baseurl/.default]
```
We’ve yet to finalise the set of scopes that the client is asking for, but it’ll be as a minimum:

* appointment/*.write
* slot/*.read
* schedule/*.read
* location/*.read
* organization/*.read
* healthcareservice/*.read

Assuming the credentials match, then the Authentication server returns an access token encoded as a JWT.

This access token is then passed in the Authorization http header in all calls to a provider system.

Using the access token the provider system can:
* Determine the identity of the consumer system.
* Be reassured that the consumer system has gone through the appropriate assurance to request slots and/or book appointments.
* Determine that the consumer system is involved in the provision of direct patient care (rather than for administrative purposes).
* Determine the care setting (e.g. urgent care, routine care Etc) for which the consumer system is requesting slots or booking an appointment.

## Get Slots

The first request to the SSP will be to get available slots. The request returns the slot resource from the target service. the request URL has three parts:

1. The SSP proxy URL
2. FHIR endpoint server root URL
3. FHIR resource location and request parameters

<img src="_pages/functional_spec/img/GetSlots1.png">

Once the request is made at the SSP, it is passed through to the FHIR endpoint at the provider service.
<img src="_pages/functional_spec/img/GetSlots2.png">

This will return a FHIR slot resource bundle for example:
<div markdown="span" class="bs-callout bs-callout-code">
```json
{
  "resourceType": "Bundle",
  "type": "searchset",
  "entry": [
    {
      "fullUrl": "Schedule/14",
      "resource": {
        "resourceType": "Schedule",
        "id": "14",
        "meta": {
          "versionId": "1469444400000",
          "profile": [
            "https://fhir.nhs.uk/STU3/StructureDefinition/NHS-Schedule-1"
          ]
        },        
        "actor": [
          {
            "reference": "Location/17"
          },
          {
            "reference": "Practitioner/2"
          }
        ],
        "comment": "Schedule 1 for general appointments"
      }
    },
    {
      "fullUrl": "Practitioner/2",
      "resource": {
        "resourceType": "Practitioner",
        "id": "2",
        "meta": {
          "versionId": "636064088099800115",
          "profile": [
            "https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"
          ]
        },
        "identifier": [
          {
            "system": "https://fhir.nhs.uk/Id/sds-user-id",
            "value": "S001"
          }
        ],
        "name": {
          "family": [ "Black" ],
          "given": [ "Sarah" ],
          "prefix": [ "Mrs" ]
        },
        "gender": "female"
      }
    },
    {
      "fullUrl": "Slot/1584",
      "resource": {
        "resourceType": "Slot",
        "id": "1584",
        "meta": {
          "versionId": "1471219260000",
          "profile": [
            "https://fhir.nhs.uk/STU3/StructureDefinition/NHS-Slot-1"
          ]
        },        
        "schedule": {
          "reference": "Schedule/14"
        },
        "status": "free",
        "start": "2016-08-15T11:30:00.000+01:00",
        "end": "2016-08-15T11:59:59.000+01:00"
      }
    },
    {
      "fullUrl": "Slot/1644",
      "resource": {
        "resourceType": "Slot",
        "id": "1644",
        "meta": {
          "versionId": "1471219260112",
          "profile": [
            "https://fhir.nhs.uk/STU3/StructureDefinition/NHS-Slot-1"
          ]
        },        
        "schedule": {
          "reference": "Schedule/14"
        },
        "status": "free",
        "start": "2016-08-15T12:00:00.000+01:00",
        "end": "2016-08-15T12:29:59.000+01:00"
      }
    }
  ]
}
```
</div>

## Book Appointment

The booking is made following a similar process as getting available slots. However this time a post is made to the SSP with a serialised {% include FHIRSpecificationLink.html include.word="FHIR appointment resource" %} as the payload.

<img src="_pages/functional_spec/img/BookAppointment1.png">

This will be passed through to the provider FHIR endpoint

<img src="_pages/functional_spec/img/BookAppointment2.png">

If a booking is successfully created a  `201: Created` HTTP status code will be returned.

<img src="_pages/functional_spec/img/BookAppointment3.png">

If the slot has been taken the response would have a `422 status (see details)` as the request “…violated applicable FHIR profiles or server business rules”.

The response body would be an OperationOutcome containing an explanation of the problem.
