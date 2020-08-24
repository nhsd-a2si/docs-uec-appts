---
title: Functional Scope
toc: True
sidebar: overview_sidebar
permalink: scope_functional.html
summary: "This page defines the currently envisaged limit of functional scope for the direct booking standards"
---

## What is a UEC Appointment?
* UEC Appointments are specific time-based slots 
* Urgency tends to be denoted by the 'disposition' which represents a timeframe within which the patient needs to be seen (e.g. within 6 hours) - this is basically a short-term representation of clinical urgency but it differs from planned care in as much as it works on the basis that the 'clock is ticking from the moment the patient first calls'. 
* Appointments can be offered which are delivered by different roles

## Slot Management 
* All existing models within urgent care use real-time slot queries to get availability of appointments. At the busiest periods even this can result in appointments becoming unavailable between the initial search and confirming it with the patient - this is not unlike the high-demand ticket-booking scenario. Demand on services can fluctuate rapidly.
* Ultimately the services providing the slots have ownership over what they do and don't make available
* Services will sometimes make slots available for certain types of patient and have to manage their slot allocation carefully so as to avoid using all slots within the first hour of opening 
  
## User Privileges 
For UEC booking not using GP Connect:
* Appointment booking privileges should not need to be restricted at user level. 
* API authentication is done at system level. 

## Slot mapping/semantics
* In urgent & emergency care, slots do not usually have a named clinician.

## Appointment Management 
* Proprietary solutions currently provide the ability to Book an appointment with limited capability to Cancel or Reschedule that appointment from within the actual booking workflow. None of the existing proprietary solutions support cancellations / rescheduling after the call has ended.
A national solution should support the full range of workflow actions expected from an appointment booking system.

## Patient Access to the booking system(s)
* This standard supports direct access to the booking capability by patients

## Monitoring, Analytics and Reporting 
* Provider systems SHALL audit all API access and actions.
* It is expected that this will be handled locally by each system. 
* There must be a capability to report against expected national metrics for appointment booking 
* the must be a clear mechanism to share these data with commissioners and other key stakeholders
