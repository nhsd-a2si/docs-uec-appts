---
title: ABUS.21 Cancel a Booked Appointment for a specific Patient/Service Provider
sidebar: usecase_sidebar
permalink: usee_abus21.html
---

## ABUS.21 Cancel a Booked Appointment for a specific Patient/Service Provider 
**_In order_** that the patient or their carer can cancel an already-booked appointment that they had initially booked at any reasonable time after the appointment has been booked 

**_As a** Integrated Urgent Care Service Provider

**_I want_** to cancel appts booked for a patient 

### Commentary 
It may be that the provider system cannot cancel the appt.  User systems will have to have protocols in place to handle all returned statuses. 

GP Connect use case can be found <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html" target="_blank">here</a>

### Acceptance Criteria  
* The consumer system must be capable of cancelling slots for any provider system, regardless of what relationship the provider organisation has with the consumer organisation (does not apply to GP Connect booking).
* The consumer system must provide visible confirmation to the user of the status returned by the provider system  ie. whether the original appt was successfully cancelled.
* The provider system must not be required to inform the patient of the cancellation of the appt.  Business/clinical responsibility for informing the patient must remain with the consumer organisation.
