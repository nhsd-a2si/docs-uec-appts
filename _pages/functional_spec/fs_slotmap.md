---
title: Booking Mapping
sidebar: overview_sidebar
keywords: specification
permalink: fs_slotmap.html
toc: false
folder: functional_spec
---

When booking using the GP Connect standard there is not the same level of granularity for linking services to booking diaries as you would find in bookings based on the NHS Booking Standard. Some services may be returned that are profiled for broader clinical needs for which there is no intention to support a booking. It is therefore a requirement to perform a local mapping within the consumer system against the triage outcome and booking.

When the clinical assessment is specifically being performed using the NHS Pathways assessment tool a standard set of Pathways dispositions has been developed to support this mapping. When booking into Primary Care services it is expected that all Pathways assessments that reach one of the following list of dispositions should result in a referral to a service with an appointment being offered:

> * Dx05 To contact a Primary Care Service within 2 Hours
> * Dx06 To contact a Primary Care Service within 6 Hours
> * Dx07 To contact a Primary Care Service within 12 Hours
> * Dx08 To contact a Primary Care Service within 24 Hours
> * Dx10 MUST contact own GP Practice for a Non-Urgent appointment
> * Dx11 Speak to a Primary Care Service within 1 Hour
> * Dx12 Speak to a Primary Care Service within 2 Hours
> * Dx13 Speak to a Primary Care Service within 6 Hours
> * Dx14 Speak to a Primary Care Service within 12 Hours
> * Dx15 Speak to a Primary Care Service within 24 Hours
> * Dx75 MUST contact own GP Practice within 3 working days
> * Dx81 Contact own GP Practice next working day for a repeat prescription
> *	Dx1112 COVID risk Clinical Assessment Service 1 hour
> *	Dx1113 COVID risk Clinical Assessment Service 2 hours
> *	Dx1114 COVID risk Clinical Assessment Service 4 hours
> *	Dx1115 COVID risk Clinical Assessment Service 6 hours
> *	Dx1116 COVID risk Clinical Assessment Service 12 hours
> *	Dx1117 COVID risk Clinical Assessment Service next working day
> * Dx110	Community Nurse within 4 hours 
> * Dx111	Community Nurse within 24 hours 
> * Dx112	Community Nurse next working day 
> * Dx113	Health Visitor next working day 
> * Dx114	Community Midwife next working Day 
> * Dx115 Contact own GP Practice next working day for an appointment
> * Dx117 Speak to a Primary Care Service within 1 hour for Palliative Care

However, locally some areas may differ from the above list, therefore your system should be flexible enough to meet local need in terms of which dispositions can support booking.
