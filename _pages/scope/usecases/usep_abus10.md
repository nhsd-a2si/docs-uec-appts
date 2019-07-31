---
title: ABUS.10 Display Available Slots From a Specific Service
sidebar: usecase_sidebar
permalink: usep_abus10.html
---

## ABUS.10 Display Available Slots From a Specific Service
**_In order_** to book a patient into the selected provider service 

**_As a_** Integrated Urgent Care Sservice Provider 

**_I want_** to view the available slots for a provider service for a specified timeframe.

### Commentary 
The list returned must be limited to only appointment slots at appropriate locations

GP Connect use case can be found at <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_search_for_free_slots.html" target="_blank">GP Connect search for free slots use case</a>

### Acceptance Criteria 
* The list **must** contain the actual geographic location of the appointment, rather than generic details of the location of the overall service provider. 
* The list **must** contain details of the start/end times of the available slots. 
* The list **may** mark those appts that do not meet the current disposition timeframe, making them unbookable, if the user of the system does not have sufficient clinical authority to book appts outside the disposition timeframe. 
* The available appts **must** be capable of being retrieved from any provider, regardless of the relationship that the consuming user's organisation has with that provider (does not apply to GP Connect booking). 
* The method of retrieval **must** not depend on any pre-installed data linkage processes between the requesting user's organisation and the provider organisation. (does not apply to GP Connect booking). 
* Where there are no available slots, the provider **must** send an appropriate response to indicate this. 
* The provider system **must** return available slots without requiring the potential patient to be "registered" with the provider. 
* This list **may** be capable of being quickly refreshed by the user or automatically as a timed event. 
* Where the provider has a number of diaries available to fulfil a request (say, when 2 or more clinicians are delivering surgeries at the same site) the provider must return all of those slots as part of the initial response. 
