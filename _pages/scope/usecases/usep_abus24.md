---
title: ABUS.24 Stopping referrals for booking only services
sidebar: usecase_sidebar
permalink: usep_abus24.html
---

## ABUS.24 Stopping referrals for booking only services
**_In order_** that the patient can be assured that the provider will see them on or around the allotted time at the selected location 

**_As a_** Integrated Urgent Care Sservice Provider

**_I want_** to confirm/book an offered appointment slot with the provider. 

### Commentary 
For UEC booking, appointments will be immediately booked with the following steps:
*	Send an Appointment requesting that it be booked into one of the available Slots.
*	Receive confirmation (including an identifier) that the Appointment has been booked.
OR
*	Receive an error describing why the Appointment couldn’t be booked.

GP Connect use case can be found at <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_book_an_appointment.html" target="_blank">GP Connect book and appointment use case</a>

### Acceptance Criteria 
* The provider system **must** accept the appointment booking even if the patient is not "registered" with this provider
* Where the booking was not successful, the provider **must** send an appropriate response to indicate this.
* Where the booking was not successful, the consumer **must** present an appropriate message to the user to indicate this.
