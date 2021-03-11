---
title: ABUS.10 Display Available Slots From a Specific Service
sidebar: overview_sidebar
permalink: usep_abus10.html
---

## ABUS.10 Display Available Slots From a Specific Service
**_In order_** to book a patient into the selected provider service 

**_As a_** Integrated Urgent Care Service Provider 

**_I want_** to view the available slots for a provider service for a specified timeframe.

### Commentary 
The list returned must be limited to only appointment slots at appropriate locations, for example: 
  * display available appointments for a specific GP
  * display available appointments for a GP Extended Access Hub
  * display appointments for an Urgent treatent Centre

GP Connect use case can be found at <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_search_for_free_slots.html" target="_blank">GP Connect search for free slots use case</a>

### Acceptance Criteria 
* The list **must** contain the actual geographic location of the appointment, rather than generic details of the location of the overall service provider. 
* The list **must** contain details of the start/end times of the available slots. 
* The available appointments **must** be capable of being retrieved from any provider, regardless of the relationship that the consuming user's organisation has with that provider (does not apply to GP Connect booking). 
* The method of retrieval **must** not depend on any pre-installed data linkage processes between the requesting user's organisation and the provider organisation. (does not apply to GP Connect booking). 
* Where there are no available slots, the provider **must** send an appropriate response to indicate this.
* Where there are no available slots, the consumer **must** present an appropriate message to the user to indicate this. 
* The provider system **must** return available slots without requiring the potential patient to be "registered" with the provider. 
* Where the provider has a number of diaries available to fulfil a request (say, when 2 or more clinicians are delivering surgeries at the same site) the provider **must** return all of those slots as part of the initial response. 
