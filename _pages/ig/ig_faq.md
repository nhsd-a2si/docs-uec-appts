---
title: Information Governance - Frequently Asked Questions
sidebar: overview_sidebar
keywords: guidance
permalink: ig_faq.html
toc: false
folder: ig
---

## Information Governance Overview

The NHS Booking Standard has had extensive review to understand the implications and context for information governance. 
<br>
This review was for the standard itself and not specific implementations that remain under the jurisdiction of the suppliers developing those solutions. The outcome of this review means that NHS Digital has not been required to prepare a DPIA for implementations of the NHS Booking Standard because no personal or special category information assets of NHS Digital were invoked or shared as a result of its operation. Local care Trusts use a UEC Booking API to share data, for which they are the controllers, through a set of infrastructure services operated by NHS Digital. The NHS Digital DPIA for those infrastructure services have been updated in a minor way and would not help in the preparation of local DPIAs. There has also been extensive clinical governance put in place including the development of a clinical safety case. This can be viewed on request.
<br>
The following diagram illustrates how data is shared using the NHS Booking Standrad within UEC:

<image src="/ig/DPIA-diagram.jpeg"/>

## Do I need a Data Sharing Agreement (DSA) between two organisations to allow booking?  

* There are two aspects to this. Firstly does a pre-existing agreement between two specific organisations already cover this flow? Secondly what access controls are in place to restrict access to appointments between organisations.
* GP Connect requires a DSA to be in place between two organisations before any GP Connect operations can take place. This is mainly because the capabilities of GP Connect include sharing information from a patients medical record at their GP Practice.
* The presence of a DSA is enforced by the Spine Secure Proxy (SSP) when any GP Connect operation is attempted. This therefore performs the role of access control too.
* For bookings using the NHS Booking Standard, the only operations relate to booking administrative data. The information being transmitted and accessed for booking is minimal. Most of the important information is (e.g. patient demographics) is obtained from the PDS (Spine) and obtained/requested prior to the booking operations, or sent as part of a referral workflow.
* Therefore a specific pre-established DSA is not required allowing for on-the-fly establishment of booking relationships. The access control is applied during the service discovery. If a service advertises its appointments on the service directory tool being used for service discovery (such as the Urgent Care DoS) then the service looking up on the tool will be able to book.
* The authentication that happens for NHS Booking on the SSP establishes trust that the service performing the booking operations is a valid service and system accredited and allowed to do so.
