---
title: Information Governance - Frequently Asked Questions
sidebar: overview_sidebar
keywords: guidance
permalink: ig_faq.html
toc: false
folder: ig
---

{% include note-notpublished.html %}

Do I need a Data Sharing Agreement (DSA) between two organisations to allow booking?

* For GP Connect - Yes
* For Care Connect - No


There are two aspects to this. Firstly does a pre-existing agreement between two specific organisations need to be put in place? Secondly what access controls are in place to restrict access to appointments between organisations.

GP Connect requires a DSA to be in place between two organisations before any GP Connect operations can take place. This is mainly because the capabilities of GP Connect include sharing information from a patients medical record at their GP Practice.

The presence of a DSA is enforced by the Spine Secure Proxy (SSP) when any GP Connect operation is attempted. This therefore performs the role of access control too.

For UEC bookings using Care Connect the only operations relate to appointments. The information being transmitted and accessed for appointment booking is minimal. Most of the important information is (e.g. patient demographics) is obtained from the PDS (Spine) and obtained/requested prior to the booking operations.

Therefore a specific pre-established DSA is not required allowing for on-the-fly establishment of booking relationships. The access control is applied during the service discovery. If a service advertises its appointments on the service directory being used for service discovery (such as the Urgent Care DoS) then the service looking up on the directory will be able to book.

The authentication that happens for Care Connect on the SSP establishes trust that the service performing the booking operations is a valid service and system accredited and allowed to do so.
