---
title: ABUS.01 Display Possible Provider Services
sidebar: overview_sidebar
permalink: usep_abus01.html
---

## ABUS.01 Display Possible Provider Services
**_In order_** that the patient can choose their most convenient provider or the provider that they think most closely serves their need

**_As a_** 111 Call Handler or urgent care service provider

**_I want_** to view the all the provider services that could currently assist the patient with a certain clinical need.

### Commentary
Whilst not strictly concerning the new messaging/API for appt booking, searching DoS (directory of services) for a provider is a key precursor to appt booking.

### Acceptance Criteria
* Suitable service **must** be displayed in a list
* The list **must** include all possible providers that can support a patient with the current clinical need, regardless of the location/organisation of the call handler making the request.
* The list **must** be sorted so that the most appropriate provider is sorted to the top of the list. Appropriateness of the provider is defined by the distance from the patient's current location.
* The list **must** provide the location details of the provider (so that the patient can help to assess which provider really has the most convenient location)
* Possible data items to display:
    * Name of provider
    * Address of provider where the care will be offered (not the business address of the provider organisation)
    * Distance from patient
