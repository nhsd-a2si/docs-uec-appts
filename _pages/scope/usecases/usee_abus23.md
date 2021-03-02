---
title: ABUS.23 Cancel a Booked Appointment for a specific Patient/Service Provider by any IUC Provider
sidebar: overview_sidebar
permalink: usee_abus23.html
---

## ABUS.23 Cancel a Booked Appointment for a specific Patient/Service Provider by any IUC Provider
**_In order_** that the patient or their carer can cancel or rearrange an already-booked appointment at a specific provider 

**_As a**  Integrated Urgent Care Sservice Provider

**_I want_** to cancel appts booked for a patient with a specific service provider that is not themselves 

### Commentary 

As urgent care providers can receive calls for different regions they must have the ability to cancel appts that they did not actually raise.   

It may be that the provider system cannot cancel the appt.  User systems will have to have protocols in place to handle all returned statuses. 

GP Connect use case can be found <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_cancel_an_appointment.html" target="_blank">here</a>

### Acceptance Criteria  
* The consumer system **must** be capable of cancelling slots for any provider system, regardless of what relationship the provider organisation has with the consumer organisation (does not apply to GP Connect booking).
* The consumer system **must** provide visible confirmation to the user of the status returned by the provider system  ie. whether the original appt was successfully cancelled.
* The provider system **must** not be required to inform the patient of the cancellation of the appt.  Business/clinical responsibility for informing the patient **must** remain with the consumer organisation.
