---
title: User Stories
sidebar: overview_sidebar
permalink: user_stories.html
---

## ABUS.01 Display Possible Provider Services

*In order* that the patient can choose their most convenient provider or the provider that they think most closely serves their need
*As a* 111 Call Handler or urgent care service provider
*I want* to view the all the provider services that could currently assist the patient with a certain disposition.

### Commentary
Whilst not strictly concerning the new messaging/API for appt booking, searching DoS (directory of services) for a provider is a key precursor to appt booking.

### Acceptance Criteria
* The list must include all possible providers that can support a patient with the current disposition, regardless of the location/organisation of the call handler making the request.
* The list must be sorted so that the most appropriate provider is sorted to the top of the list. Appropriateness of the provider is defined by the distance from the patient's current location.
* The list must provide the location details of the provider (so that the patient can help to assess which provider really has the most convenient location)
* Possible data items to display:
    * Name of provider
    * Address of provider where the care will be offered (not the business address of the provider organisation)
    * Distance from patient

<br>

## ABUS.02 Display Appt Availability Status of Providers
*In order* that the patient can quickly be informed of what services have free appts and the call can be completed more quickly
*As a* 111 Call Handler or urgent care service provider
*I want* to view the appt availability of all the provider services that could currently assist the patient with a certain disposition when, or shortly after, that list is returned from the DoS.

### Commentary

Suppliers of consumer systems may wish to consider whether they wish to immediately access the provider systems listed to, for example, return a simple count of the number of appts that are available at the provider during the disposition timeframe.  Suppliers may wish to return and display the DoS data and then follow-up with the counts of free appts as the API calls are successfully made and returned.

The user interface could also show all the ‘next available appointment within time frame’ displayed for each individual location. so they don’t have to hunt through various diaries to find a slot.

During conversation with the patient, it is possible that the situation will change.  Suppliers of consumer software may wish to consider whether they can offer a manual or automatic refresh facility for this list.

Suppliers (and users) should be mindful that some scenarios for returning appointments may return more 'possible' appointments than the user may actually wish to choose from.  For example, an occasion where a GP practice returns all available appointments for the practice, but in reality the user is only interested in those appointments for a specific branch surgery.

### Acceptance Criteria

* The list **may** include details of free appts available at this DoS location, such as the count of free appts available at each location, within the current disposition timeframe.
* The list **may** include the earliest appt time available at each location, within the current disposition timeframe.
* This list **may** be capable of being quickly refreshed by the user or automatically as a timed event.
