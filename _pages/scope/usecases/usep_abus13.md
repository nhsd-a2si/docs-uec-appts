---
title: ABUS.13 Warn Users Where Appts are Outside Disposition Timeframe 
sidebar: usecase_sidebar
permalink: usep_abus13.html
---

## ABUS.13 Booking outside a disposition timeframe

**_In order_** that bookings are not made outside a disposition timeframe 

**_As a_** Integrated Urgent Care Service Provider

**_I want_** to be notified when selecting an appointment booking timeslot when it is over the disposition timeframe 

### Commentary

Notifications are only applicable to non-clinical users and any booking outside a dispositions should be logged and auditable. 

A notification and prompt to seek clinical approval to book outside the disposition timeframe will be needed for dispositions up to 6 hours:
* Dx05 To contact a Primary Care Service within 2 hours
* Dx06 To contact a Primary Care Service within 6 hours
* Dx11 Speak to a Primary Care Service within 1 Hour
* Dx12 Speak to a Primary Care Service within 2 Hours
* Dx13 Speak to a Primary Care Service within 6 Hours

Users will be need to be notified when booking outside the disposition timeframe for dispositions from 6 hours to 12 hours:
* Dx07 To contact a Primary Care Service within 12 hours
* Dx08 To contact a Primary Care Service within 24 hours
* Dx14 Speak to a Primary Care Service within 12 Hours
* Dx15 Speak to a Primary Care Service within 24 Hours

### Acceptance Criteria
*	The system must allow clinical users to book outside the disposition timeframes 
*	The system must notify non-clinical users that they are booking outside a disposition timeframe and they need to seek clinical approval for Dx05
*	The system must notify non-clinical users that they are booking outside a disposition timeframe and they need to seek clinical approval for Dx06
*	The system must notify non-clinical users that they are booking outside a disposition timeframe and they need to seek clinical approval for Dx11
*	The system must notify non-clinical users that they are booking outside a disposition timeframe and they need to seek clinical approval for Dx12
*	The system must notify non-clinical users that they are booking outside a disposition timeframe and they need to seek clinical approval for Dx13
*	The system must notify non-clinical users that they are booking outside a disposition timeframe for Dx07
*	The system must notify non-clinical users that they are booking outside a disposition timeframe for Dx08
*	The system must notify non-clinical users that they are booking outside a disposition timeframe for Dx14
*	The system must notify non-clinical users that they are booking outside a disposition timeframe for Dx15
*	The system must allow you to produce a report to show where a patient has been booked outside their disposition timeframe
