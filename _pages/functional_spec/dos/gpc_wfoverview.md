---
title: GP Connect - Workflow Overview
sidebar: dos_sidebar
keywords: specification
permalink: gpc_wfoverview.html
toc: false
folder: functional_spec
---



GP Connect appointment booking could be utilised for a number of different booking workflows where the end point is a GP IT System. The most frequently anticipated flow is when services are booking directly into a patients own registered GP Practice. An example might be from an urgent care service such as UTC or a 111/IUC service.

The "default" workflow pattern for booking into a GP Practice where the patient is registered to that practice is clearly defined by the GP Connect documentation <a href="https://nhsconnect.github.io/gpconnect/" target="_blank">here</a>. This requires that the consuming system obtains the ODS code for the GP Practice and uses this to query SDS for the endpoint. It is anticipated the ODS cde the the patients registered GP practice is obtained from the spine Patient Demographic Service (PDS) UNLESS the UEC DoS is being used as the service discovery tool. If the DoS is used to determine the service to be booked into then the information to query SDS for the booking endpoint should be obtained from the DoS endpoint store for that service rather than PDS.

There are however some more complex flows where the relationship between the patient and the GP Practice needing to be booked into is not very clear. An example is where an Urgent Care service such as 111 or a UTC want to book into an extended access Federation of GP Practices. Currently solutions to these more complex flows are still being developed but for Consuming systems being used by Urgent Care services an example of how this could work is presented <a href="gpc_wfexample.html">here</a>
