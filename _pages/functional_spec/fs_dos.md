---
title: Interactions with the DoS
sidebar: overview_sidebar
keywords: specification
permalink: fs_dos.html
toc: false
folder: functional_spec
---

{% include note-notpublished.html %}

## Introduction

The NHS Digital A2SI Directory of Services (known as the "DoS") is the primary service discovery and information tool available to the NHS. Although this standard does support booking workflows that do not need to use the DoS it is envisaged that it will provide the service discovery element in the majority of booking workflows that use this standard.

Therefore it is important to understand how the DoS will interact with booking workflows. At a very high level there are four key elements that take place, in sequence, during the booking process. These are:

* Service discovery
* End point discovery
* Slot discovery
* Booking

Understanding how these steps interact with each other is essential, especially when booking into more complex services. For exmaple the way the profiling of the DoS service is tied to a provider systems schedules. In order to understand these interactions better lets walk through an example.

## Example workflow


