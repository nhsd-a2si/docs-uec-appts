---
title: ABUS.22 Rebook an Appointment for a specific Patient/Service Provider 
sidebar: usecase_sidebar
permalink: usee_abus22.html
---

## ABUS.22 Rebook an Appointment for a specific Patient/Service Provider 
**_In order_** that the patient or their carer can rebook an already-booked appointment that they had initially booked 

**_As a** Integrated Urgent Care Sservice Provider

**_I want_** to rebook appts booked for a patient 

### Commentary 
The capability to cancel an appointment gives the ultimate capability of also amending an appt as an amendment is effectively a cancel followed by a re-book (following a reassessment).  

GP Connect use case can be found <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html" target="_blank">here</a>

### Acceptance Criteria  
* The consumer system **must** be capable of cancelling slots for any provider system, regardless of what relationship the provider organisation has with the consumer organisation (does not apply to GP Connect booking).
* The consumer system **must** provide visible confirmation to the user of the status returned by the provider system  ie. whether the requested appt was successfully cancelled or not.  Example returned statuses could be: 
   * Appt successfully cancelled 
   * Not cancelled - system failure 
   * Not cancelled - appt requested was not found 
   * Not cancelled - appt was not for this patient 
   * Not cancelled - appt was already in the past 
   * Not cancelled - appt was already cancelled 
* The provider system *must not* be required to inform the patient of the cancellation of the appt.  Business/clinical responsibility for informing the patient must remain with the consumer organisation. 
