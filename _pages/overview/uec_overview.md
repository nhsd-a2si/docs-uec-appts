---
title: Urgent Emergency Care Landscape
sidebar: overview_sidebar
tags: [getting_started]
permalink: uec_overview.html
---

The following info-graphic displays the patient flow through NHS 111 into the wider UEC system. The data shows NHS 111 call volumetrics of those patients triaged by NHS 111 and given a recommendation to attend/speak to onward UEC care setting. The data are taken from the NHS111 MDS (Minimum Data Set) published by NHS England ( <a href="https://www.england.nhs.uk/statistics/statistical-work-areas/nhs-111-minimum-data-set/" target="_blank"> available here</a>) and data supplied internally by the NHS Pathways >Intelligent Data Tool (IDT) team at NHS Digital (<a href="https://digital.nhs.uk/services/directory-of-services-dos" target="_blank">information can be found here</a>).

<image src="images/overview/iuc_overview2.png"/>  

The biggest development in 111 since its beginning is to move to an "Integrated Urgent Care" service model (IUC). This combines the original 111 service with a "Clinical Assessment Service" known as the "CAS". This is a telephone service staffed by a multidisciplinary team of senior clinicians.

The 111/CAS service currently sends referrals to GP In Hours, GP Out of Hours (GP OOH), Urgent Treatment Centres (UTCs), and other services, using <a href="https://developer.nhs.uk/apis/uec-tech-standards/referrals.html" target="_blank">CDA ITK messages</a>. Development and implementation has been done using proprietary solutions to enable booking between NHS 111 and both GP In Hours and UTCs. However, these solutions are point to point and take a lot of resource to implement and scale.

The <a href="https://www.england.nhs.uk/wp-content/uploads/2014/06/Integrated-Urgent-Care-Service-Specification.pdf" target="_blank">Integrated Urgent Care service specification </a> references booking a number of times including:

* 4.1 - NHS Outcomes Framework Domains & Indicators (pg.22)
  * A single call to get an appointment during the out-of-hours period.
* 5.0 Scope - Key service requirements (pg.24):
  * Implementation of a solution capable of direct appointment booking with destination services through the chosen clinical workflow system. 
* 5.5.1 Appointment Booking (pg. 41):
  * Booking shall be available for both in-hours services (such as, GP Surgeries) and urgent care services (such as, Urgent Treatment Centres, Out of hours GP and extended access same day services and in time dental services where commissioned). 
