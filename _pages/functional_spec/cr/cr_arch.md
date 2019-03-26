---
title: Appointment Management - Architecture
sidebar: cr_sidebar
keywords: specification
permalink: cr_arch.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

In order to support finding, and therefore cancelling of appointments, a central registry of appointments is proposed. This will be RESTful service, based around a cut-down (profiled) Appointment resource, which acts as a pointer to the actual Appointment and will support the following interactions:

* Create
  * This is called by the Provider system once an Appointment has been booked, it POSTs a profiled Appointment resource as described <a href="https://www.hl7.org/fhir/stu3/http.html#create" target="_blank">here</a>.
* Get
  * This is used where the ID is known, and retrieves a single Appointment pointer. It's not obvious where this will be used (rather than search by URL below), but as it retrieves a specific resource <a href="https://www.hl7.org/fhir/stu3/http.html#read" target="_blank">a RESTful read</a> rather than a Bundle of one resource it is simpler.
* Search by URL
  * This is used by the Provider, where the URL of the Appointment is known, but the ID of the Pointer is not known. This is a <a href="https://www.hl7.org/fhir/stu3/http.html#search" target="_blank">search</a> with a search parameter on the identifier.url, and can be used to retrieve the ID of a Pointer prior to a Get or a Delete request.
* Search by NHS Number
  * This is the main use-case, and gets all Appointment pointers for a given Patient. This is a <a href="https://www.hl7.org/fhir/stu3/http.html#search" target="_blank">search</a> with a search parameter on the participant.actor.identifier, though it will also likely need to support various filter criteria such as date ranges etc.
* Delete
  * This is used by the Provider to remove a pointer to a booked Appointment where the pointer is no longer correct, it will often (though not always) be combined with a create (where an Appointment has been moved (using a delete and create pair)). This is a RESTful <a href="https://www.hl7.org/fhir/stu3/http.html#delete" target="_blank">delete</a> operation.

The resource only needs to hold five details:

* id - The ID of the pointer resource in the registry (supplied by the registry not the Provider).
* nhsnumber - The NHS number of the patient.
* url - The URL of the actual Appointment resource.
* created - When the pointer was created.
* start - The date/time of the Appointment.

The remainder of the Appointment resource is 'boilerplate' content:
