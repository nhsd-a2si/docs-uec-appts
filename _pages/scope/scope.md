---
title: Scope
toc: True
sidebar: overview_sidebar
permalink: scope.html
summary: "This page defines the currently envisaged limit of scope for the direct booking standards"
---

## Appointment Types 
* Appointments are specific time-based slots, 1 patient per slot. 
* Urgency tends to be denoted by the 'disposition' which represents a timeframe within which the patient needs to be seen (e.g. within 6 hours) - this is basically a short-term representation of clinical urgency but it differs from planned care in as much as it works on the basis that the 'clock is ticking from the moment the patient first calls'. 
* There will be some variety in the types of appointment patients needs e.g. with a GP, with a nurse practitioner, they might need a prescribing clinician, they might need an emergency dentist. There is a mixed model of how this is provided: some providers will supply several types of appointment, whereas other specialist providers might only supply one type (e.g. an emergency dental provider might only supply one type of appointment). 

## Slot Management 
* Publishing, synchronization, ownership 
* All existing models within urgent care use real-time slot queries to get availability of appointments. At the busiest periods even this can result in appointments becoming unavailable between the initial search and confirming it with the patient - this is not unlike the high-demand ticket-booking scenario. Demand on services can fluctuate rapidly, and services maintain the ultimate control over the appointments they are making available; it is not unheard of for a service to remove some availability when they see an influx of patients to prevent running over-capacity.  
* Ultimately the services providing the slots have ownership over what they do and don't make available - there are some political complications if the service providers are contracted to provide a certain number of appointments for instance, but this is a separate detail. 
* Services will sometimes make slots available for certain types of patient and have to manage their slot allocation carefully so as to avoid using all slots within the first hour of opening - they have an obligation to continue to provide a service during the out of hours period and so they have to apply demand predictions and spread their slot availability out. This can be done by restricting certain slots for patients with certain clinical urgency, and spreading these through the schedule (e.g. reserve a % of slots every hour that can only be booked into for patients with a urgency of < 1 hour). Another method of controlling demand is to use the disposition timeframe to filter the time range for appointments e.g. if a patient needs to be seen within 6 hours, don't show slots sooner than 2 hours away. Obviously, some serious thought has to be put into how this is all filtered and as to how they make sure they are providing an acceptable service for patients. 

## User Privileges 
* Patients do not have any access to their own appointment information currently, and certainly aren't allowed to book appointments directly without first being triaged by a professional of some kind. 
* Appointment booking privileges are not really restricted at user level, it is more about inter-organisational agreements i.e. can X NHS 111 service book appointments into Y OOH GP service. Generally is someone is able to deal with a patient on the phone, they will be able to take the patient through the full journey including booking them an appointment at another service. None of the proprietary solutions pass user-level details between them via APIs - API auth is all done at system level. 

## Slot mapping/semantics 
* Varies depending on the scheduling models that systems implement, and to a certain extent we don't really care. Ultimately, though, slots are made available by services, and may be restricted by the type of care provided and restricted by certain patient criteria i.e. only patients who have received a certain disposition can book this slot. 
* There is not much precedence of slots being named clinician level as there is very little consistency of clinicians in urgent & emergency care, and the encounters by definition are not part of an ongoing relationship.  

## Appointment Management 
* Proprietary solutions currently provide Book and limited Cancel / Reschedule. Cancel / Reschedule is limited because this can only really be done during the initial call with the patient i.e. if the patient changes their mind before the call ends. 
* None of the existing proprietary solutions support cancellations / rescheduling after the call has ended, and a big workflow challenge for urgent care is identifying that an appointment has previously been booked for a patient if they are to call back to NHS 111 some period after they originally called. This is a part of the workflow that needs tackling as part of a national solution. 
* A national solution should support the full range of workflow actions expected from an appointment booking system. 

## Access to the booking system(s) 
* No direct access to the booking capability by the patient is currently envisaged.  
* Access will be via API integrations only 

## Monitoring, Analytics and Reporting 
* It is expected that this will be handled locally by each system. However there should be a capability to report against expected national metrics for appointment booking and a clear mechanism to share these data with commissioners and other key stakeholders 
