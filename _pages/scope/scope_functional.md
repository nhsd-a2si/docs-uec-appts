---
title: Functional Scope
toc: True
sidebar: overview_sidebar
permalink: scope_functional.html
summary: "This page defines the currently envisaged limit of functional scope for this standard"
---

## What is a Booking?
* Bookings are where a patient is allocated to a specific time-based unit of resource at a healthcare service
  * Traditionally this would be a time where the patient would expect to be starting a face to face consultation with a clinician
  * However there are many other uses for bookings:
      * it could just be a "turn-up" time to "check-in" to the service (as in "ED Bookings")
      * the booking could be for a telephone or video assessment
      * the patient would normally be notified of the booking but this need not be the case, the bookings might be "silent" and used just to manage capacity etc..
* Urgency tends to be determined by the outcome of the initial assessment which represents a timeframe within which the patient needs to be seen after an onward referral (e.g. within 6 hours) - this is basically a short-term representation of clinical urgency but it differs from planned care in as much as it works on the basis that the 'clock is ticking from the moment the patient first calls'. 
* Bookings can be offered which are delivered by different roles

## Slot Management 
* Some existing models, such as within urgent care, use real-time slot queries to get availability of bookings. At the busiest periods even this can result in bookings becoming unavailable between the initial search and confirming it with the patient - this is not unlike the high-demand ticket-booking scenario. Demand on services can fluctuate rapidly.
* Ultimately the services providing the slots have ownership over what they do and don't make available
* Services will sometimes make slots available for certain types of patient and have to manage their slot allocation carefully so as to avoid using all slots within the first hour of opening 
  
## User Privileges 
* Currently, appointment booking privileges should not need to be restricted at user level, this may change in the future with new capabilities. 
* API authentication is done at system level. 

## Slot mapping/semantics
* In some care settings, (e.g. urgent & emergency care), slots do not usually have a named clinician, therefore flexibility in mappings needs to be maintained.

## Booking Management 
* Proprietary solutions currently provide the ability to make a booking with limited capability to Cancel or Reschedule that booking from within the actual booking workflow. None of the existing proprietary solutions support cancellations/rescheduling after the call has ended.
* A national standardised solution should support the full range of workflow actions expected from a booking system.

## Patient Access to the booking system(s)
* This standard supports direct access to the booking capability by patients

## Monitoring, Analytics and Reporting 
* Provider systems SHALL audit all API access and actions.
* It is expected that this will be handled locally by each system. 
* There must be a capability to report against expected national metrics for booking 
* the must be a clear mechanism to share these data with commissioners and other key stakeholders
