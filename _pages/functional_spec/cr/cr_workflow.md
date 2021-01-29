---
title: Appointment Management - workflow
sidebar: cr_sidebar
keywords: specification
permalink: cr_workflow.html
toc: false
folder: functional_spec
---

With the UEC Booking Standard there is no specific Rebook functionality. The reason for this is that any need for a change to an appointment should require a re-assessment and be considered as a new encounter. Only once this assessment has been completed (including any new bookings associated with that encounter) would the consumer system then cancel any appointments that they are aware of that would no longer be appropriate. It is worth noting that depending on the capabilities of the system being used to make the reassessment the original appointment may not be cancelled.

### Workflows

There are a number of workflows where the cancel/rebook capability can be demonstrated.

Below is a typical scenario that would require what could be described operationally as "re-booking":

* On a Friday afternoon, Mr. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and an appointment is made at an appropriate service, near their home, in 6 hours time. 
* an appointment is booked at their local Urgent Treatment Centre
* An hour later he feels much worse so calls 111 back. 
* Mr. Patient is reassessed and a new assessment outcome is reached. An urgent appointment is required within 2 hours so the booking process is entered. 
* The appointment booking process is completed and the consumer system sends a booking confirmation for the new booking to the provider service.
* The list of existing relevent appointments is displayed to the 111 user (in this case there is just one appointment)
* The user confirms with Mr. Patient the correct appointment that was previously booked and that this appointment will be cancelled and a new appointment booked.
* In the background the 111 system then cancels the previous appointment (confirmed above).

Now consider a slightly different, less common but still likely scenario where the orignal appointment is never cancelled:

* On a Friday afternoon, Whilst at work, Mrs. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and an appointment is made at an appropriate service, near their home, in 12 hours time. 
* When the appointment is confirmed by the providing system, it creates a record on the Appointment Registry for that patient.
* An hour later Mrs. Patient goes home.
* When she arrives home she feels much worse so calls 111 back. 
* Now she is at home, she reaches a different 111 service from the one she called whilst at work
* Mrs. Patient is reassessed and a new assessment outcome is reached. An urgent appointment is required at the same Urgent Treatment Centre, but within 2 hours so the booking process is entered. 
* The appointment booking process is completed at the UTC service and the provider system sends a booking confirmation for the new booking to the provider service.
* The original appointment still exists on the system as the 111 service making the more urgent booking has no knowledge of the prior booking and would have to be dealt with locally when then patient arrives for the new more urgent appointment.

### Consuming system:

* At the end of any re-assessment, the option to cancel the original appointment needs to be offered
