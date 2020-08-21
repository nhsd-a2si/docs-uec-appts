---
title: Delivery Channels
sidebar: overview_sidebar
keywords: specification
permalink: fs_deliverychannel.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}


## Consumer display requirements ##

The fields below allow a patient to choose and attend an appointment appropriate to their needs.

In order to prevent incorrect or unsuitable bookings, and to allow a patient to attend the appointment at the correct time, place or via the correct delivery channel, consumer systems SHALL support the following fields: 

- Start date and time
- End date and time, or duration
- Delivery channel (in-person, telephone, video)
- Slot type and schedule type (see `Slot.serviceType` and `Schedule.serviceCategory`)
- Location name and address
- Practitioner role (e.g. General Medical Practitioner, Nurse)
- Practitioner name and gender
