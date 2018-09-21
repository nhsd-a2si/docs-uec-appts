---
title: ABUS.13 Warn Users Where Appts are Outside Disposition Timeframe 
sidebar: usecase_sidebar
permalink: usep_abus13.html
---
{% include note-notpublished.html %}

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
