---
title: Appointment Management - workflow
sidebar: cr_sidebar
keywords: specification
permalink: cr_workflow.html
toc: false
folder: functional_spec
---

With the UEC Booking Standard there is no specific Rebook functionality. The reason for this is that any need for a change to an appointment should require a re-assessment and be considered as a new encounter. Only once this assessment has been completed (including any new bookings associated with that encounter) would the consumer system then cancel any appointments that they are aware of that would no longer be appropriate. It is worth noting that depending on the capabilities of the system being used to make the reassessment the original appointment may not be cancelled.


There are a number of workflows where the cancel/rebook capability can be demonstrated.

Below is a typical scenario that would require what could be described operationally as "re-booking":

* On a Friday afternoon, Mr. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and an appointment is made at an appropriate service, near their home, in 6 hours time. 
* an appointment is booked at their local Urgent Treatment Centre
* An hour later he feels much worse so calls 111 back. 
* Mr. Patient is reassessed and a new assessment outcome is reached. An urgent appointment is required within 2 hours so the booking process is entered. 
* The appointment booking process is completed and the consumer system sends a booking confirmation for the new booking to the provider service.
* The list of existing relevent appointments is displayed to the 111 user (in this case there is just one appointment)
* The user confirms with Mr. Patient the correct appointment that was previously booked and that this appointment will be cancelled and a new appointment booked.
* In the background the 111 system then cancels the previous appointment (confirmed above).

Now consider a slightly different, less common but still likely scenario where the orignal appointment is never cancelled:

* On a Friday afternoon, Whilst at work, Mrs. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and an appointment is made at an appropriate service, near their home, in 12 hours time. 
* When the appointment is confirmed by the providing system, it creates a record on the Appointment Registry for that patient.
* An hour later Mrs. Patient goes home.
* When she arrives home she feels much worse so calls 111 back. 
* Now she is at home, she reaches a different 111 service from the one she called whilst at work
* Mrs. Patient is reassessed and a new assessment outcome is reached. An urgent appointment is required at the same Urgent Treatment Centre, but within 2 hours so the booking process is entered. 
* The appointment booking process is completed at the UTC service and the provider system sends a booking confirmation for the new booking to the provider service.
* The original appointment still exists on the system as the 111 service making the more urgent booking has no knowledge of the prior booking and would have to be dealt with locally when then patient arrives for the new more urgent appointment.

{% include warning.html content="The information below is currently out of scope and will form part of a future enhancement. It is included here for interest only" %}

The following example is the same as the above but demonstrates the benefit of using a registry:

* On a Friday afternoon, Whilst at work, Mrs. Patient feels ill so calls a 111 service. 
* It is determined during this assessment that they require a face to face consultation and an appointment is made at an appropriate service, near their home, in 12 hours time. 
* When the appointment is confirmed by the providing system, it creates a record on the Appointment Registry for that patient.
* An hour later Mrs. Patient goes home.
* When she arrives home she feels much worse so calls 111 back. 
* Now she is at home, she reaches a different 111 service from the one she called whilst at work
* Whilst they are confirming her demographics, the system they use is checking the appointment registry for any existing relevent appointments. It finds one (from earlier) and sets a flag against the record in the system and the 111 user is notified.
* Mrs. Patient is reassessed and a new assessment outcome is reached. An urgent appointment is required within 2 hours so the booking process is entered. 
* The list of existing relevent appointments is displayed to the 111 user (in this case there is just one appointment)
* The user confirms with Mrs. Patient the correct appointment that was previously booked and that this appointment will be cancelled and a new appointment booked.
* The appointment booking process is completed at the new service and the provider system sends a booking confirmation for the new booking to the new provider service.
* In the background the 111 system then cancels the previous appointment (confirmed above).
* The original provider service expires the original booking entry on the Appointment Registry

The above workflow is illustrated in the sequence diagram below:

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile modified=\&quot;2019-03-26T13:20:47.363Z\&quot; host=\&quot;www.draw.io\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; etag=\&quot;KkR4IQ09NnnigqSwLL14\&quot; version=\&quot;10.5.7\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;IvEeq4OhAhwKIa1ZwIv2\&quot; name=\&quot;Page-1\&quot;&gt;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&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

There are some key requirements that the providing and consuming systems need to do to support this capability:

### Providing system:

* Whenever an appointment confirmation is sent at the end of a successful booking process, the system will need to update the Appointment Registry with a new record for the appointment just made
* Whenever a cancellation of an appointment is successfully completed, the system needs to update the Appointment Registry for that appointment to update the record to cancelled.

### Consuming system:

* At the end of any re-assessment, the option to cancel the original appointment needs to be offered
