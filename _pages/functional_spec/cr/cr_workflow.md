---
title: Booking Management - workflow
sidebar: overview_sidebar
keywords: specification
permalink: cr_workflow.html
toc: false
folder: functional_spec
---

With the NHS Booking Standard there is no specific Rebook functionality. The reason for this is that any need for a change to a booking should require a re-assessment and be considered as a new encounter. Only once this assessment has been completed (including any new bookings associated with that encounter) would the consumer system then cancel any bookings that they are aware of that would no longer be appropriate. It is worth noting that depending on the capabilities of the system being used to make the reassessment the original booking may not be cancelled.

### Workflows

There are a number of workflows where the cancel/rebook capability can be demonstrated.

Below is a typical scenario that would require what could be described operationally as "re-booking":

* On a Friday afternoon, Mr. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and a booking is made at an appropriate service, near their home, in 6 hours time. 
* a booking is made at their local Urgent Treatment Centre
* An hour later he feels much worse so calls 111 back. 
* Mr. Patient is reassessed and a new assessment outcome is reached. An urgent booking is required within 2 hours so the booking process is entered. 
* The booking process is completed and the consumer system sends a booking confirmation for the new booking to the provider service.
* The list of existing relevent bookings is displayed to the 111 user (in this case there is just one booking)
* The user confirms with Mr. Patient the correct booking that was previously made and that this booking will be cancelled and a new booking made.
* In the background the 111 system then cancels the previous booking (confirmed above).

Now consider a slightly different, less common but still likely scenario where the orignal booking is never cancelled:

* On a Friday afternoon, Whilst at work, Mrs. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and a booking is made at an appropriate service, near their home, in 12 hours time. 
* When the booking is confirmed by the providing system, it creates a record on the Booking Registry for that patient.
* An hour later Mrs. Patient goes home.
* When she arrives home she feels much worse so calls 111 back. 
* Now she is at home, she reaches a different 111 service from the one she called whilst at work
* Mrs. Patient is reassessed and a new assessment outcome is reached. An urgent booking is required at the same Urgent Treatment Centre, but within 2 hours so the booking process is entered. 
* The booking process is completed at the UTC service and the provider system sends a booking confirmation for the new booking to the provider service.
* The original booking still exists on the system as the 111 service making the more urgent booking has no knowledge of the prior booking and would have to be dealt with locally when then patient arrives for the new more urgent booking.

### Consuming system:

* At the end of any re-assessment, the option to cancel the original booking needs to be offered
