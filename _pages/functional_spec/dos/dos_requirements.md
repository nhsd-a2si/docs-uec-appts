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

* The appointment consumer:
  * MUST be able to retreive the HealthcareServiceID from the endpoint details returned from the DoS
  * MUST ensure that the booking functionality invoked is compliant with the national standards when a booking endpoint (HealthcareServiceID) is returned
  * MUST ensure that if no booking endpoint is returned by the relvant DoS API call that any other proprietary booking mechanisms still work and are then subsequently tried
* The DoS:
  * MUST be able to store the HealthcareServiceID
  * MUST return a booking ASID (HealthcareServiceID) as part of its endpoint data
* The appointment provider:
  * MUST allow association of a HealthcareServiceID (which will be the ASID assigned after a service has gone through assurance) with the booking diary(s) for that service.
