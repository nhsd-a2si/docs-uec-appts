---
title: ABUS.24 Stopping referrals for booking only services
sidebar: overview_sidebar
permalink: usep_abus24.html
---

## ABUS.24 Stopping referrals for booking only services
**_In order_** that referrals a not made to services that operate a booking only model when an appointment has not been booked

**_As a_** Integrated Urgent Care Sservice Provider

**_I want_** to be notified when selecting a service that only accepts referrals when a booking has been made

### Commentary 
For booking only DoS services a service attribute will need to be added by the local DoS lead. The service attribute is called "**requirebooking**"

### Acceptance Criteria 
* The system **must** stop the users from making a referral if no appointment has been made when the "**requirebooking**" service attribute is present on the DoS service
* The system **must** present an appropriate warning message to the user
* The system **must** allow the user to select a different service on the DoS
* The system **must** allow a referral to be sent when a booking is made
