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

The <a href="https://digital.nhs.uk/services/directory-of-services-dos" target="_blank">Urgent Care Directory of Services (known as the "DoS")</a> is the primary service discovery and information tool available to the NHS. Although this standard does support booking workflows that do not need to use the DoS it is envisaged that it will provide the service discovery element in the majority of booking workflows that use this standard.

Therefore it is important to understand how the DoS will interact with these booking workflows. At a very high level there are four key elements in the booking sequence. These are:

* Service discovery
* End point discovery
* Slot discovery
* Booking a slot

Understanding how these steps interact with each other is essential, especially when booking into more complex services. For exmaple the way the profiling of the DoS service is tied to the schedules on a provider system. In order to understand these interactions better lets walk through an example.

## Example workflow

Services on the DoS are profiled with a rage of data that is used to determine the ranking for services that are returned for a specific search. There is also additional data items that are used for other purposes, for example interoperability. Examples of these data items are as follows:

* Geographical information such as address and search etc..
* Demographic profile of patients the service is available to
* The comissioning footprint of the service, for example 
  * GP Practices that patients have to be registered to in order to use the service
* The clinical needs that the servie will meet, for exampled
  * symptoms
  * timeframes
* Referal endpoint information for example:
  * URL's
  * Document format

Service Type | DoS ID | Service Name             | Service ODS Code 
-------------|--------|--------------------------|------------------
GP Federation|123456  | GP Hub - Main location   | AB1234            
GP Federation|123457  | GP Hub - the High Street | 123457            



Provider Name      | Provider ODS Code | HealthcareServiceID (SDS)
|--------------------|-------------------|--------------------------
GP Federations Ltd.| AB1234            | 87654321
GP Federations Ltd.| AB1234            | 97654322




