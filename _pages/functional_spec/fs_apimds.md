---
title: Appointment Types
sidebar: overview_sidebar
keywords: specification
permalink: fs_apimds.html
toc: false
folder: functional_spec
---

Below is a list of the key mandarory elements for the appointment and associated resources:

* Appointment
  * DocumentReference (ID - e.g. 111CDA document)
  * PatientObject (ID - see below)
  * Created (Timestamp)
  * Slot Reference
  * Profile (URL)
  * Resource Language Setting (en or en-GB)
  * Status (e.g. Booked)
  * Participant (container)
  * SupportingInformation (element that points to the contained DocumentReference)
* Patient
  * Identifier
  * Verification Status
  * Name (given and family)
  * ~~ContactPoint (email or phone)~~
  * Gender
  * Birthdate
  * Address
   * Use
   * Postcode  
