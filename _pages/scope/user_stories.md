---
title: User Stories
sidebar: overview_sidebar
permalink: user_stories.html
---

## ABUS.01 Display Possible Provider Services
**_In order_** that the patient can choose their most convenient provider or the provider that they think most closely serves their need

**_As a_** 111 Call Handler or urgent care service provider

**_I want_** to view the all the provider services that could currently assist the patient with a certain disposition.

### Commentary
Whilst not strictly concerning the new messaging/API for appt booking, searching DoS (directory of services) for a provider is a key precursor to appt booking.

### Acceptance Criteria
* The list **must** include all possible providers that can support a patient with the current disposition, regardless of the location/organisation of the call handler making the request.
* The list **must** be sorted so that the most appropriate provider is sorted to the top of the list. Appropriateness of the provider is defined by the distance from the patient's current location.
* The list **must** provide the location details of the provider (so that the patient can help to assess which provider really has the most convenient location)
* Possible data items to display:
    * Name of provider
    * Address of provider where the care will be offered (not the business address of the provider organisation)
    * Distance from patient

<br>

## ABUS.02 Display Appt Availability Status of Providers
**_In order_** that the patient can quickly be informed of what services have free appts and the call can be completed more quickly

**_As a_** 111 Call Handler or urgent care service provider

**_I want_** to view the appt availability of all the provider services that could currently assist the patient with a certain disposition when, or shortly after, that list is returned from the DoS.

### Commentary
Suppliers of consumer systems may wish to consider whether they wish to immediately access the provider systems listed to, for example, return a simple count of the number of appts that are available at the provider during the disposition timeframe.  Suppliers may wish to return and display the DoS data and then follow-up with the counts of free appts as the API calls are successfully made and returned.

The user interface could also show all the ‘next available appointment within time frame’ displayed for each individual location. so they don’t have to hunt through various diaries to find a slot.

During conversation with the patient, it is possible that the situation will change.  Suppliers of consumer software may wish to consider whether they can offer a manual or automatic refresh facility for this list.

Suppliers (and users) should be mindful that some scenarios for returning appointments may return more 'possible' appointments than the user may actually wish to choose from.  For example, an occasion where a GP practice returns all available appointments for the practice, but in reality the user is only interested in those appointments for a specific branch surgery.

### Acceptance Criteria
* The list **may** include details of free appts available at this DoS location, such as the count of free appts available at each location, within the current disposition timeframe.
* The list **may** include the earliest appt time available at each location, within the current disposition timeframe.
* This list **may** be capable of being quickly refreshed by the user or automatically as a timed event.

<br>

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

<br>

## ABUS.12 Confirm/Book an Appointment Slot 
**_In order_** that the patient can be assured that the provider will see them on or around the allotted time at the selected location 

**_As a_** 111 Call Hander or urgent care service provider 

**_I want_** to confirm/book an offered appointment slot with the provider. 

### Commentary 
Current proprietary solutions seem to have a two-step booking process where the slot is reserved and then confirmed/booked by the process of sending the ITK message with clinical details.  GP Connect does not have this method.  The appt is just booked in a single message exchange. 

Urgent care settings will book patient appts at GP practices where they are not registered for general medical services. 

The meeting between UC and GPC (31-Aug-2017) confirmed that, for now, UC would use the same protocols as GPC.  Appts would be immediately booked and, if the caller decides not to continue, then the appt will be cancelled. 

GP Connect use case can be found at <https://nhsconnect.github.io/gpconnect/appointments_use_case_book_an_appointment.html>

### Acceptance Criteria 
* The request to confirm the appt slot **must** contain all the data to enable the provider to uniquely identify the slot and confirm the appt. 
* The request **must** contain textual details to indicate the reason for the appt. 
* The provider system **must** accept the appt booking even if the patient is not "registered" with this provider. 
* The provider system **must** confirm that the slot has been booked or must return a response to indicate that the booking confirmation has failed. 

<br>

## ABUS.13 Warn Users Where Appts are Outside Disposition Timeframe 
**_In order_** that the patient and their call handler or clinician can make an informed decision of the appropriate timescale and location of service that best meets the patient's needs and situation 

**_As a_** 111 Call Hander or urgent care service provider 

**_I want_** to be warned if the appt slot I am about to book falls outside of the disposition timeframe for this patient. 

### Commentary 
Urgent care can theoretically book an appointment at any time offered even if that goes beyond the NHS Pathways disposition time frame.  Ideally any appointment interface should warn the user that they are about to book beyond the disposition time, and show by how long.  It should then ask for them to confirm that decision. It may be that it should be possible to prevent appointments from being booked past the disposition timeframe unless requested by the patient. 

### Acceptance Criteria 
* The request to confirm the appt slot **must** warn the user if they are about to book an appt that is outside the disposition timeframe. 
* The user warning **should** include details of by how long the appt fails to meet the disposition timeframe. 
* The system **must** ensure that the user confirms a decision to continue. 
* The system **may** include, as part of the confirmation, an assertion from the user that the patient (or their carer) has has made an informed decision to accept an appt is outside the disposition timeframe. 

<br>

## ABUS.20 Display any Booked Appointments for a specific Patient/Service Provider 
**_In order_** that the patient can confirm what appts are already booked for them at a provider or an urgent care clinician can check the attendance status of a patient's appt 

**_As a_** 111 Call Handler or urgent care service provider 

**_I want_** to retrieve the details of appts booked for a patient with a specific service provider. 

### Commentary 
Patients (or their representatives) may contact an urgent care provider (such as 111) to confirm details of an appt that has already been made.  This may be just to be reminded of the details or so that they can amend/delete that appt.  Regardless of the reason, the urgent care service provider taking the call will have a requirement to make a request to another provider to retrieve the details of this appt.  

111 systems are not nationally integrated and therefore if a caller comes into a 111 service different from the one where the appt was raised, the new 111 will not have access to the original call history or appt details.  

It may be that the patient has already missed the booked appt.  Therefore, the acceptance criteria includes a requirement for the request to cover a time window that is defined by the requesting system. 

Additionally, urgent care clinicians may wish to query provider systems to confirm that the patient has attended their appt.  If they have failed to attend, there are occasions when the clinician will call back to check on the patient. 

GP Connect use case can be found at <https://nhsconnect.github.io/gpconnect/appointments_use_case_retrieve_a_patients_appointments.html> 

### Acceptance Criteria  
* The consumer system **must** be capable of querying any provider system, regardless of what relationship the provider organisation has with the consumer organisation. 
* The patient's appts **must** be capable of being retrieved by a consumer system from any provider system where there are data sharing agreements loaded on the Spine, to be accessed by the Spine Security Proxy (SSP). 
* The request **must** have a date/time window specified by the consumer system.  It is expected that the window will be based on the conversation with the patient and may include a start date/time that is in the past.  It will be for the developers and users of the consumer system to define what ranges will be appropriate for each occasion. 
* The provider system **must** return a list of appts booked for this patient (within the time window provided) or must return a response to indicate that there are no matching appts. 
* The list of appts returned **must** include the appt status and a unique reference for the appt. 

### Notes 
For example, a restricted list from the FHIR base valueset for AppointmentStatus could meet the needs for Urgent Care: 

<http://hl7.org/fhir/valueset-appointmentstatus.html> 

|    Code   |  Display  | Definition |
|:---------:|:---------:|------------|
|  pending  | Pending   |Some or all of the participant(s) have not finalized their acceptance of the appointment request. |
|   booked  |  Booked   | All participant(s) have been considered and the appointment is confirmed to go ahead at the date/times specified.  |
|  arrived  |  Arrived  | Some of the patients have arrived. |
| fulfilled | Fulfilled | This appointment has completed and may have resulted in an encounter. |
| cancelled | Cancelled | The appointment has been cancelled. |
|   noshow  |  No Show  | Some or all of the participant(s) have not/did not appear for the appointment (usually the patient). |

<br> 

## ABUS.21 Cancel a Booked Appointment for a specific Patient/Service Provider 
**_In order_** that the patient or their carer can cancel or rearrange an already-booked appointment at a specific provider 

**_As a 111_** Call Handler or urgent care service provider 

**_I want_** to cancel appts booked for a patient with a specific service provider. 

### Commentary 
The capability to cancel an appointment gives the ultimate capability of also amending an appt as an amendment is effectively a cancel followed by a re-book.  There is still a user story to cover the amendment of an appt, but this will not cover amending details such as date/time/location. 

As urgent care providers (definitely 111s) can receive calls for different regions they must have the ability to cancel appts that they did not actually raise.   

It may be that the provider system cannot cancel the appt.  User systems will have to have protocols in place to handle all returned statuses. 

GP Connect use case can be found at <https://nhsconnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html>

### Acceptance Criteria  
* The consumer system **must** be capable of cancelling slots for any provider system, regardless of what relationship the provider organisation has with the consumer organisation 
* The patient's appts **must** be capable of being cancelled by a consumer system at any provider system where there are data sharing agreements loaded on the Spine, to be accessed by the Spine Security Proxy (SSP). 
* The consumer system **must** provide visible confirmation to the user of the status returned by the provider system  ie. whether the requested appt was successfully cancelled or not.  Example returned statuses could be: 
   * Appt successfully cancelled 
   * Not cancelled - system failure 
   * Not cancelled - appt requested was not found 
   * Not cancelled - appt was not for this patient 
   * Not cancelled - appt was already in the past 
   * Not cancelled - appt was already cancelled 
* The provider system *must not* be required to inform the patient of the cancellation of the appt.  Business/clinical responsibility for informing the patient must remain with the consumer organisation. 

<br> 

## ABUS.22 Amend a Booked Appointment Reason for a specific Patient/Service Provider 
**_In order_** that the service provider has the correct reason for the appt displayed on their system 

**_As a_** 111 Call Handler or urgent care service provider 

**_I want_** to amend the appt reason for a previously booked appt, where the reason has changed or was erroneously provided to the service provider. 

### Commentary 
GP Connect offers the message set to enable the reason for the appt to be amended.  For the use case go to <https://nhsconnect.github.io/gpconnect/appointments_use_case_amend_an_appointment.html>

### Acceptance Criteria  
* The consumer system *must* be capable of amending slots for any provider system, regardless of what relationship the provider organisation has with the consumer organisation 
* The patient's appts *must* be capable of being amended by a consumer system at any provider system where there are data sharing agreements loaded on the Spine, to be accessed by the Spine Security Proxy (SSP). 
* The user's system *must* provide visible confirmation to the user of the status returned by the provider system  ie. whether the requested appt reason was successfully amended or not.  Example returned statuses could be: 
   * Appt successfully amended 
   * Not amended - system failure 
   * Not amended - appt requested was not found 
   * Not amended - appt was not for this patient 
   * Not amended - appt was already in the past 
   
 ## ABUS.23 DoS Interaction
 
 
 
 <div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; version=\&quot;9.1.0\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;device\&quot;&gt;&lt;diagram name=\&quot;Page-1\&quot; id=\&quot;13e1069c-82ec-6db2-03f1-153e76fe0fe0\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

