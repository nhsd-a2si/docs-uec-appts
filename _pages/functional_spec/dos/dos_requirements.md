---
title: Interactions with the DoS
sidebar: dos_sidebar
keywords: specification
permalink: dos_requirements.html
toc: false
folder: dos
---

{% include note-notpublished.html %}

# Key Requirements

For the three key actors in this process there are the following key requirments:

* The appointment consumer (111 system in the example above):
  * MUST be able to retreive the HealthcareServiceID from the endpoint details returned from the DoS
  * MUST ensure that the booking functionality invoked is compliant with the national standards when a booking endpoint (HealthcareServiceID) is returned
  * MUST ensure that if no booking endpoint is returned by the GetServiceDetailsByID API call that any proprietary booking mechanisms are then tried and still work
* The DoS:
  * MUST be able to store the HealthcareServiceID
  * MUST return a booking ASID (HealthcareServiceID) as part of its endpoint data
* The appointment provider (GP Federation system in the example above):
  * MUST allow association of a booking diary with a HealthcareServiceID
  * MUST ensure that two different diaries cannot be associated with the same HealthcareServiceID UNLESS there is a clear use case for slots from multiple schedules to be returned in one schedule bundle and therefore be considered by a booking consumer as a single service.
