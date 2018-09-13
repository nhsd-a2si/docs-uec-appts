---
title: ABUS.10 Display Available Slots From a Specific Provider by Geographic Location 
sidebar: usecase_sidebar
permalink: usep_abus10.html
---

## ABUS.10 Display Available Slots From a Specific Provider by Geographic Location 
**_In order_** to book a patient into their most convenient EC, UC or GP location and time for their current disposition 

**_As a_** 111 Call Handler or urgent care service provider 

**_I want_** to view the available slots by geographic location and time from the provider service for a specified timeframe. 

### Commentary 
Where GP practices are huge joint practices or collections of federated practices, there must be a way of splitting them into locations that can then be selected.  This may also be true for other urgent care providers either now or in the future.  Ideally the list returned would be limited to those locations that fulfil the location requirement of the patient, however, if the returned list contains enough data for the user to make an informed decision with the patient/caller then this is at least a start. 

When returning appt lists from some GP providers, there can be issues where the GP provider has not set up their rotas correctly and many slots are returned that should not be booked by the urgent care consumer .  An example is provided here. 

GP Connect use case can be found at <https://nhsconnect.github.io/gpconnect/appointments_use_case_search_for_free_slots.html>

Urgent care consumers can theoretically book an appointment at any time offered even if that goes beyond the NHS Pathways disposition time frame.  Ideally any appointment interface would warn the user that they are about to book beyond the disposition time, and show by how long.  It should then ask for them to confirm that decision.  It may be that it should be possible to prevent appointments from being booked past the disposition timeframe unless requested by the patient or prevent non-clinical call handlers from exceeding that timeframe.. 

Providers may wish to demand-manage their slot collections.  GP practices may wish to have some appts available for urgent cases, and urgent care providers. 

From a 111 provider:
>_Some providers may have multiple diaries set up where clinics are being delivered by more than one clinician.
>Current proprietary solutions can offer up appointments grouped by diaries, forcing the 111 call handler to go through each diary looking for the best slot. In the national API, providers will be expected to return all the slots that match the start/end times, regardless of the provider's internal diary structure._ 

### Acceptance Criteria 
* The list **must** contain the actual geographic location of the appointment, rather than generic details of the location of the overall service provider. 
* The list **must** contain details of the start/end times of the available slots. 
* The list **must** contain details of the type of appt, such as face-to-face, video, telephone call-back. 
* The request **must** include the fact that the consumer system delivers urgent care.  The provider system will then able to filter back to the consumer those slots that they have released for urgent care. 
* The request **must** have a date/time window specified by the consumer system.  It will be for the consumer system to define what window they deem to be acceptable.  It is expected that the window will be derived from the disposition of the patient, but it will be for the developers of the consumer system to define what ranges will be appropriate for each occasion. 
* The request **must** include the coded disposition of the patient.  This will enable provider systems to return the best slots that meet the requirement, whilst also maintaining a level of demand management. 
* The slots provided **must** be for a service that can respond to the current disposition of the patient. 
* The list **may** mark those appts that do/do not meet the current disposition timeframe, making it easier for urgent care staff and the patient to make an informed decision. 
* The list **may** mark those appts that do not meet the current disposition timeframe, making them unbookable, if the user of the system does not have sufficient clinical authority to book appts outside the disposition timeframe. 
* The available appts **must** be capable of being retrieved from any provider, regardless of the relationship that the consuming user's organisation has with that provider. 
* The available appts **must** be capable of being retrieved by a consumer system from any provider system where there are data sharing agreements loaded on the Spine, to be accessed by the Spine Security Proxy (SSP). 
* The method of retrieval **must** not depend on any pre-installed data linkage processes between the requesting user's organisation and the provider organisation. 
* Where there are no available slots, the provider **must** send an appropriate response to indicate this. 
* The provider system **must** return available slots without requiring the potential patient to be "registered" with the provider. 
* This list **may** be capable of being quickly refreshed by the user or automatically as a timed event. 
* Where the provider has a number of diaries available to fulfil a request (say, when 2 or more clinicians are delivering surgeries at the same site) the provider must return all of those slots as part of the initial response. 
