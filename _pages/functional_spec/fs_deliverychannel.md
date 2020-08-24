---
title: Slot Display Requirements
sidebar: overview_sidebar
keywords: specification
permalink: fs_deliverychannel.html
toc: false
folder: functional_spec
---

There are a number of fields that are supported by the standard when retrieving slots. They can be displayed to allow a patient to choose and attend an appointment appropriate to their needs. It is important to note that some of these fields are not all mandatory and so they might not be returned by the appointment provider system. However, if they are returned the consumer system **MUST** display them to their user in a sensible way. However if the optional fields are not returned the consumer system must also still be able to function.

In order to prevent incorrect or unsuitable bookings, and to allow a patient to attend the appointment at the correct time, place or via the correct delivery channel, consumer systems **SHALL** support the following fields: 

- Start date and time <mark style="background-color: grey;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> `mandatory (Provider)`
- End date and time, or duration `mandatory (Consumer)` `mandatory (Provider)`
- Delivery channel (in-person, telephone, video) `mandatory (Consumer)` `optional (Provider)`
- Location name and address `mandatory (Consumer)` `optional (Provider)`
- Practitioner role (e.g. General Medical Practitioner, Nurse) `mandatory (Consumer)` `optional (Provider)`
- Practitioner name and gender `mandatory (Consumer)` `optional (Provider)`
