---
title: Get the FHIR® capability statement
sidebar: overview_sidebar
keywords: Capability
permalink: uec_capability.html
toc: true
folder: iops
summary: FHIR NHS Scheduling API server's capability statement
---

## Prerequisites
### Consumer
The consumer system:
* SHALL have previously resolved the organisation’s FHIR endpoint base URL through the [Spine Directory Service](https://nhsconnect.github.io/FHIR-SpineCore/build_directory.html)

## API usage
### Request operation
#### FHIR relative request

```html
GET /metadata
```


#### FHIR absolute request
```html
GET https://[proxy_server]/https://[provider_server]/[fhir_base]/metadata
```


#### Request headers
Consumers SHALL include the following additional HTTP request headers:

| Header | Value |
| :--- | :--- |
| Ssp-TraceID| Consumer’s TraceID (i.e. GUID/UUID) |
| Ssp-From | Consumer’s ASID |
| Ssp-To | Provider’s ASID |
| Ssp-InteractionID | urn:nhs:names:services:careconnect:fhir:rest:read:metadata|
| Authorisation | JWT Authorisation Token  |


#### Payload request body
N/A

#### Error handling
Provider systems are expected to always be able to return a valid capability statement.




### Request response
#### Response Headers
Provider systems are not expected to add any specific headers beyond that described in the HTTP and FHIR® standards.

#### Payload response body
Provider systems:

* SHALL return a 200 OK HTTP status code on successful retrieval of the capability statement
* SHALL return a capability statement which conforms to the standard FHIR CapabilityStatement

An example FHIR NHS Scheduling API CapabilityStatement is shown below ready for customisation and embedding into assured provider systems. Providers should use this CapabilityStatement as a base for their own CapabilityStatement, replacing the element in square brackets ([ & ]) with specific information of their implementation. The main version at the top of the CapabilityStatement should represent the FHIR NHS Scheduling API specification version which the FHIR server implements.

```json
{
  "resourceType": "CapabilityStatement",
  "version": "2.0.1",
  "name": "Care Connect",
  "status": "active",
  "date": "2021-01-20",
  "publisher": "[Provider Software Vendor Name]",
  "contact": [
    {
      "name": "[Provider Software Vendor Contact Name]"
    }
  ],
  "description": "This server implements the FHIR NHS Scheduling API version 2.0.0",
  "copyright": "Copyright NHS Digital 2016-21
  ",
  "kind": "capability",
  "software": {
    "name": "[Provider Software Name]",
    "version": "[Provider Software Version]",
    "releaseDate": "[Provider Software Release Date]"
  },
  "fhirVersion": "3.0.1",
  "acceptUnknown": "both",
  "format": [
    "application/fhir+json",
    "application/fhir+xml"
  ],
  "profile": [
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Slot-1" },
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1"},
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Schedule-1" },
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Appointment-1" },
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1" },
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DocumentReference-1"},
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1" },  
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1" },
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1" },    
      { "reference": "https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1" }
  ],
  "rest": [
    {
      "mode": "server",
      "security": {
        "cors": true
      },
      "resource": [
        {
          "type": "Appointment",
          "interaction": [
            {
              "code": "read"
            },
            {
              "code": "create"
            },
            {
              "code": "search-type"
            }
          ],
          "updateCreate": false,
          "searchParam": [
            {
              "name": "identifier",
              "type": "token",
              "documentation": "NHS Number (i.e. https://fhir.nhs.uk/Id/nhs-number|123456789)"
            },
            {
              "name": "appointmentId",
              "type": "token",
              "documentation": "Unique identifier for an appointment"
            },
            {
              "name": "version",
              "type": "token",
              "documentation": "The version identifier for the Appointment being requested."
            }
          ]
        },
        {
          "type": "Slot",
          "interaction": [
            {
              "code": "search-type"
            }
          ],
          "searchInclude": [
            "Slot.schedule",
            "Schedule:actor:Practitioner",
            "Schedule:actor:PractitionerRole",
            "Schedule:actor:HealthcareService",
            "HealthcareService.providedBy",
            "HealthcareService.location"
          ],
          "searchParam": [
            {
              "name": "service",
              "type": "token"
            },
            {
              "name": "status",
              "type": "token"
            },
            {
              "name": "start",
              "type": "date"
            },
            {
              "name": "end",
              "type": "date"
            }

          ]
        }
      ],
      "operation": []
    }
  ]
}
```
Consumer systems:

* SHOULD request the capability statement from the FHIR server endpoint in order to ascertain details of the implementation of Care Connect capabilities delivered by the FHIR server
* Consumers may also cache the capability statement information retrieved from an endpoint to reduce the number of future calls they make to the target organisation’s FHIR server.
