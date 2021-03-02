---
title: Interactions with the DoS
sidebar: overview_sidebar
keywords: specification
permalink: dos_overview.html
toc: false
folder: dos
---

The <a href="https://digital.nhs.uk/services/directory-of-services-dos" target="_blank">Urgent Care Directory of Services (known as the "DoS")</a> is the primary service discovery and information tool available to the NHS. Although this standard does support booking workflows that do not need to use the DoS it is envisaged that it will provide the service discovery element in the majority of booking workflows that use this standard.

Therefore it is important to understand how the DoS will interact with these booking workflows. At a very high level there are four key elements in the booking sequence. These are:

* Service discovery
* End point discovery
* Slot discovery
* Booking a slot

Understanding how these steps interact with each other is essential, especially when booking into more complex services. For example the way the profiling of the DoS service is tied to the schedules on a provider system. In order to understand these interactions better we shall walk through an example.
