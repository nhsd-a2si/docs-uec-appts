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

GP Federation Ltd. deliver their services from a single IT Platform, known as "Another GP Clinical System (AGPCS)" (see figure 1). 

Provider Name      | Provider ODS Code | IT System
-------------------|-------------------|--------------
GP Federations Ltd.| AB1234            | ANGPS

###### _figure 1_
<p>
 
Each of the three locations has its own appointment diary represented as a schedule in AGPCS. Location 3 has two diaries, a GP diary like the other two and a Nurse diary also (see figure 2):

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; version=\&quot;9.2.7\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;a9224995-d5d3-854d-5d66-375058506576\&quot; name=\&quot;Page-1\&quot;&gt;7VfBbqMwFPwajonABpYck7TprpSVKqXSnl1wwFqDWeM00K/fZzAEkhRFalrlEA5gz7P9zMwbCyy8TMsnSfLkt4got5AdlRZ+sBByZsiDh0aqFrENEksWGewAbNg7NaBt0B2LaDEYqITgiuVDMBRZRkM1wIiUYj8cthV8mDUnMT0BNiHhp+gfFqmkQTG27UPgJ2VxYlJDaNZEXkn4N5Zil5mEFsLb+mrCKWkXMysVCYnEvgfhRwsvpRCqaaXlknLNbstbM2/1QbTbuKSZumRC0Ex4I3xH2x37HKYutgJWgA2qyrDi/9uJNjApas3mMMAN8vIQhFasn0/PEFrRiEqimMgK6K1ZyhSNoPXrBW6bqlA0bbPBDpuEzXRDTpcbFXuWcpJBb5GolAPoQLNQRCpTPv5Mx4Rk77AOaUeEusMyKl+qXI9SktJu/TcqFS0/ZM7p9IBKpyKlSlYwxExwjYLVsLs/1IuD23pOerXiYQMSU6Rxt/RBJ2gYqc7Lhk9kW4uwZhpQPMaeZtkw5gSXMhGMMjHzhlQ4vj21e1dbZD1q0OwMM+gazKAzBX3MRkLqWmBpfQz0C0rzwOAcmHMWZ7pcRN5D1+SV8mdRsJpo/PAqlBIpDOA6sOisvxRcyDpXa368qJPNi7w5rmxASNvZshJsYYZAP1FKn3Nz/c5oFUYZmjKo4y3LwE7TEDKiVUQUgYfGwVurjO4nFSVyImkh+M5YbuW7cOtBE9udOCiY5ll8ke54VPfAGcjuOUPV8akh2kroq96Bn1HdH/ODM+aH/hECW/4Sg+ATf5xQ4547Kq5iiB93Q1zPEP6ozkfnoH9kiMD9RkfM7rJ/l+zIvyHd3bGT8EwNfOmXgee5t/Nl4N0dcT1HuDf6ZaDfqvt5qmO9f1T8+B8=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>
###### _figure 2 - the configuration of the three locations in the IT system_

<p>
The important thing here is how the DoS services link through the the appointment schedule. The below table describes the location configuration on the IT system:

ID |  Location Name  | ODS Code | Schedule | Appointment Type | HealthcareServiceID
---|-----------------|----------|----------|------------------|---------------------
1  | Main Location   | AB1234   | 1        | GP               | 109876543210
1  | Main Location   | AB1234   | 2        | Nurse            | 101234567890
2  | The High Street | AB1234   | 3        | GP               | 987654321001
3  | Other Town GP   | AB1234   | 4        | GP               | 123456789001



The table below (figure 4) shows key information about the associated DoS services and the HealthcareServicesID defined against each service:

Service Type | DoS ID  | Service Name                 | Service ODS Code | HealthcareServiceID
-------------|---------|------------------------------|------------------|---------------------------
GP Federation| 123456  | GP Hub - Main location GP    |      AB1234      | 109876543210
GP Federation| 654321  | GP Hub - Main location Nurse |      654321      | 101234567890
GP Federation| 123457  | GP Hub - the High Street     |      123457      | 987654321001
GP Federation| 123458  | GP Hub - Other Town GP       |      123458      | 123456789001

###### _figure 4_

<p>
From this information we can see that each DoS service has a 1:1 relationship with appointment schedules through the HealthcareServiceID. This identifier needs to be specificied on the appointment provider system and against the corresponding service on the DoS. As can be seen this means that each location (and even each appointment type) has its own DoS service. Since ODS code is not relevent to the booking process here it means that the locational and slot ambiguity caused by the brittle relationship between ODS code, the service, its locations and schedules is removed.

The following digram shows the relationship and cardinality of DoS services to appointment schedules.

