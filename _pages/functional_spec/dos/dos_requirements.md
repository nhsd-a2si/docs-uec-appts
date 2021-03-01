---
title: Interactions with the DoS
sidebar: overview_sidebar
keywords: specification
permalink: dos_requirements.html
toc: false
folder: dos
---

# Key Requirements

For the three key actors in this process there are the following key requirments:

* The booking consumer:
  * MUST be able to retreive the SDS record pointer (e.g. ASID or ODS code) from the endpoint details returned from the DoS
  * MUST ensure that the booking functionality invoked is compliant with the national standard when a booking endpoint is returned
  * MUST ensure that if no booking endpoint is returned by the relvant DoS API call that any other proprietary booking mechanisms still work and are then subsequently tried
* The DoS:
  * MUST be able to store the SDS record pointer (e.g. ASID or ODS code)
  * MUST return a booking ASID or ODS as part of its endpoint data (in the correct form)
* The booking provider:
  * MUST allow association of the discovered service with the booking diary(s) for that service (for example the DoS Service ID).
