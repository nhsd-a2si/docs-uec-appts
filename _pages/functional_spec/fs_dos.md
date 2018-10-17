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

The aspect of this that is key for direct booking is how a specific service will relate to a CareConect Schedule resource on a particular system.

For this example, consider a GP Federataion provider called "GP Federations Ltd.". This provider has been comissioned by the GP Practices in a comissioning area to deliver the extended access GP services on behalf of these GP Practices. GP Federations Ltd. operates this service from three different locations, these are consulting rooms in three of the GP Practices they are covering.

GP Federation Ltd. deliver their services from a single IT Platform, known as "Another GP Clinical System (AGPCS)". Each of the three locations has its own appointment diary represented as a schedule in AGPCS. 

Location 3 has two diaries, a GP diary like the other two and a Nurse diary too:

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; version=\&quot;9.2.7\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;a9224995-d5d3-854d-5d66-375058506576\&quot; name=\&quot;Page-1\&quot;&gt;7VdRb5swEP41PCYCm7DwmKRNNymTKqXSnl1wwJqxmXEW6K/fGewElDSttmTdpPAA9ne2z3fffSfh4UVRPyhS5l9lSrmH/LT28J2HUBCjCXwM0jjEt0imWGqxA7BmL9SCvkW3LKXVYKGWkmtWDsFECkETPcCIUnI3XLaRfOi1JBk9AtYJ4cfoN5bqvEMx9v2D4TNlWW5dgynuLM8k+Z4puRXWoYfwpn06c0HcYfakKiep3PUgfO/hhZJSd6OiXlBusuvy1u1bvmLdX1xRod+zAXcbfhK+tbGvZEI0kwJQe1qlG5eYascKTgTM5hsptGUumMLcHkSVpvWrlwn2IULxUFlQrRpY4jaENou2bpDL9+5AAootlg/yb0Fiic/2Zx9ih4EN/3Qq0FEqjsPPSWmGrGgLaJ7rgpv4YWgCZ1BBM84yAZiWZQ9dkWfKH2XF2sziu2eptSxgATeG+b5oFpJL1fpyZYPnrbNZVXaF7gNC3GTDapq6JTDPtTYKmZmY0TJJBRoz0MiGiZSqcQIe0TIlmsDH4BV8Bd2NGkrUSNFK8q25n4GjEF49aOSHowBNx6XI3kU0Pkv0NBjwPAnGfu9xRdljHVwfs74H/4T18JwATlTAVQUwcXX8IQKY3ARwOQGE/4sAonMCwOcEUGminALgyldRROy/rYgwuJYiPt0UcTlFROdb35Dn6AMVEd9Y/1uso+jfoX16gvaIa9vXBvxHP7bSGUZV2/Eg1X44LeuDEUaZ+T48gmlJIfHEJtVfsYJpIAz5X57gtW4qTQvnDe7ZOey2n+vAvbLrN+MoNjap2AucQ9yKxEyYoOqpaWtXK0ov06TDIYnhcYsO8KkePfmNHm2qcf931Np6P6H4/hc=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>


Provider Name      | Provider ODS Code | IT System
-------------------|-------------------|--------------
GP Federations Ltd.| AB1234            | ANGPS





Service Type | DoS ID | Service Name             | Service ODS Code 
-------------|--------|--------------------------|------------------
GP Federation|123456  | GP Hub - Main location   | AB1234            
GP Federation|123457  | GP Hub - the High Street | 123457            









