---
title: Appointment/slot mapping
sidebar: overview_sidebar
keywords: specification
permalink: fs_slotmap.html
toc: false
folder: functional_spec
---

## Introduction

As already described the primary service discovery tool is envisaged to be the Urgent Care Directory of Services. One aspect of searching the DoS that has not been described is how outcomes from the prior clinical assessment map to DoS services and subsequent appointment booking workflows. 

## With Care Connect booking

It is the intention that with UEC booking using the Care Connect standard the clinical profiling of the DoS service will solely determine the requirement for booking. This is because of the effective 1:1 mapping between DoS service and apppointment diary. This means that for UEC appointment booking using the Care Connect standard, if a service is returned and has a booking endpoint, then a booking should be attempted with no further check on the outcome of the prior clinical assessment.

## With GP Connect Booking

However, since this level of granularity for linking DoS services to appointment diaries is not available when booking UEC appointments using the GP Connect standard some services may be returned that are profiled for broader clinical needs for which there is no intention to support a booking. It is therefore a requirement to perform a local mapping within the consumer system against the triage outcome and appointment booking.

When the clinicl assement is performed using the NHS Pathways assessment tool a standard set of Pathways dispositions has been developed to support this mapping. When booking into Primary Care services it is expected that all Pathways assesments that reach one of the following list of dispositons should result in a referral to a service with an appointment being offered:

> * Dx05 To contact a Primary Care Service within 2
> * Dx06 To contact a Primary Care Service within 6
> * Dx07 To contact a Primary Care Service within 12
> * Dx08 To contact a Primary Care Service within 24
> * Dx09 For persistent or recurrent symptoms: get in touch with the GP Practice for a Non-Urgent Appointment (Green 4)
> * Dx10 MUST contact own GP Practice for a Non-Urgent appointment
> * Dx11 Speak to a Primary Care Service within 1 Hour
> * Dx12 Speak to a Primary Care Service within 2 Hours
> * Dx13 Speak to a Primary Care Service within 6 Hours
> * Dx14 Speak to a Primary Care Service within 12 Hours
> * Dx15 Speak to a Primary Care Service within 24 Hours
> * Dx75 MUST contact own GP Practice within 3 working days
> * Dx81 Contact own GP Practice next working day for a repeat prescription
> * Dx115 Contact own GP Practice next working day for an appointment
> * Dx117 Speak to a Primary Care Service within 1 hour for Palliative Care

## Support for "booking only" type services

Some services that are profiled on the Urgent Care Directory of Services are comissioned as "booking only" services. That is to say that they only accept referrals with an appointment. If no appointment is available then a referral should not be made.
Currently the DoS referral workflows do not support witholding refferal options if no booking is made. 

This will be supported in an upcoming release of the DoS. A new "service attribute" will be configurable against services. This will allow the service to be flagged as "booking only". Therefore is this attribute is present on the service all consumer systems should withold referrals.
