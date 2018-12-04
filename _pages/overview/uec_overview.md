---
title: Urgent Emergency Care Landscape
sidebar: overview_sidebar
permalink: uec_overview.html
---
{% include note-notpublished.html %}

The following info-graphic displays the patient flow through NHS 111 into the wider UEC system. The data shows NHS 111 call volumetrics of those patients triaged by NHS 111 and given recommendation to attend/speak to onward UEC care setting. The data are taken from the NHS111 MDS (Minimum Data Set) https://www.england.nhs.uk/statistics/statistical-work-areas/nhs-111-minimum-data-set/ published by NHS England (available here) and data supplied internally by the NHS Pathways >Intelligent Data Tool (IDT) team at NHS Digital (information can be found here).https://digital.nhs.uk/services/directory-of-services-dos

<image src="images/overview/iuc_overview.png"/>  

The 111/CAS service currently sends referrals to GP In Hours, GP Out of Hours (GP OOH), Urgent Treatment Centres (UTCs),and other services, using <a href="https://developer.nhs.uk/apis/uec-tech-standards/endpoint_location.html" target="_blank">CDA ITK messages</a>. Development and implementation has been done using proprietary solutions to enable booking between NHS 111 and both GP In Hours and UTCs. However, these solutions are point to point and take a lot of resource to implement and scale.

The <a href="https://www.england.nhs.uk/wp-content/uploads/2014/06/Integrated-Urgent-Care-Service-Specification.pdf" target="_blank">Integrated Urgent Care service specification </a> references booking a number of times including:

* 4.1 - NHS Outcomes Framework Domains & Indicators (pg.22)
  * A single call to get an appointment during the out-of-hours period.
* 5.0 Scope - Key service requirements (pg.24):
  * Implementation of a solution capable of direct appointment booking with destination services through the chosen clinical workflow system. 
* 5.5.1 Appointment Booking (pg. 41):
  * Booking shall be available for both in-hours services (such as, GP Surgeries) and urgent care services (such as, Urgent Treatment Centres, Out of hours GP and extended access same day services and in time dental services where commissioned). 
