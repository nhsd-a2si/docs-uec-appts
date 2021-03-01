---
title: Slot Display Requirements
sidebar: overview_sidebar
keywords: specification
permalink: fs_deliverychannel.html
toc: false
folder: functional_spec
---

There are a number of fields that are supported by the standard when retrieving slots. They can be displayed to allow a patient to choose and attend a booking appropriate to their needs. 

It is important to note that some of these fields are not all mandatory and so they might not be returned by the booking provider system. However, if they are returned the consumer system **MUST** display them to their user in a sensible way. 

{% include important.html content="However if the optional fields are not returned the consumer system must also still be able to function." %}

In order to prevent incorrect or unsuitable bookings, and to allow a patient to attend the booking at the correct time, place or via the correct delivery channel, consumer systems **SHALL** support the following fields: 

- Start date and time 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">mandatory (Provider)</mark>
- End date and time, or duration 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">mandatory (Provider)</mark>
- Delivery channel (in-person, telephone, video) 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Provider)</mark>
- Health Care Service 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Provider)</mark>
- Providing Organisation 
<br><mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Provider)</mark>
- Location name and address 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Provider)</mark>
- Practitioner role (e.g. General Medical Practitioner, Nurse) 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Provider)</mark>
- Practitioner name and gender 
<br><mark style="background-color: LightGray;font-family: Courier New, Courier, monospace">mandatory (Consumer)</mark> <mark style="background-color: LightBlue;font-family: Courier New, Courier, monospace">Optional (Provider)</mark>

In the case of Delivery Channel, if no delivery channel is specified by the Provider, then the Consumer **must not** default to any specific delivery channel, they must instead not display anything or else in some way indicate the information was not supplied.
