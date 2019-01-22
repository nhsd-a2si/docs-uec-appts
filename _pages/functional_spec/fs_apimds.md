---
title: Appointment Types
sidebar: overview_sidebar
keywords: specification
permalink: fs_apimds.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

* Appointment
  * DocumentReference (ID - e.g. 111CDA document)
  * PatientObject (ID - see below)
  * Created (Timestamp)
  * Slot Reference
  * Profile (URL)
  * Resource Language Setting (en or en-gb)
  * Status (e.g. Booked)
  * Participant (container)
  * SupportingInformation (element that points to the contained DocumentReference)
* Patient
  * Identifier
  * Verification Status
  * Name (given and family)
  * > ContactPoint (email or phone)
  * Gender
  * Birthdate
> * Address
 > * Use
 > * Postcode  
