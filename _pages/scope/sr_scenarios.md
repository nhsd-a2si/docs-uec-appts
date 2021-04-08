---
title: Scope & Requirement Scenarios 
sidebar: overview_sidebar
keywords: workflow requirements
permalink: sr_scenarios.html
toc: false
folder: scope
---

With the NHS Booking Standard there is no specific Rebook functionality. The reason for this is that any need for a change to a booking, outside of the current consultation context, should require a re-assessment and be considered as a new encounter. Only once this re-assessment has been completed (including any new bookings associated with that encounter) would the consumer system then cancel any other existing bookings they are aware of that would no longer be appropriate. It is worth noting that depending on the capabilities of the system being used to make the reassessment the original booking may not be cancelled, for example, where re-assessment is performed by a different service provider with no access to the original booking.

The other Rebook functionality the Standard expected systems to support is the ability to perform this action within the context of the current consultation. In line with the capabilities documented, this would align with Capability 1. Consumer systems, having made a booking during the current consultation with the patient, might attempt to rebook for an alternative time after negotiation with the patient but the workflow principles will follow the same as above i.e. having made an original booking, the new booking **should** be made prior to cancelling the first, original, one. The rationale for this is to ensure the patient is not left without a booking and intended to mitigate clinical hazards. 

{% include important.html content="If a booking is cancelled, any referral document, sent as part of that booking, should be decoupled when cancelled and not be assumed a referral in its own right." %}

### Workflows

There are a number of workflows where the cancel/rebook capability can be demonstrated.

The following is an example of cancel/rebook within a current consultation (**Capability 1**):

* On Tuesday evening, Ms. Patient feels ill so calls a 111 service.
* It is determined during this assessment that they require a face to face consultation and a booking is made at their local Urgent Treatment Centre for 09:30 the following day.
* The booking is confirmed by the Urgent Treatment Centre.
* As the details are being confirmed back to the patient, reiterating where and when they need to go and what they should do if symptoms worsen, the patient realises they cannot make 09:30 due to a prior engagement.
* The 111 user returns to the booking process, re-requests available slots at the same Urgent Treatment Centre and makes another booking for the patient at 10:30.
* The new booking is confirmed by the Urgent Treatment Centre.
* The list of existing bookings is displayed to the 111 user so the orginal booking can be cancelled.
* The user confirms with Ms. Patient the original booking, made previously, and that this booking will be cancelled because the new later booking has been confirmed.
* In the background the 111 system cancels the original booking (confirmed above).



Below is a typical scenario that would require what could be described operationally as "re-booking" (**Capability 2**):

* On a Friday afternoon, Mr. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and a booking is made at an appropriate service, near their home, in 6 hours time. 
* A booking is made at their local Urgent Treatment Centre
* An hour later he feels much worse so calls 111 back. 
* Mr. Patient is reassessed and a new assessment outcome is reached. An urgent booking is required within 2 hours so the booking process is entered. 
* The booking process is completed and the consumer system sends a booking confirmation for the new booking to the provider service.
* The list of existing bookings is displayed to the 111 user (in this case there is just one booking)
* The user confirms with Mr. Patient the original booking, made previously, and that this booking will be cancelled because the new more urgent booking has been confirmed.
* In the background the 111 system cancels the original booking (confirmed above).



Now consider a slightly different, less common but still likely scenario where the orignal booking is never cancelled:

* On a Friday afternoon, whilst at work, Mrs. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and a booking is made at an appropriate service, near their home, in 12 hours time. 
* The booking is confirmed by the providing system, it creates a record on the Booking Registry for that patient.
* An hour later Mrs. Patient goes home.
* When she arrives home she feels much worse so calls 111 back. 
* Now she is at home, she reaches a different 111 service from the one she called whilst at work
* Mrs. Patient is reassessed and a new assessment outcome is reached. An urgent booking is required at the same Urgent Treatment Centre, but within 2 hours so the booking process is entered. 
* The booking process is completed at the UTC service and the provider system sends a booking confirmation for the new booking to the provider service.
* The original booking still exists on the system as the 111 service making the more urgent booking has no knowledge of the prior booking and would have to be dealt with locally when then patient arrives for the new more urgent booking.



### Consuming system:

* At the end of any re-assessment, the option to cancel the original booking needs to be offered
