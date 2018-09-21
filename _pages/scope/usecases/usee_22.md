---
title: ABUS.22 Amend a Booked Appointment Reason for a specific Patient/Service Provider 
sidebar: usecase_sidebar
permalink: usee_abus22.html
---
{% include note-notpublished.html %}

## ABUS.22 Amend a Booked Appointment Reason for a specific Patient/Service Provider 
**_In order_** that the service provider has the correct reason for the appt displayed on their system 

**_As a_** 111 Call Handler or urgent care service provider 

**_I want_** to amend the appt reason for a previously booked appt, where the reason has changed or was erroneously provided to the service provider. 

### Commentary 
GP Connect offers the message set to enable the reason for the appt to be amended.  For the use case go to <https://nhsconnect.github.io/gpconnect/appointments_use_case_amend_an_appointment.html>

### Acceptance Criteria  
* The consumer system *must* be capable of amending slots for any provider system, regardless of what relationship the provider organisation has with the consumer organisation 
* The patient's appts *must* be capable of being amended by a consumer system at any provider system where there are data sharing agreements loaded on the Spine, to be accessed by the Spine Security Proxy (SSP). 
* The user's system *must* provide visible confirmation to the user of the status returned by the provider system  ie. whether the requested appt reason was successfully amended or not.  Example returned statuses could be: 
   * Appt successfully amended 
   * Not amended - system failure 
   * Not amended - appt requested was not found 
   * Not amended - appt was not for this patient 
   * Not amended - appt was already in the past 
