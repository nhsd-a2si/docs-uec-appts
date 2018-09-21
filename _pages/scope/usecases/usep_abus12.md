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
Current proprietary solutions seem to have a two-step booking process where the slot is reserved and then confirmed/booked by the process of sending the ITK message with clinical details.  GP Connect does not have this method.  The appt is just booked in a single message exchange. 

Urgent care settings will book patient appts at GP practices where they are not registered for general medical services. 

The meeting between UC and GPC (31-Aug-2017) confirmed that, for now, UC would use the same protocols as GPC.  Appts would be immediately booked and, if the caller decides not to continue, then the appt will be cancelled. 

GP Connect use case can be found at <https://nhsconnect.github.io/gpconnect/appointments_use_case_book_an_appointment.html>

### Acceptance Criteria 
* The request to confirm the appt slot **must** contain all the data to enable the provider to uniquely identify the slot and confirm the appt. 
* The request **must** contain textual details to indicate the reason for the appt. 
* The provider system **must** accept the appt booking even if the patient is not "registered" with this provider. 
* The provider system **must** confirm that the slot has been booked or must return a response to indicate that the booking confirmation has failed. 
