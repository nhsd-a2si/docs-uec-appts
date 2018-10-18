---
title: ABUS.12 Confirm/Book an Appointment Slot 
sidebar: usecase_sidebar
permalink: usep_abus12.html
---
{% include note-notpublished.html %}

## ABUS.12 Confirm/Book an Appointment Slot 
**_In order_** that the patient can be assured that the provider will see them on or around the allotted time at the selected location 

**_As a_** 111 Call Hander or urgent care service provider 

**_I want_** to confirm/book an offered appointment slot with the provider. 

### Commentary 
Current proprietary solutions seem to have a two-step booking process where the slot is reserved and then confirmed/booked by the process of sending the ITK message with clinical details.  As a contrast, GP Connect does not have this method.  The appointment is just booked in a single message exchange. 

For UEC booking, appointments will be immediately booked.

GP Connect use case can be found at <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_book_an_appointment.html" target="_blank">GP Connect book and appointment use case</a>

### Acceptance Criteria 
* The provider system **must** accept the appointment booking even if the patient is not "registered" with this provider. 
