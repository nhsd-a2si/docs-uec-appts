---
title: ABUS.20 Display any Booked Appointments for a specific Patient/Service Provider 
sidebar: overview_sidebar
permalink: usee_abus20.html
---

## ABUS.20 Display any Booked Appointments for a specific Patient/Service Provider 
**_In order_** that the patient can confirm what appts are already booked for them at a provider or an urgent care clinician can check the attendance status of a patient's appt 

**_As a_** 111 Call Handler or urgent care service provider 

**_I want_** to retrieve the details of appts booked for a patient with a specific service provider. 

### Commentary 
Patients (or their representatives) may contact an urgent care provider (such as 111) to confirm details of an appt that has already been made.  This may be just to be reminded of the details or so that they can amend/delete that appt.  Regardless of the reason, the urgent care service provider taking the call will have a requirement to make a request to another provider to retrieve the details of this appt.  

111 systems are not nationally integrated and therefore if a caller comes into a 111 service different from the one where the appt was raised, the new 111 will not have access to the original call history or appt details.  

It may be that the patient has already missed the booked appt.  Therefore, the acceptance criteria includes a requirement for the request to cover a time window that is defined by the requesting system. 

Additionally, urgent care clinicians may wish to query provider systems to confirm that the patient has attended their appt.  If they have failed to attend, there are occasions when the clinician will call back to check on the patient. 

GP Connect use case can be found <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_retrieve_a_patients_appointments.html" target="_blank">here</a>

### Acceptance Criteria  
* The consumer system **must** be capable of querying any provider system, regardless of what relationship the provider organisation has with the consumer organisation. 
* The patient's appts **must** be capable of being retrieved by a consumer system from any provider system where there are data sharing agreements loaded on the Spine, to be accessed by the Spine Security Proxy (SSP). 
* The request **must** have a date/time window specified by the consumer system.  It is expected that the window will be based on the conversation with the patient and may include a start date/time that is in the past.  It will be for the developers and users of the consumer system to define what ranges will be appropriate for each occasion. 
* The provider system **must** return a list of appts booked for this patient (within the time window provided) or must return a response to indicate that there are no matching appts. 
* The list of appts returned **must** include the appt status and a unique reference for the appt. 

### Notes 
For example, a restricted list from the FHIR base valueset for AppointmentStatus could meet the needs for Urgent Care: 

<a href="http://hl7.org/fhir/valueset-appointmentstatus.html">http://hl7.org/fhir/valueset-appointmentstatus.html</a> 

|    Code   |  Display  | Definition |
|:---------:|:---------:|------------|
|  pending  | Pending   |Some or all of the participant(s) have not finalized their acceptance of the appointment request. |
|   booked  |  Booked   | All participant(s) have been considered and the appointment is confirmed to go ahead at the date/times specified.  |
|  arrived  |  Arrived  | Some of the patients have arrived. |
| fulfilled | Fulfilled | This appointment has completed and may have resulted in an encounter. |
| cancelled | Cancelled | The appointment has been cancelled. |
|   noshow  |  No Show  | Some or all of the participant(s) have not/did not appear for the appointment (usually the patient). |

<br> 
