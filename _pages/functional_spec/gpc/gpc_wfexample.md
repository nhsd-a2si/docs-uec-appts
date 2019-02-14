---
title: GP Connect - Workflow Example
sidebar: gpc_sidebar
keywords: specification
permalink: gpc_wfexample.html
toc: false
folder: functional_spec
---


{% include note-notpublished.html %}

# Example scenario

Services on the DoS are profiled with a range of data that is used to determine the ranking for services. There are also additional data items that are used for other purposes, for example interoperability. Examples of these data items are as follows:

* Geographical information such as address and search etc..
* Demographic profile of patients the service is available for
* The comissioning footprint of the service, for example 
  * GP Practices that patients have to be registered to in order to use the service
* The clinical needs that the service will meet, for example:
  * symptoms
  * timeframes
* Referal endpoint information, for example:
  * URLs
  * Document format

The key aspect for direct booking is how a specific service will relate to a GP Connect Schedule resource on a particular system.

Please note that in the example below, many irrelevent details are simplified or skipped. Also the technical details of the API messaging interactions are omitted. This is explained in detail <a href="https://nhsconnect.github.io/gpconnect/" target="_blank">here</a>.

For this example, consider a GP Federataion provider called "GP Federations Ltd.". This provider has been comissioned by the GP Practices in a comissioning area to deliver the extended access GP services on behalf of these GP Practices. GP Federations Ltd. operates this service from three different locations, these are consulting rooms in three of the GP Practices they are covering.

GP Federation Ltd. deliver their services from a single IT Platform, known as "Another GP System (ANGPS)". 


Provider Name      | Provider ODS Code | IT System
-------------------|-------------------|--------------
GP Federations Ltd.| AB1234            | ANGPS
 
 
Each of the three locations has its own appointment diary represented as a schedule in ANGPS. Location 1 has two diaries, a GP diary like the other two and a Nurse diary also:


<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; version=\&quot;9.2.7\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;a9224995-d5d3-854d-5d66-375058506576\&quot; name=\&quot;Page-1\&quot;&gt;7VfBbqMwFPwajonABpYck7TprpSVKqXSnl1wwFqDWeM00K/fZzAEkhRFalrlEA5gz7P9zMwbCyy8TMsnSfLkt4got5AdlRZ+sBByZsiDh0aqFrENEksWGewAbNg7NaBt0B2LaDEYqITgiuVDMBRZRkM1wIiUYj8cthV8mDUnMT0BNiHhp+gfFqmkQTG27UPgJ2VxYlJDaNZEXkn4N5Zil5mEFsLb+mrCKWkXMysVCYnEvgfhRwsvpRCqaaXlknLNbstbM2/1QbTbuKSZumRC0Ex4I3xH2x37HKYutgJWgA2qyrDi/9uJNjApas3mMMAN8vIQhFasn0/PEFrRiEqimMgK6K1ZyhSNoPXrBW6bqlA0bbPBDpuEzXRDTpcbFXuWcpJBb5GolAPoQLNQRCpTPv5Mx4Rk77AOaUeEusMyKl+qXI9SktJu/TcqFS0/ZM7p9IBKpyKlSlYwxExwjYLVsLs/1IuD23pOerXiYQMSU6Rxt/RBJ2gYqc7Lhk9kW4uwZhpQPMaeZtkw5gSXMhGMMjHzhlQ4vj21e1dbZD1q0OwMM+gazKAzBX3MRkLqWmBpfQz0C0rzwOAcmHMWZ7pcRN5D1+SV8mdRsJpo/PAqlBIpDOA6sOisvxRcyDpXa368qJPNi7w5rmxASNvZshJsYYZAP1FKn3Nz/c5oFUYZmjKo4y3LwE7TEDKiVUQUgYfGwVurjO4nFSVyImkh+M5YbuW7cOtBE9udOCiY5ll8ke54VPfAGcjuOUPV8akh2kroq96Bn1HdH/ODM+aH/hECW/4Sg+ATf5xQ4547Kq5iiB93Q1zPEP6ozkfnoH9kiMD9RkfM7rJ/l+zIvyHd3bGT8EwNfOmXgee5t/Nl4N0dcT1HuDf6ZaDfqvt5qmO9f1T8+B8=&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>


The important thing here is how the DoS services link through the the appointment schedule. The below table describes the location configuration on the IT system. Note that each schedule is on this system will be represented on SDS by the same end point. This endpoint will have an ASID (HealthcareServiceID), this ID is what is known as an accredited system identifier (ASID) and is created when an endpoint is configured on the Spine Directory Service (SDS):


ID  |  Location Name  | ODS Code | Schedule | Appointment Type | HealthcareServiceID
----|-----------------|----------|----------|------------------|---------------------
1   | Main Location   | AB1234   | 1        | GP               | 109876543210
1   | Main Location   | AB1234   | 2        | Nurse            | 109876543210
2   | The High Street | AB1234   | 3        | GP               | 109876543210
3   | Other Town GP   | AB1234   | 4        | GP               | 109876543210


This service will most likely be represented on the DoS as a single service, the table below shows key information about the associated DoS service and the HealthcareServiceID defined against this service, Note that each service has its own unique HealthcareServiceID:


Service Type | DoS ID  | Service Name                 | Service ODS Code | HealthcareServiceID
-------------|---------|------------------------------|------------------|---------------------------
GP Federation| 123456  | GP Hub - GP Federations Ltd. |      AB1234      | 109876543210
 
 
From this information we can see that this DoS service will have 1 to many appointment schedules. At this stage ODS code is not relevent to the booking process which means that the location and slot ambiguity caused by the brittle relationship between ODS code, the service, its locations and schedules is removed.

The following digram illustrates with a typical return from the DoS, the relationship of DoS services to appointment schedules.

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile userAgent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; version=\&quot;9.2.7\&quot; editor=\&quot;www.draw.io\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;88323ed8-82d2-1482-348e-76e8bdfa6592\&quot; name=\&quot;Page-1\&quot;&gt;7Vtbj9o4FP41PIJiOwnkkWu70nR3tDPSdp9WJhiIGuKsYwr016+d2Lk5oek2BUYaRjMkx7eT853v+MT2DND8cP7AcLz/RDckHEBrcx6gxQBC4LmO+JKSi5bYSrJjwUbJCsFL8I0ooaWkx2BDkkpFTmnIg7gq9GkUEZ9XZJgxeqpW29KwOmqMd8QQvPg4NKV/BRu+z6QIWVZR8JEEu70aWhR5Wcka+192jB4jNeAAom36yYoPWHemekr2eENPJRFaDtCcUcqzq8N5TkJpXW23rN2qpTRXnJGId2mA7KzFVxweiVY5VYxftDXk88Rmx2qsr4Rxcm6CBa91D8WTCZ8h9EA4u4h6qpWLJlk75S4IgJHyl1NhfdtRJtuXDO8ApS5WiO/y3ouHFhfquVtsAL5vg4Qz+iV3BjBAsxw5S9xscLInG3WDw2AXiWtfmIowIdjzQ1i0imWXh/NOcmd0oP6XYzwSFuM4iAhLRmvpvoT9FURp9zOm6CF73gZhOKchZalS2rNEr6l2pRI3/VRLYFZkWRO/3ghlRb4tf0TRQejySs6ZkedSCeIfWRJ8JX+SpFDH9IncnepOYYJ/G2ihAe2z5D60wB0hxpG/l0jNtkKm4AVjdd+Eoh4uJFvebPc2MraTzqpwThu7hAoADahAtwdQkAHKnnMZ2qeyD7gCACSXhJODuN7Q5B9GtoQxHD4CZBU63g8+gKr4aThL+MEmVvWBnzPuEC+VRbchOU/ljCyem0QbdbnwQ5wkgV9FoS26ZZ2TjTFnmwZM6JH5qlqHwNMYd5SMkRBzEfGqyUWD2dQIzzQQ2uQADe3qpAbGEz2p6U4yZVW78hxd62oCKz15ntETx2xHuNGTsDa+lKrFskJyRedxTWcXqZHaVKu3KHQrfCnTovCsHIpOzqYTpZKzfXgW9x+Pa/F3KH4/CYqKr5D6Ai8aKams1OKTLE0ZZ2mWloYH6XynfcDJS4xT7zmJKGBEiCKuVKfbiEbE9F7Xns2WUJKf+SpGoHrMkFNtIoYMot1TGhoWNtRVlNrADCur9NMprHSfjXUpcKoeYAMzrsAG1tjWz8cVaOZhDbO0AlE0FW8D0vAxYYEYS8Z0LX0uRGWDwybrXkG2HIRq8AJrjLxl3kJPQbYJV96DMQH1Adikhhcy8XIb4HL7gMvMrTox83eRSYoMzA2l066ZuNoV7nsvuq4mczR583SFlntDupppXHsecGe6rqCHwAPS1TPx+mV0Nd/0a3T9KAYUXy+cEcLvTEdrspyAN0/H8S1nT8fAFz0qHadLGyD4cHSE7g1nT/d7dPyD78WDQuuVnqL7stFZjFee99bZiNAtJ0fzHdl+VDYK29rO4uHYiOANJ8eJAddycV/SuWDuzpdvnXS2dcsp0DNQdB6VdABOpzPn8Ujn3W4KdM0XiFa0+lhHJOeAf1Z15PXfErORk/YoVP+sIExvirJMpaurj02Ljyp2ZStzyhfvuiDp1Ff8XVDDsOt6ZN5Q9+TUvaGn9UjgwupI7ti6qpnRAGj/7ms5Uj/pA6196w3ysqe59/Q0b4yqqD2+o+XTT03lVkerN+jd0WxzLjMd7RQcQpwmD+VMQxhFT1iuzNr3lAXf5FaWrpHva71eUkeVL/y5rzXs5xve1r6raMOqWSwNYXljETXtLDqohynFMen5VKw+NrwPFxYs51WTrtbIUGo1h+fUY641skofnXaWkyOvadeuF9t0OeagQldwSE/IlN1KWiLwcThVWQincUn6hNckfKZJkJoaLdaUc3oQFUJZMMtPxTTFuHSwaRJnJ3nSvVp9sw3OMsGeKX0W1X1ifxPBUSC8eRuIRJyNfJruGGOOxZeUC8qvInIaXghmQ0YSGh6lflLsikxpVRINLXsoSDyKo10n5J3rZ1omoAK8A6q4I5MU2hfKuOfCn8IdXuNEww5LwYlyKBE6/xqSIIMjhnHsxqMIvZDiB3LQd1J8lxTwKtJOfZKtBUP7lqzocPDtHfiegK+fNrov8uZCeSkeXs2yfkX4c7QnPkSOYK5Kv7Pi/7PCeSs5gmvmCHqHPolxVOzRZzLJg4pTuP8eqS4YZidEhf0tG8bnorDey1oL0o2PFRHwYGV66yk4BFzACq3fXsWfF3UcMGsonmZd70zIMq0McfUBas7M01OuZR9m8oSrOros/Uy9O4razmyQLpPjI6fqFCwwV1GbOaBWaV/lzWJoX3njb1wb7ifPqp7VMo9Yj62GuNJLWDGX11vDSp8rfZax0jfovJ5SWc1TXKyssdjN1n5fzes4kKOO/XdWTJ95bWvg6dMULQ1+dE1GBv/8HzGy6sX/u6Dlfw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

Once all the above is understood we can walk through a typical booking scenario using this example service.

### Booking scenario walk-through

1. A patient dials 111 on their phone and gets through to their local 111 service. 
2. The health advisor takes them through an NHS Pathways assessment and they get referred to the Clinical Assessment Service (CAS) to speak to a clinician.
3. The clinician assesses the patient and determines that the patient requires an urgent appointment with a GP.
4. The 111 IT system searches the DoS with the details of the patient and the assessment
5. The DoS returns a ranked list of services. The top service is the service named "GP Hub - Main location GP"
6. This service is selected and information on the referral and booking endpoints is returned including the HealthcareServiceID
7. Next the 111 system will use the HealthcareServiceID to retreive the correct booking API endpoint from the endpoint registry.
In this scenario, since the target system is the same, the returned URL's from all services that it has profiled will all be the same. 
8. A request will be made by the 111 system to the appointment provider IT system to retreive all available and appropriate slots that have been shared with this type of consuming service (111).
9. The consuming system will then filter the returned slots for the "Main location GP Clinic" and identify them to the user/
