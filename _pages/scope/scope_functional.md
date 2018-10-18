---
title: Functional Scope
toc: True
sidebar: overview_sidebar
permalink: scope_functional.html
summary: "This page defines the currently envisaged limit of functional scope for the direct booking standards"
---
{% include note-notpublished.html %}

## Appointment Types 
* Appointments are specific time-based slots 
* Urgency tends to be denoted by the 'disposition' which represents a timeframe within which the patient needs to be seen (e.g. within 6 hours) - this is basically a short-term representation of clinical urgency but it differs from planned care in as much as it works on the basis that the 'clock is ticking from the moment the patient first calls'. 
* Appointments can be offered which are delivered by different roles

## Slot Management 
* All existing models within urgent care use real-time slot queries to get availability of appointments. At the busiest periods even this can result in appointments becoming unavailable between the initial search and confirming it with the patient - this is not unlike the high-demand ticket-booking scenario. Demand on services can fluctuate rapidly.
* Ultimately the services providing the slots have ownership over what they do and don't make available
* Services will sometimes make slots available for certain types of patient and have to manage their slot allocation carefully so as to avoid using all slots within the first hour of opening 
  * This can be done by restricting certain slots for patients with certain clinical urgency, and spreading these through the schedule (e.g. reserve a % of slots every hour that can only be booked into for patients with a urgency of < 1 hour). 
  * Another method of controlling demand is to use the disposition timeframe to filter the time range for appointments e.g. if a patient needs to be seen within 6 hours, don't show slots sooner than 2 hours away. 

## User Privileges 
* Appointment booking privileges should not need to be restricted at user level, it is more about inter-organisational agreements i.e. can X NHS 111 service book appointments into Y OOH GP service. 
* API auth is done at system level. 

## Slot mapping/semantics 
* Varies depending on the scheduling models that systems implement, and to a certain extent we don't really care. Ultimately, though, slots are made available by services, and may be restricted by the type of care provided and restricted by certain patient criteria i.e. only patients who have received a certain disposition can book this slot. 
* There is not much precedence of slots being named clinician level as there is very little consistency of clinicians in urgent & emergency care, and the encounters by definition are not part of an ongoing relationship.  

## Appointment Management 
* Proprietary solutions currently provide the ability to Book an appointment with limited capability to Cancel or Reschedule that appointment from within the actual booking workflow. None of the existing proprietary solutions support cancellations / rescheduling after the call has ended.
A national solution should support the full range of workflow actions expected from an appointment booking system.

## Access to the booking system(s) 
* No direct access to the booking capability by the patient is currently envisaged.  
* Access will be via API integrations only 

## Monitoring, Analytics and Reporting 
* It is expected that this will be handled locally by each system. 
* There must be a capability to report against expected national metrics for appointment booking 
* the must be a clear mechanism to share these data with commissioners and other key stakeholders
