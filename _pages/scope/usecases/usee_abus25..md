---
title: ABUS.25 - Booking only services
sidebar: overview_sidebar
permalink: usee_abus25.html
---

## ABUS.25 xxxx
**_In order_** that a service profiled on the DoS only accepts referrals when a booking is also made

**_As a_** 111 Call Handler or urgent care service provider

**_I want_** to have the option to refer via the DoS removed if I have not also booked an appointment

### Commentary
The Directory of services is being enhanced to have service parameters that can be set against services. One of these parameters will be "booking required". 

### Acceptance Criteria
* "booking required" flag **must** be available and set in the DoS
* 111 system **must** check the "booking required" flag on DoS services prior to displaying results to user
* If the service is marked as "booking required" then the referral options for this service must be unavailable until a booking has been made.
