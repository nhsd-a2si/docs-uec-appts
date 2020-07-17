---
title: SMS For Appointments
sidebar: overview_sidebar
keywords: specification
permalink: fs_sms.html
toc: false
folder: functional_spec
---

{% include important.html content="Currently the below guidance is only in draft, it is published here for information only" %}

Research '<link to reference here>' has shown that attendances for appointments are improved when a patient receives an SMS reminder for their appointment. Therefore we offer the following guidance on SMS messaging for appointments made to the UEC Booking Standard:

### Appointment consumers:
*	SHOULD send an SMS confirmation to any patients that have provided mobile numbers and consented during the booking process.
* This MUST be transmitted as soon as the '200OK' response is received from the appointment provider system
* It MUST include as a minimum:
     * Appointment Time
     * Appointment Type (In-Person, Telephone, Video)
     * Appointment Location (if In Person)
     * The name of the provider sending the SMS
     * A note to contact the service (e.g. 111) should their condition worsen or they need to cancel the appointment.

### Appointment Providers:
* SHOULD send an SMS reminder  a reasonable time prior to the appointment
* It MUST include as a minimum:
     * Appointment Time
     * Appointment Location
     * Appointment Type (In-Person, Telephone, Video)
     * The name of the provider sending the SMS
     * A note to contact the service that booked the appointment(e.g. 111) should their condition worsen or they need to cancel the appointment.
