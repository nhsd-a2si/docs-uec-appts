---
title: Consumer Slot Display Requirements
sidebar: overview_sidebar
keywords: specification
permalink: fs_deliverychannel.html
toc: false
folder: functional_spec
---

There are a number of fields that are supported by the standard when retrieving slots. They can be displayed to allow a patient to choose and attend an appointment appropriate to their needs. It is important to note that some of these fields are not all mandatory and so they might not be returned by the appointment provider system. However, if they are returned the consumer system **MUST** display them to their user in a sensible way. However if the optional fields are not returned the consumer system must also still be able to function.

In order to prevent incorrect or unsuitable bookings, and to allow a patient to attend the appointment at the correct time, place or via the correct delivery channel, consumer systems **SHALL** support the following fields: 

- Start date and time `mandatory`
- End date and time, or duration `mandatory`
- Delivery channel (in-person, telephone, video) `optional`
- Location name and address `optional`
- Practitioner role (e.g. General Medical Practitioner, Nurse) `optional`
- Practitioner name and gender `optional`
