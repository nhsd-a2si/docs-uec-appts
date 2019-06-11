---
title: Appointment Management - Architecture
sidebar: cr_sidebar
keywords: specification
permalink: cr_arch.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

In order to support finding, and therefore cancelling of appointments, a central registry of appointments is proposed. This will be a RESTful service, based around a cut-down (profiled) Appointment resource, which acts as a pointer to the actual Appointment and will support the following interactions:

* Create
  * This is called by the Provider system once an Appointment has been booked, it POSTs a profiled Appointment resource as described <a href="https://www.hl7.org/fhir/stu3/http.html#create" target="_blank">here</a>.
* Get
  * The GET interaction is required to be used just before updating an Appointment pointer to cancelled. This makes sure that it is replaced with an equivalent (identical apart from the status change and timestamp) pointer. As it retrieves a specific resource with <a href="https://www.hl7.org/fhir/stu3/http.html#read" target="_blank">a RESTful read</a> rather than a Bundle of one resource it is simpler.
* Search by URL
  * This is used by the Provider, where the URL of the Appointment is known, but the ID of the Pointer is not known. This is a <a href="https://www.hl7.org/fhir/stu3/http.html#search" target="_blank">search</a> with a search parameter on the identifier.url, and can be used to retrieve the ID of a Pointer prior to a Get or a Delete request.
* Search by NHS Number
  * This is the main use-case, and gets all Appointment pointers for a given Patient. This is a <a href="https://www.hl7.org/fhir/stu3/http.html#search" target="_blank">search</a> with a search parameter on the participant.actor.identifier, though it will also likely need to support various filter criteria such as date ranges etc.
* Update
  * The pointer (and appointment) are replaced with a duplicate copy with a new status of ‘cancelled’ or ‘entered-in-error’. This is a RESTful <a href="https://www.hl7.org/fhir/stu3/http.html#update" target="_blank">update</a> operation.

The resource only needs to hold five details:

* id - The ID of the pointer resource in the registry (supplied by the registry not the Provider).
* nhsnumber - The NHS number of the patient.
* url - The URL of the actual Appointment resource.
* created - When the pointer was created.
* start - The date/time of the Appointment.

The remainder of the Appointment resource is 'boilerplate' content:

### Sample proposed Appointment pointer

```json
{
    "resourceType": "Appointment",
    "id": "0c55f3f6-6e7c-4a3e-b891-286b6a97f0ca",
    "meta": {
        "profile": "https://fhir.hl7.org.uk/STU3/StructureDefinition/[New Profile Name Goes Here]"
    },
    "text": "<div>Empty</div>",
    "identifier": [
        {
            "use": "official",
            "system": "urn:ietf:rfc:3986",
            "value": "https://actual.resource.location/base/Appointment/[id]"
        }
    ],
    "status": "booked",
    "created": "2018-01-17T13:36:00.000Z",
    "start": "2018-04-01T09:00:15.000Z",
    "participant": [
        {
            "actor": {
                "identifier": {
                    "use": "official",
                    "system": "https://fhir.nhs.uk/Id/nhs-number",
                    "value": "12341234123"
                }
            }
        }
    ]
}
```


